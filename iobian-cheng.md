打开：

    FILE *fopen(const char *path,const char *mode)
    功能:按照指定的模式打开或创建一个文件
    返回值：成功返回FILE *的指针，失败返回NULL
    参数：
        1.const char* path 需要打开或创建的文件名字
        2.const char* mode 指定打开文件的模式：
        
            r： 以只读模式打开一个文件，如果不存在则出错返回
            r+: 以读写模式打开一个文件，如果不存在则出错返回
            w:  以只写方式打开一个文件，如果存在则清空，不存在则创建
            w+: 以读写方式打开一个文件，如果存在则清空，不存在则创建
            a: 以只写追加方式打开一个文件，如果存在则定位到文件末尾写入，否则创建
            a+：以读写追加方式打开一个文件，如果不存在则创建，文件存在则 写指针定位到末尾，读指针定位到开头
            
关闭:

    int fclose(FILE *fp)
    功能：关闭一个文件流
    返回值：成功0，失败-1
    参数：FILE *fp，一个文件流指针（通常由fopen返回）
    
写入：

    int fputs（const char *str，FILE *fp）
    
    int fwrite（const void *buff, size_t size, sizt_t n,FILE *fp)
    
    fputc
    fprintf

读出：

    char *fgets(char *buff, size_t size, FILE *fp)
    
    int fread(void *buff, size_t size, size_t n, FILE *fp)
    
    fgetc
    fscanf
    
定位:
    
    int fseek(FILE *fp, long offset, int whence)
    
    long ftell(FILE *fp)
    
    void rewind(FILE *fp)
    
临时文件：

    FILE *tmpfile(void);
    
    char *tmpnam(char *buff)