通用结构体：

    struct sockaddr {
        sa_family_t sa_family; // unsigned short 指定了通信协议家族
        char sa_data[14];
    }
    
IPV4网络通信地址结构体：

    struct sockaddr_in {
        sa_family_t sin_family;
        in_port_t   sin_port;
        struct in_addr{
            unsigned int s_addr;
        }sin_addr;    
    }
    
UNIX本体通信地址结构体：

    struct sockaddr_un {
        sa_family_t sun_family;
        char        sun_path[UNX_PATH_MAX];
    }
    
- socket


    int socket(int domain, int type, int protocl)
    功能：打开一个套接字，并返回一个相关的文件描述符
    返回值：
        成功： 一个新的文件描述符
        失败： -1
    参数：
        int domain: 通信域
            AF_INET|AF_INET6| AF_UNIX|AF_PACKET
        int type:套接字类型
            SOCK_STREAM  流式套接字
            SOCK_DGRAM   数据报套接字
            SOCK_RAW     原始套接字
        int protocl:协议(在原始套接字中根据需要选择使用，流式或数据报套接字中为0)
        
- bind


    int bind(int sockfd, const struct sockaddr *addr, socklen_t addrelen);
    功能：为一个打开的套接字，保定一个地址（IP+PORT）
    返回值：
        成功： 0
        失败： -1
    参数：
        int sockfd:通过socket 打开并返回的文件描述符
        const struct sockaddr * addr:通用结构体地址，更具通信域选择相关的地址格式
        socklen_t addrlen:实际地址结构体的大小

- listen


    int listen(int sockfd, int backlog)
    功能：将一个经过bind的套接字置为被动状态，以便来使用accept接收新的请求
    返回值：
    成功： 0
    失败： -1
    参数：
    int sockfd: 通过socket创建，并通过bind后的套接字描述符
    int backlog:握手请求队列的最大值
- accept


    int accept(int sockfd,struct sockaddr* addr socklen_t addrlen)
    功能：接收一个握手请求，并返回一个新的文件描述符
    返回值：
    成功：新的文件描述符(用来收发数据的通道)
    失败：-1
    参数：
    int sockfd:经过socket创建，bind后并且listen后的文件描述符
    sturct sockaddr *addr:用来待会握手请求方的地址结构体
    socklen_t addrlen:期望接收的对方的地址大小，该值会被修改为实际大小，调用者需要提前初始化
               
- sendto
    
    
    int sendto(int sockfd,void *buff, size_t size, int flag,const sockaddr *addr, socklen_t addrlen)
    功能：向一个指定的目标主机发送数据包
    返回值：
        成功：实际发送的字节数
        失败：-1
    参数：
        int sockfd：通过socket打开并返回的文件描述符
        void *buff:即将发送的数据
        size_t size:数据大小
        int flag:发送标志位(阻塞，非阻塞等，如果无特殊要求则设置为0)
        const struct sockaddr * addr:目标主机的地址结构体(IP+PORT)
        socklen_t addrlen:目标主机结构体大小
        
- recvfrom


    int recvfrom(int sockfd, void *buff, size_t size,int flag,struct sockaddr *addr, socklen_t *addrlen)
    功能：接受一个数据包，并待会数据报的来源地址
    返回值：
        成功：实际接收的字节数
        失败：-1
        对方关闭：0
    参数：
        int sockfd：通过socket打开并返回的文件描述符
        void *buff: 接受数据的缓存区
        size_t size: 缓冲区大小
        int flag: 接收标志位(阻塞、非阻塞等，如果无特殊要求则设置为0)
        struct sockaddr *addr:用来保存数据来源主机的地址结构体(IP+PORT)
        socklen_t *addrlen:期望接收的数据源主机的地址结构体大小(在使用前由用户自己初始化)，一旦该函数调用结束，该变量会被改为实际大小


- select


    int select(int nfds, fd_set *rdfds, fd_set *wrfds, fdset *exceptfds, struct timeval *timeval)
    功能：在多路IO复用模型中，负责
    返回值：
        成功：资源个数
        失败：-1
    参数：
    
    
    