
### 1. Write a C program to create a new text file and write "Hello, World!" to it?
```c
#include<stdio.h>
#include<string.h>
#include<unistd.h>
#include<fcntl.h>
int main()
{
    int fd,ret;
    char buf[50];
    printf("enter data:");
    fgets(buf,50,stdin);
    fd=open("file.txt",O_WRONLY|O_CREAT,0664);
    if(fd<0)
    {
        printf("failed to open a file\n");
        return 0;
    }
    ret=write(fd,buf,strlen(buf));
    if(ret<0)
    {
        printf("failed to write into the file\n");
        close(fd);
        return 0;
    }
    printf("the data is successfully written to the file\n");
}
```

### 2. Develop a C program to open an existing text file and display its contents?
```c
#include<stdio.h>
#include<string.h>
#include<unistd.h>
#include<fcntl.h>
int main()
{
    int fd,ret;
    char buf[50];
    fd=open("file.txt",O_RDONLY);
    if(fd<0)
    {
        printf("failed to open a file\n");
        return 0;
    }
    ret=read(fd,buf,50);
    if(ret<0)
    {
        printf("failed to write into the file\n");
        close(fd);
        return 0;
    }
    buf[ret]='\0';
    printf("the data read from the file is %s\n",buf);
}
```

### 3. Implement a C program to create a new directory named "Test" in the current directory?
```c
#include<stdio.h>
#include<sys/types.h>
#include<sys/stat.h>
int main()
{
    int status;
    status=mkdir("Test",0664);
    if(status==0)
        printf("the test directory is created successfully\n");
    else
        printf("the test directory is not created\n");
}
```

### 4. Write a C program to check if a file named "sample.txt" exists in the current directory?
```c
#include<stdio.h>
#include<unistd.h>
#include<fcntl.h>
int main()
{
    int fd;
    fd=open("sample.txt", O_RDONLY);
    if(fd!=-1)
        printf("the file exists in the directory\n");
    else
        printf("the file doesn't exists in the directory\n");
}
```

### 5. Develop a C program to rename a file from "oldname.txt" to "newname.txt"?
```c
#include<stdio.h>
#include<unistd.h>
#include<fcntl.h>
int main()
{
    int status;
    status=rename("oldname.txt","newname.txt");
    if(status==0)
        printf("the file name renamed successfully\n");
    else
        printf("the file name is not renamed successfully\n");
}
```

### 6. Implement a C program to delete a file named "delete_me.txt"?
```c
#include<stdio.h>
#include<unistd.h>
#include<fcntl.h>
int main()
{
    int status;
    status=remove("delete_me.txt");
    if(status==0)
        printf("the file name removed successfully\n");
    else
        printf("the file name is not removed successfully\n");
}
```

### 7. Write a C program to copy the contents of one file to another?
```c
#include<stdio.h>
#include<unistd.h>
#include<fcntl.h>
#include<string.h>
int main()
{
    int ret,ret1,fd1;
    char buf[50];
    int fd=open("file.txt",O_RDONLY);
    if(fd<0)
    {
        printf("failed to open a file\n");
        return 0;
    }
    
    fd1=open("file1.txt",O_CREAT|O_WRONLY,0664);
    if(fd1<0)
    {
        printf("failed to open a file\n");
        return 0;
    }
    while((ret=read(fd,buf,50))>0)
    {
        buf[ret]='\0';
        ret1=write(fd1,buf,strlen(buf));
        if(ret1!=ret)
        {
            printf("failed to copy the contents\n");
            close(fd);
            close(fd1);
            return 0;
        }
        
    }
    printf("the contents of file is copied successfully\n");
    close(fd);
    close(fd1);
}
```

### 8. Develop a C program to move a file from one directory to another?
```c
#include<stdio.h>
#include<unistd.h>
#include<fcntl.h>
#include<string.h>
int main()
{
    int ret,ret1,fd1;
    char buf[50];
    int fd=open("dir1/file.txt",O_RDONLY);
    if(fd<0)
    {
        printf("failed to open a file\n");
        return 0;
    }
    
    fd1=open("dir2/file.txt",O_CREAT|O_WRONLY,0664);
    if(fd1<0)
    {
        printf("failed to open a file\n");
        return 0;
    }
    while((ret=read(fd,buf,50))>0)
    {
        buf[ret]='\0';
        ret1=write(fd1,buf,strlen(buf));
        if(ret1!=ret)
        {
            printf("failed to write\n");
            close(fd);
            close(fd1);
            return 0;
        }
        
    }
    if(ret<0)
        printf("failed to read\n");
    printf("the file is moved from one directory to another directory\n");
    close(fd);
    close(fd1);
}
```
                  
