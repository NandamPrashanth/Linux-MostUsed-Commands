# SESSION 5 - Process and Package Management

In this session we will learn **Monitor and controll processes** and we will understand **systemd, services, journald logs** and later we will see **Install, Update and manage packages with DNF** **Handle software repositories and .rpm packages**

# Process Management  

Process management involves monitoring, controlling, and automating applications that are running on the system.  

```bash
ps aux                # List all processes
top                   # Real-time process monitoring
htop                  # Interactive viewer (install via dnf)
pidof nginx           # Get PID of a running process

```

 # Kill or Controll Processes  
```bash
kill <PID>             # Gracefully stop a process
kill -9 <PID>          # Force kill
nice -n 10 <command>   # Run command with priority
renice -n -5 -p <PID>  # Change priority of running process  
```

# Service Management (systemd)  

```bash
systemctl status nginx.service     # Check status
systemctl start nginx.service      # Start service
systemctl stop nginx.service       # Stop service
systemctl restart nginx.service    # Restart service
systemctl enable nginx.service     # Enable on boot
systemctl disable nginx.service    # Disable on boot
journalctl -u nginx.service        # View logs
journalctl -xe                     # Last errors
```

# Package Management with DNF & RPM

## What is a Package?

A **package** is a compressed archive of:

- Software binaries
- Configuration files
- Metadata (version, dependencies, etc.)

## What is RPM?

- **RPM** = Red Hat Package Manager
- Low-level CLI tool
- Works with `.rpm` files (no dependency resolution)

### common RPM Commands

```bash
rpm -ivh nginx.rpm      # Install local RPM
rpm -qa                 # List all installed RPMs
rpm -qi nginx           # Package info
rpm -ql nginx           # List files from package
rpm -e nginx            # Erase/remove package
```

### Repositories
```bash
dnf repolist                     # List enabled repos
dnf config-manager --add-repo <url>  # Add external repo
```

## What is DNF?
DNF = Dandified YUM (default on Rocky Linux)

- High-level package manager  
- Uses RPM in the background  
- Automatically resolves dependencies  


### Common DNF Commands  

```bash
dnf update                       # Update all packages
dnf upgrade                      # Upgrade all packages
dnf install nginx                # Install a package
dnf remove nginx                 # Remove a package
dnf info nginx                   # Get package info
dnf list installed               # List installed packages
dnf history                      # View package history
dnf clean all                    # Clean package cache
dnf reinstall nginx             # Reinstall a package
```







