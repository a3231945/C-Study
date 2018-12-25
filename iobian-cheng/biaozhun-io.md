**打开:**

	FILE *fopen(const char *path, const char *mode)
	功能：按照指定的模式打开或创建一个文件。
	返回值：成功返回FILE *的指针， 失败返回NULL;
	参数：
		1.const char *path, 需要打开或创建的文件名字。
		2.cosnt char *mode, 指定打开的模式：
			"r": 以只读模式打开一个文件，如果不存在则出错返回。
			"r+"：以读写模式打开一个文件， 如果不存在则出错返回。
			"w"： 以只写方式打开一个文件，如果存在则清空，不存在则创建。
			"w+"：以读写方式打开一个文件，如果存在则清空， 不存在则创建。
			"a"： 以只写追加方式打开一个文件， 如果存在则定位到文件末尾写入，否则创建。
			"a+"：以读写追加方式打开一个文件， 如果不存在则创建， 文件存在则位置指针在写入时定位到末尾， 读取时定位开头。

**关闭：**

	int fclose(FILE *fp)
	功能：关闭一个文件流。
	返回值：成功0， 失败-1。
	参数：
		FILE *fp, 一个文件流指针（通常由fopen返回）。

**写入：**

	int fputs(const char *str, FILE *fp);
	功能：把str指向的字符串写入fp指向的文件流中。
	返回值：
		成功返回非负的整数， 失败返回EOF.
	参数：
		1.const char *str, 要写入的字符串。
		2.FILE *fp, 要写入的文件流指针。


	int fwrite(const void *buff, size_t size, size_t n, FILE *fp);
	功能： 将存在于buff的n块数据写入文件，每块大小是size字节。
	返回值：成功返回写入的块数， 失败返回一个比n小的数或0.
	参数：
		1. const void *buff, 用户的数据空间地址。
		2. size_t size, 每块数据的大小。
		3. size_t n, 期望写入的数据块数。
		4. FILE *fp, 文件流指针。

	fputc
	fprintf

**读出：**

	char *fgets(char *buff, size_t size, FILE *fp);
	功能： 从一个文件流中读取顶多size-1个字符的一行字符串，并存储到buff指向的缓冲区中。
	返回值：成功返回buff, 出错或者到达文件末尾则返回NULL。
	参数：
		1. char *buff, 用户自己指定的缓冲区地址。
		2. size_t size， 用户指定缓冲区的大小。
		3. FILE *fp, 要读的文件流指针。


	int fread(void *buff, size_t size, size_t n, FILE *fp);
	功能： 从文件流fp中读取n快数据存放到buff中，每块大小是size字节。
	返回值：成功返回实际读到的块数（而不是字节数）， 失败返回比期望小的数或0.	
	参数：
		1. void *buff, 用户的数据空间地址。
		2. size_t size, 每块数据的大小。
		3. size_t n, 期望读取的数据块数。
		4. FILE *fp, 文件流指针。


	fgetc
	fscanf

**定位：**

	int fseek(FILE *fp, long offset, int whence);
	功能：设定文件流的文件位置指示器。
	返回值： 成功，0； 失败， -1；
	参数：
		1. FILE *fp, 文件流指针。
		2. long offset, 偏移量，以字节为单位。
		3. int whence, 起始位置：
			SEEK_SET: 从文件头开始。
			SEEK_CUR: 从当前位置开始。
			SEEK_END：从文件尾开始。
	
	long ftell(FILE *fp);
	功能：返回文件当前的位置偏移量。
	返回值：long， 文件的位置偏移量（相对于文件头， 以字节为单位）；
	参数：
		FILE *fp, 文件流指针。

	void rewind(FILE *fp);
	功能：将fp指向的文件流的位置指针重置为开头。
	返回值：无，不会失败。
	参数：
		FILE *fp, 需要重定位的文件流指针。


**临时文件：**
	
	FILE *tmpfile(void);
	功能： 创建并打开一个无名临时文件。
	返回值：成功， FILE *fp； 失败， NULL;
	参数： 无。

	char *tmpnam(char *buff);
	功能： 生成一个唯一的临时文件名（但是并没有创建文件，需要用户自己手动建）。
	返回值： 成功，文件名的指针； 失败， NULL;
	参数：
		char *buff: 用户可以指定接受名字的缓冲区，此时该函数会将文件名写入用户指定的缓冲区;或者传递NULL,此时文件名通过函数的返回值返回。
	