### 9. Implement a C program to list all files in the current directory?
```c
#include<stdio.h>
#include<string.h>
#include<dirent.h>
int main()
{
    DIR *d;
    struct dirent *entry;
    d=opendir(".");
    if(d==NULL)
    {
        printf("failed to open a directory\n");
        return 0;
    }
    printf("the files in the current directory:\n");
    while((entry=readdir(d))!=NULL)
    {
        if(strcmp(entry->d_name,".")!=0 && strcmp(entry->d_name,".."))
            printf("%s\n",entry->d_name);
    }
    closedir(d);
}
```c

### 10. Write a C program to get the size of a file named "file.txt"?
```c
#include<stdio.h>
#include<sys/stat.h>
int main()
{
    int fd;
    struct stat size;
    fd=stat("file.txt",&size);
    if(fd<0)
    {
        printf("failed get file details\n");
        return 0;
    }
    printf("the size of the file is %ld\n",size.st_size);
}
```
### 11. Develop a C program to check if a directory named "Test" exists in the current directory?
```c
#include<stdio.h>
#include<fcntl.h>
#include<unistd.h>
int main()
{
    int fd;
    fd=mkdir("Test");
    printf("%d",fd);
    if(fd==0)
        printf("the directory doesn't exists\n");
    else
        printf("the directory already exists\n");
}
```

### 12. Implement a C program to create a new directory named "Backup" in the parent directory?
```c
#include<stdio.h>
#include<fcntl.h>
#include<unistd.h>
#include<sys/stat.h>
int main()
{
    int fd;
    fd=mkdir("../Backup",0664);
    if(fd==0)
        printf("the directory is created successfully\n");
    else
        printf("the directory creation failed\n");
}
```

### 13. Write a C program to recursively list all files and directories in a given directory?
```c
#include<stdio.h>
#include<fcntl.h>
#include<unistd.h>
#include<string.h>
#include<dirent.h>
#include<sys/stat.h>

void list_files(const char *basepath)
{
    char path[1000];
    struct dirent *dp;
    DIR *dir=opendir(basepath);
    if(dir==0)
    {
        printf("error in opening directory\n");
        return;
    }
    while((dp=readdir(dir))!=NULL)
    {
        if(strcmp(dp->d_name,".")==0 || strcmp(dp->d_name,"..")==0)
            continue;
        snprintf(path,sizeof(path),"%s\t%s\n",basepath,dp->d_name);
        printf("%s\n",path);
        struct stat buf;
        if(stat(path,&buf)==0 && S_ISDIR(buf.st_mode))
            list_files(path);
    }
    closedir(dir);
}
int main(int argc,char *argv[])
{
    const char *start_path;
    if(argc<2)
        start_path=".";
    else
        start_path=argv[1];
    list_files(start_path);
}
```

###  14. Develop a C program to delete all files in a directory named "Temp"?
```c
#include<stdio.h>
#include<fcntl.h>
#include<unistd.h>
#include<string.h>
#include<dirent.h>
#include<sys/stat.h>

int main()
{
    DIR *dir;
    struct dirent *dp;
    char path[512];
    struct stat file_stat;
    dir=opendir(".");
    if(dir==NULL)
    {
        printf("failed to open a directory\n");
        return 0;
    }
    while((dp=readdir(dir))!=NULL)
    {
        if(strcmp(dp->d_name,".")==0 || strcmp(dp->d_name,"..")==0)
            continue;
        snprintf(path, sizeof(path), "./%s", dp->d_name);

        // Get file type
        if (stat(path, &file_stat) == 0) {
            if (S_ISREG(file_stat.st_mode)) {
                // Delete regular file
                if (remove(path) == 0)
                    printf("Deleted file: %s\n", path);
                else
                    perror("Failed to delete file");
            }
        }
    }

    closedir(dir);
    return 0;
}
```

### 15. Implement a C program to count the number of lines in a file named "data.txt"?
```c
#include<stdio.h>
#include<unistd.h>
#include<fcntl.h>
int main()
{
    int fd,ret,count=0;
    char buf[100];
    fd=open("file.txt",O_RDONLY);
    if(fd<0)
    {
        printf("error in opening a file\n");
        return 0;
    }
    while((ret=read(fd,buf,100))>0)
    {
       for(int i=0;i<ret;i++)
       {
           if(buf[i]=='\n')
            count++;
       }
    }
    buf[ret]='\0';
    if(ret<0)
    {
        printf("error in reading file\n");
        close(fd);
        return 0;
    }
    printf("the no of lines in a file are %d\n",count);
}
```

### 16. Write a C program to append "Goodbye!" to the end of an existing file named "message.txt"?
```c
#include<stdio.h>
#include<unistd.h>
#include<fcntl.h>
#include<string.h>
int main()
{
    int fd,ret,count=0;
    char buf[100];
    printf("enter data:");
    fgets(buf,100,stdin);
    fd=open("file.txt",O_WRONLY|O_APPEND);
    if(fd<0)
    {
        printf("failed to open a file\n");
        return 0;
    }
    ret=write(fd,buf,strlen(buf));
    if(ret<0)
    {
        printf("failed to write\n");
        close(fd);
        return 0;
    }
    printf("the append content is added successfully\n");
    
}
```

