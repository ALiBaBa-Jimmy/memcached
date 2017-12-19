解压

# tar xzvf memcached-1.4.25.tar.gz

#cd memcached-1.4.25




配置

#./configure --prefix=/usr/local/memcached --with-libevent=/usr

注意这里选择libevent的位置就可以  比如你的是在–with-libevent=/usr/local/libevent/

# ./configure --prefix=/usr/local/memcached --with-libevent=/usr/local/libevent




编译安装

# make && make install


# wget https://github.com/libevent/libevent/releases/download/release-2.0.22-stable/libevent-2.0.22-stable.tar.gz
# tar xzvf libevent-2.0.22-stable.tar.gz
# cd libevent-2.0.22-stable
# ./configure --prefix=/usr/local/libevent
# make && make install


启动

# /usr/local/memcached/bin/memcached -d -m 100 -uroot -l 0.0.0.0 -p 11211 -c 512 -P /usr/local/memcached/memcached.pid





启动參数：
memcached 1.4.2
-p <num>      监听的TCPport(默认: 11211)
-U <num>      监听的UDPport(默认: 11211, 0表示不监听)
-s <file>     用于监听的UNIX套接字路径（禁用网络支持）
-a <mask>     UNIX套接字訪问掩码，八进制数字（默认：0700）
-l <ip_addr>  监听的IP地址。

（默认：INADDR_ANY。全部地址）
-d            作为守护进程来执行。


-r            最大核心文件限制。
-u <username> 设定进程所属用户。

（仅仅有root用户能够使用这个參数）
-m <num>      单个数据项的最大可用内存，以MB为单位。（默认：64MB）
-M            内存用光时报错。（不会删除数据）
-c <num>      最大并发连接数。（默认：1024）
-k            锁定全部内存页。注意你能够锁定的内存上限。
              试图分配很多其它内存会失败的，所以留意启动守护进程时所用的用户可分配的内存上限。
              （不是前面的 -u <username> 參数。在sh下。使用命令"ulimit -S -l NUM_KB"来设置。

）
-v            提示信息（在事件循环中打印错误/警告信息。）
-vv           具体信息（还打印client命令/响应）
-vvv          超具体信息（还打印内部状态的变化）
-h            打印这个帮助信息并退出。
-i            打印memcached和libevent的许可。


-P <file>     保存进程ID到指定文件，仅仅有在使用 -d 选项的时候才有意义。


-f <factor>   块大小增长因子。（默认：1.25）
-n <bytes>    分配给key+value+flags的最小空间（默认：48）
-L            尝试使用大内存页（假设可用的话）。提高内存页尺寸能够降低"页表缓冲（TLB）"丢失次数，提高执行效率。


              为了从操作系统获得大内存页。memcached会把全部数据项分配到一个大区块。


-D <char>     使用 <char> 作为前缀和ID的分隔符。


              这个用于按前缀获得状态报告。

默认是":"（冒号）。
              假设指定了这个參数。则状态收集会自己主动开启。假设没指定，则须要用命令"stats detail on"来开启。
-t <num>      使用的线程数（默认：4）
-R            每一个连接可处理的最大请求数。
-C            禁用CAS。
-b            设置后台日志队列的长度（默认：1024）
-B            绑定协议 - 可能值：ascii,binary,auto（默认）
-I            重写每一个数据页尺寸。调整数据项最大尺寸。








查看详情

#ps aux|grep mem    

输出pid

#cat /usr/local/memcached/memcached.pid

 

状态

# telnet 127.0.0.1 11211
