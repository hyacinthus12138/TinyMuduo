# 简要说明

与原版muduo库相比：

    移除了boost库，使用c++11标准库代替。

    只用了epoll实现主要功能。

    线程，锁等使用了C++11标准库提供的组件，代码更精简。

## 1. 编译&&安装

    硬性要求：linux环境，C++编译器支持C++11标准。
    测试环境：
        ubuntu24.04,
        g++ 11.4.0,
        GNU Make 4.3,
        cmake version 3.28.3
    
    编译&&安装：
        git clone git@github.com:hyacinthus12138/TinyMuduo.git
        cd TinyMuduo
        mkdir build
        cd build
        cmake ..
        make 
        sudo make install

    测试回显服务器：
        cd test
        ./echoserver
        ## 正常安装的话已经开始打印信息了，并等待客户端连接

    测试回显客户端：
        telnet 127.0.0.1 8000
        ## 输入任意字符，回车后，会打印出客户端输入的字符

## 2. 主要组件说明

[1. 主要组件说明](docs/basicClass.md)

[2. 连接流程说明](docs/basicConnectModel.md)

[3. 读写流程说明](docs/basicReadWriteModel.md)

[4. 关闭流程说明](docs/basicCloseModel.md)

[5. one loop per thread 模型](docs/basicOneLoopPerThreadModel.md)



## 3. 压力测试 WebBench

    webbench -c 500 -t 30 http://127.0.0.1:8080/
    环境：ubuntu24.04, 4核8G, 6代i5

    ------------ 本机测试 127.0.0.1 -------------
    Benchmarking: GET http://0.0.0.0:8000/
500 clients, running 30 sec.

Speed=23244 pages/min, 22856 bytes/sec.
Requests: 11622 susceed, 0 failed.

    ------------ 公网测试 -------------
    qps:2000左右，主要瓶颈在网络发包上，完全吃不满cpu