### 17. Implement a C program to change the permissions of a file named "file.txt" to readonly?
```c
#include<stdio.h>
#include<string.h>
#include<sys/stat.h>
int main()
{
    int res=chmod("file.txt",S_IRUSR|S_IRGRP|S_IROTH);
    printf("%d\n",res);
    if(res==-1)
        printf("failed to change permissions\n");
    else
        printf("permissions are changed to read only\n");
}
```

### 18. Write a C program to change the ownership of a file named "file.txt" to the user "user1"?
```c
#include<stdio.h>
#include<stdlib.h>
#include<unistd.h>
#include<sys/types.h>
#include<pwd.h>
#include<errno.h>
int main()
{
    const char *file_name="file.txt";
    const char *user="user1";
    struct passwd *pw=getpwnam(user);
    if(pw==NULL)
    {
        printf("error in getting present working directory\n");
        return 0;
    }
    uid_t new_uid=pw->pw_uid;
    gid_t new_gid=pw->pw_gid;
    if(chown(file_name,new_uid,new_gid)==-1)
    {
        printf("failed to change the ownership of the file\n");
        return 0;
    }
    printf("the ownerships is changed successfully\n");
}
```

### 19. Develop a C program to get the last modified timestamp of a file named "file.txt"?
```c
#include<stdio.h>
#include<sys/stat.h>
#include<time.h>
int main()
{
    struct stat file_stat;
    int res=stat("file.txt",&file_stat);
    if(res==-1)
    {
        printf("failed to get file information\n");
        return 0;
    }
    printf("the last modified time of file is %s\n",ctime(&file_stat.st_mtime));
}
```

### 20. Implement a C program to create a temporary file and write some data to it?
```c
#include<stdio.h>
#include<fcntl.h>
#include<unistd.h>
#include<string.h>
int main()
{
    int fd,ret;
    char buf[100];
    printf("enter a string:");
    fgets(buf,100,stdin);
    fd=open("temp.txt",O_WRONLY|O_CREAT,0777);
    if(fd<0)
    {
        printf("failed to open a file\n");
        return 0;
    }
    ret=write(fd,buf,strlen(buf));
    if(ret<0)
    {
        printf("failed to write\n");
        close(fd);
        return 0;
    }
    printf("the data is written successfully to file\n");
}
```

### 21. Write a C program to check if a given path refers to a file or a directory?
```c
#include<stdio.h>
#include<stdlib.h>
#include<sys/stat.h>
int main()
{
    char path[256];
    struct stat st;
    printf("enter path:");
    scanf("%s",path);
    if(stat(path,&st)!=0)
    {
        printf("failed to get information about the file\n");
        return 0;
    }
    if(S_ISREG(st.st_mode))
        printf("the file is a regular file\n");
    else if(S_ISDIR(st.st_mode))
        printf("the file is a directory\n");
    else
        printf("the file is not a regular file or directory\n");
}
```

### 22. Develop a C program to create a hard link named "hardlink.txt" to a file named "source.txt"?
```c
#include<stdio.h>
#include<stdlib.h>
#include<unistd.h>
int main()
{
    int res=link("file.txt","link.txt");
    if(res==0)
        printf("hardlink is created successfully\n");
    else
        printf("failed to create hardlink\n");
}
Hardlink is creating another label name for same inode object.
```

### 23. Implement a C program to read and display the contents of a CSV file named "data.csv"?
```c
#include<stdio.h>
#include<stdlib.h>
#include<unistd.h>
#include<fcntl.h>
int main()
{
    char buf[100];
    int ret,fd;
    fd=open("data.csv",O_RDONLY);
    if(fd<0)
    {
        printf("error in opening a file\n");
        return 0;
    }
    ret=read(fd,buf,100);
    if(ret<0)
    {
        printf("error in reading file\n");
        return 0;
        close(fd);
    }
    buf[ret]='\0';
    printf("the contents in csv file are %s\n",buf);
}
```

### 24. Write a C program to get the absolute path of the current working directory?
```c
#include<stdio.h>
#include<unistd.h>
int main()
{
    char cwd[100];
    char *res=getcwd(cwd,sizeof(cwd));
    if(res!=NULL)
        printf("the current working directory is %s",cwd);
    else
        printf("unable to get the current working directory\n");
}
```
25. Develop a C program to get the size of a directory named "Documents"?
26. Implement a C program to recursively copy all files and directories from one directory to another?
27. Write a C program to get the number of files in a directory named "Images"?
28. Develop a C program to create a FIFO (named pipe) named "myfifo" in the current directory?
29. Implement a C program to read data from a FIFO named "myfifo"?
30. Write a C program to truncate a file named "file.txt" to a specified length?
