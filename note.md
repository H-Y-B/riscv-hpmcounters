## 信号机制

ref link :[Linux的信号机制](https://blog.csdn.net/qq_37653144/article/details/81942026)

ref linl :[Linux信号（signal) 机制分析](https://www.cnblogs.com/subo_peng/p/5325326.html)

## 信号处理

ref link :[sigemptyset、sigaddset、sigprocmask的用法 信号未决，信号阻塞 信号的捕捉](https://blog.csdn.net/u012736748/article/details/75040897)

## 信号含义

① SIGINT     终止进程     中断进程

程序终止(interrupt)信号, 在用户键入INTR字符(通常是Ctrl-C)时发出。

② SIGQUIT    建立CORE文件终止进程，并且生成core文件

③ SIGQUIT 和 SIGINT 类似，但由QUIT字符(通常是Ctrl-)来控制；进程在因收到SIGQUIT退出时会产生core文件，在这个意义上类似于一个程序错误信号。

④ SIGKILL    终止进程     杀死进程

⑤ SIGPIPE    终止进程     向一个没有读进程的管道写数据

⑥ SIGALARM    终止进程     计时器到时

⑦ SIGTERM    终止进程     软件终止信号

⑧ SIGTERM 程序结束(terminate)信号，与SIGKILL不同的是该信号可以被阻塞和处理。通常用来要求程序自己正常退出。shell命令kill缺省产生这个信号。SIGTERM is the default signal sent to a process by the kill or killall commands.

⑨ SIGURG    忽略信号     I/O紧急信号

⑩ SIGIO    忽略信号     描述符上可以进行I/O

11 SIGCHLD    忽略信号     当子进程停止或退出时通知父进程

有两个信号可以停止进程：SIGTERM和SIGKILL。

**SIGTER**M比较友好，进程能捕捉这个信号( it can be caught and interpreted (or ignored) by the process)，根据您的需要来关闭程序。在关闭程序之前，您可以结束打开的记录文件和完成正在做的任务。在某些情况下，假如进程正在进行作业而且不能中断，那么进程可以忽略这个SIGTERM信号。

对于**SIGKILL**信号，进程是不能忽略的( this signal cannot be caught or ignored,)。这是一个“我不管您在做什么,立刻停止”的信号。假如您发送SIGKILL信号给进程，Linux就将进程停止在那里。