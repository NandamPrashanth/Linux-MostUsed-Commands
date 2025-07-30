
# Session 3 - File And Directory Management

In this session we will learn what is File and what is Directory and we will see how to create a **File**, **copy a file**, **rename a file**, **delete a file**, **move a file**, **read a file**, **append a file**, **Locate a file**, **find a file**, **search in a file** and we will see how to **compress** a file in Linux.

Once it is done we will walk through the **Directory Management** and we will learn how to **create a directory**, **view directory**, **rename directory**, **delete directory**, **move direcoty**, **copy directory** and then we will see how to list the contents inside a **directory**.

----------------------------------------------------------------------------------------------------------------------------------------------------------------------

# Files Management Most Used Commands

1. To create a file we will use the command below
    **touch session3.txt**
   Now the above command will create a file with name session3.txt
   
2. To create a file and add data or any content to it  
    We have 3 ways to do it  
   1. use echo command and redirect it to a file, it will add data to the file  
      **echo "Hello, World!" > session3.txt**  
    This will create session3.txt with the text Hello, World!. The > operator is used to overwrite the file if it already exists.  

    Now  
       echo "This is an additional line" >> **session3.tx**  
   
      This will append data to an existing file, use the >> operator.  
      This appends the text "This is an additional line" to **session3.tx**  
   
    2. We can use command nano  
         sudo nano **session3.txt** now it will open the session3.txt file and then we can add content to it. Once we done adding our content to the file, we can use CTL+O then press ENTER and then CTL+X  
       This will save the content to the file and closes the file.  

    3. last we have vim or vi  
          vi session3.txt  
       If session3.txt is availble then it will open the file, if the file is not availble then it will create the file with that name.  

       Once the file is opened PRESS i for insert  

       Now add the content to the file  

       Now  

       when you are done with adding content or making changes, press ESC  

       To save and quit:  
       use :wq  

       If you only want to save (not quit):  
       Use :w  

       If you want to quit without saving:  
       Use :q!  

3. To copy a file  
      cp source.txt destination.txt  

4. To rename  
      In Linux, renaming is done using the mv (move) command.  
       mv oldname.txt newname.txt  

5. To delete  
      rm filename.txt  

6. To move  
      mv filename.txt /path/to/destination/  

7. To Read / View a File  
   
   ```bash
      | Tool   | Use                    |
| ------ | ---------------------- |
| `cat`  | Display the whole file |
| `less` | Scrollable file view   |
| `head` | View first lines       |
| `tail` | View last lines        |

```  

9. To Locate a File  
    locate filename  

10. To search  
    find /path/to/search -name "filename"  

11. To search inside a file  
    grep "search_term" filename.txt  

12. To compress a file  
    gzip filename.txt  


-----------------------------------------------------------------------------------------------------------------------------------------------------------------------

# DIRECTORY MANAGEMENT  

1. To create a directory  
    mkdir directory_name  

2. To create nested directories  
    mkdir -p parent/child/grandchild  

3. To view current directory/ where you are  
  pwd

4. To rename a directory  
    mv oldname newname  

5. To delete an empty directory  
    rmdir directory_name  

6. To delete non empty directory  
    rm -r directory_name  

7. To forece delete without confirmation  
    rm -rf directory_name  

8. To move a directory  
    mv directory_name /destination/path/  

9. To copy a directory  
    cp -r source_directory destination_directory  

10. To list content inside a directory  
    ls directory_name  

11. To detailed listing  
    ls -l directory_name  

12. To list all inclusing hidden files  
    ls -la directory_name



