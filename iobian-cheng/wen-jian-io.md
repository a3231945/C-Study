文件描述符是一个非负的整数，用来在进程中唯一标记一个打开的文件。
每次打开文件，系统总是选取当前进程中未被使用的最小的编号，作为本次的文件描述符。
每个进程默认能够打开的文件格式是1024个，因此文件描述符的范围是0 - 1023

    每个进程默认会打开3个文件：
        标准输入： 0
        标准输出： 1
        标准错误： 2
        
    因此一般情况下，用户打开的第一个文件描述符通常是3
    
    
**打开：**
    
    只打开不创建：
        int open(const char *path, int flag);
        
    创建并打开：
        
        int open(const char *path, int flag, mode_t mode);
    返回值： 
        成功： 非负整数
        失败： -1
        
    参数：
        const char *path：需要打开或创建的文件路径
        int flag:文件标志位（创建，状态等标志位）
            O_CREAT, O_APPEND, O_RDONLY,O_WRONLY,O_RDWR,O_TRUNC,O_EXCL
        mode_t mode:在创建文件时（O_CREAT)有效，指定新文件的权限，如0644
        
    创建并打开文件：
        create() 等价于 open(filename,O_CREAT|O_WRONLY|O_TRUNC,mode)
        
**关闭：**
    
    int close(int fd);
    功能： 关闭一个文件描述符
    返回值： 
        成功： 0
        失败： -1
    参数：
        int fd：已经打开的文件描述符

**读取：**
    
    ssize_t read(int fd,void *buff, size_t size);
    功能：从一个文件描述符中读取指定的数据
    返回值：
        成功： 非负整数
        失败： -1
        文件末尾： 0
    参数：
        int fd：需要读取的文件描述符
        void *buff:用户数据缓冲区，用来存放读到的数据
        size_t size:指定读取的数据大小，以字节为单位，其中size_t 等价于unsigned int
        
**写入：**
    
     ssize_t write(int fd, const void *buff, sieze_t size);
     功能：向一个文件描述符中写入指定大小的数据
     返回值：
         成功： 实际写入的字节数
         失败：-1
         未写入：0
     参数： 
         int fd:需要写入的文件描述符
         const void *buff:需要读取的数据缓存区
         size_t size:指定写入的数据大小，以字节为单位
         
** 定位：**
     
     /*等价于 fseek*/
     off_t lseek(int fd, off_t offset, int whence);
     功能：设置文件位置的偏移量，并返回新的位置
     返回值：
         成功：新的文件位置
         失败：-1
         off_t 等价于long
     参数：
         int fd:需要操作的文件描述符
         off_t offset:偏移量，以字节为单位
         int whence:起始位置
             SEEK_SET: 从文件头开始
             SEEK_CUR: 从当前位置开始
             SEEK_END: 从文件尾开始
     
     /*等价于 rewind*/        
     lseek(fd,0,SEEK_SET)
     
     /*等价于 ftell*/
     lseek(fd,0,SEEK_CUR);
     
文件状态： `stat();`

其他函数接口：
    
    getpwuid
    getgrgid
    remove
    link
    unlink
    symlink
    time

目录接口：
    
    opendir
    readdir
    chdir
    getcw
    mkdir
    rmdir
