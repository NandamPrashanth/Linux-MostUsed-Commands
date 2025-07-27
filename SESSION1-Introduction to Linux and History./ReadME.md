

# Session 1 – Introduction to Linux and Linux History

In this session, we will learn what an **Operating System** is and explore common examples of operating systems.

We will then dive into a brief **History of Linux** and understand its evolution.  

An overview of **Popular Linux Distributions** will be provided.  

You will learn how to **Install a Linux machine on your Local Computer** using virtualization tools like VirtualBox.  

We will cover how to **Connect to the Linux machine using PuTTY** from a Windows system.  

Finally, the session will introduce you to **Creating EC2 instances on AWS Cloud** and connecting to them for hands-on practice.

-------------------------------------------------------------------------------------------------

### 🔹 What is an Operating System? 

An **Operating System (OS)** is the main **software** that runs on a computer device.  
It acts as a **bridge between the hardware** (e.g., CPU, memory, keyboard, etc.) and the **software** (applications and programs).

## 🔹 Examples of Operating Systems

1. **Windows**  
2. **macOS**  
3. **Linux**

-----------------------------------------------------------------------------------------------------------------------


## 🔹 Popular Linux Distributions

1. **Ubuntu**  
2. **RHEL** – Red Hat Enterprise Linux  
3. **CentOS / Rocky Linux**

There are many other distributions as well, such as **Debian**, **Fedora**, and **Kali Linux**, but the above are among the most widely used in the industry.

-------------------------------------------------------------------------------------------------------------------------


## 🔹 Introduction to Linux and Linux History

**Linux** is a free and Open-Source operaing system that began in 1991. When a Finnish Student named **Linus Torvalds** created it as a personal prject.

Before Linux, there was an operating system called **UNIX** developed in 1969. Which was known for being powerful and stable,especially in universities and large companies.

**UNIX** served as the inspiration for many later systems, but it wasn't freely available.

In 1987 a smaller educational version called **MINIX** was created to teach students how Opearting System works.

**Linus Torvalds** used ideas from both **UNIX and MINUX** to develop **LINUX**.

After releasing it freely under an open-source license, Linux grew quickly with the help of developers around the world. And Today Linux is one of the most used Opearting Systems.


-------------------------------------------------------------------------------------

## 🔹 Steps to Install a Linux Machine on Your Local Machine

1. **Install Oracle VirtualBox** on your local computer from the official site:  
   https://www.virtualbox.org/wiki/Downloads

2. **Download the Linux ISO file** you want to install.  
   In our case, we'll use **Rocky Linux**.  
   https://rockylinux.org/download

3. **Open VirtualBox** and click on **"New"** to create a new virtual machine.  
   Provide the following:
   - A name for the VM (e.g., `RockyLinux`)
   - Choose the type as `Linux` and version as `Red Hat (64-bit)`
   - Allocate memory (RAM), e.g., **2048 MB** or more depending on your system

4. In the VM setup, when prompted to choose a startup disk,  
   click **“Create a virtual hard disk now”** and follow the defaults or customize as needed.

5. Once the VM is created, go to **Settings > Storage**, click on the **Empty** CD icon under “Controller: IDE,”  
   then click the CD icon on the right side and choose **"Choose a disk file…"**.  
   Select the **Rocky Linux ISO** you downloaded earlier.

6. Click **OK**, then click **Start** to boot the VM from the ISO.  
   Follow the installation steps shown in the virtual machine window to install Linux (as discussed in the session).

   
## 🔹 WHAT IS ISO

  ISO is the installation image of the operating system its like a digital DVD that contains everything needed to install Linux Machine.

---------------------------------------------------------------------------------------  

## 🔹 Steps to Install PuTTY and Connect to Your Linux Machine

### Step 1: Download and Install PuTTY

1. Go to the official PuTTY download page:  
   https://www.putty.org/

2. Click on the appropriate installer for your system (usually the **64-bit Windows Installer** under MSI).
   
3. Download and run the installer.

4. Follow the on-screen instructions to complete the installation.


### Step 2: Get the IP Address of Your Linux Machine

1. Start your **Linux virtual machine** in VirtualBox.

2. After logging into the Linux terminal, run the following command to find the IP address:
   ```bash
   ip a or hostname -I


### Step 3: Connect Using PuTTY

Open PuTTY on your Windows system.

In the Host Name (or IP address) field, enter the IP address of your Linux VM.

Make sure the Port is set to 22 and Connection type is set to SSH.

Click Open.

You may see a security alert the first time—click Yes to continue.

When prompted, enter your Linux username (e.g., root or rocky) and password.

You are now connected to your Linux machine via PuTTY!

**Note**: Make sure your VM's network settings in VirtualBox are set to Bridged Adapter or NAT with Port Forwarding, so that it's accessible from PuTTY.


------------------------------------------------------------------------------------------------------------------------

## 🔹 Steps to Create a Rocky Linux Machine in AWS and Connect Using PuTTY


### Step 1: Launch a Rocky Linux EC2 Instance on AWS

1. **Log in to your AWS Console**:  
    https://console.aws.amazon.com/

2. Go to **EC2 Dashboard** → Click on **Launch Instance**.

3. Under **Name and tags**, give your instance a name (e.g., `rocky-linux-ec2`).

4. In the **Amazon Machine Image (AMI)** section:  
   - Click **Browse more AMIs**  
   - Search for `"Rocky Linux"`  
   - Choose the latest **Rocky Linux** AMI from the list (official or community)

5. Under **Instance type**, choose one (e.g., `t2.micro` if you're using the free tier).

6. Under **Key pair**, choose:
   - **Create a new key pair**
   - Choose **.pem** format (this is needed for SSH) or If you want to connect only from Putty then you can download **.ppk file**
   - Download and save the `.pem` file securely — **you'll need it to connect later!**

7. Leave other settings as default or adjust based on your use case.

8. Under **Security Group**, make sure:
   - An inbound rule allows **SSH** on port `22` from **your IP address**.

9. Click **Launch Instance**.


### Step 2: Convert `.pem` to `.ppk` for PuTTY

PuTTY does not accept `.pem` files directly. You need to convert it to `.ppk`.

1. Open **PuTTYgen** (installed with PuTTY).

2. Click **Load**, and select your `.pem` file (change file filter to *All Files* to see it).

3. Click **Save private key** (you can leave passphrase empty for testing).

4. This creates a `.ppk` file — save it securely.


### Step 3: Connect to Your EC2 Instance via PuTTY

1. Open the **EC2 Dashboard**, and copy the **Public IPv4 address** of your instance.

2. Open **PuTTY**.

3. In the **Host Name** field, enter:ec2-user@<public-ip-address>

4. In the left sidebar, go to:
   
 **Connection > SSH > Auth**
 
 Click **Browse**, and select your `.ppk` file

5. (Optional) Under **Session**, you can save this session name for reuse.

6. Click **Open**.

7. If prompted with a security alert, click **Yes**.

You are now connected to your **Rocky Linux instance in AWS using PuTTY**



### Notes:
- Make sure your instance is **running** and in a **public subnet** with a public IP.
- If SSH is not connecting, double-check **security group rules** and **VPC settings**.



