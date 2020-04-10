---
title: 命名管道和进程通讯
categories: notes
tags: [c#,python,learning]
date: 2020-03-10 13:36:26
---


## 概况
参考<https://blog.csdn.net/wh_sjc/article/details/70283843>  
IPC（进程间通讯）的方式通常有管道（包括无名管道和命名管道）、消息队列、信号量、共享存储、Socket、Streams等。

## 命名管道
“命名管道”是一种简单的进程间通信（IPC）机制，命名管道可在同一台计算机的不同进程之间或在跨越一个网络的不同计算机的不同进程之间，支持可靠的、单向或双向的数据通信。

## python中的命名管道
参考<https://blog.csdn.net/kongxx/article/details/78037069>  
<https://www.programcreek.com/python/example/62752/win32pipe.PIPE_WAIT>  
<https://www.cnblogs.com/achillis/p/10462585.html>  
 
在 Windows 上的命名管道主要是通过调用 win32 api 的以下方法来实现的

### server端
```python
import win32file
import win32pipe

PIPE_NAME = r'\\.\pipe\test_pipe'
PIPE_BUFFER_SIZE = 65535

while True:
    named_pipe = win32pipe.CreateNamedPipe(PIPE_NAME,
                                           win32pipe.PIPE_ACCESS_DUPLEX,
                                           win32pipe.PIPE_TYPE_MESSAGE | win32pipe.PIPE_WAIT | win32pipe.PIPE_READMODE_MESSAGE,
                                           win32pipe.PIPE_UNLIMITED_INSTANCES,
                                           PIPE_BUFFER_SIZE,
                                           PIPE_BUFFER_SIZE, 500, None)

    try:
        while True:
            try:
                win32pipe.ConnectNamedPipe(named_pipe, None)    #连接管道
                data = win32file.ReadFile(named_pipe, PIPE_BUFFER_SIZE, None)   #接收消息
                win32file.WriteFile(named_pipe, bytes("OK", encoding='utf-8'))  #发送消息(二进制)

                if data is None or len(data) < 2:
                    continue

                print('receive msg:', data)
            except BaseException as e:
                print("exception:", e)  
                break
    finally:
        try:
            win32pipe.DisconnectNamedPipe(named_pipe)   #断开连接
        except:
            pass
```

### client客户端
```python
import win32pipe, win32file
import time

PIPE_NAME = r'\\.\pipe\test_pipe'

file_handle = win32file.CreateFile(PIPE_NAME,
                                   win32file.GENERIC_READ | win32file.GENERIC_WRITE,
                                   win32file.FILE_SHARE_WRITE, None,
                                   win32file.OPEN_EXISTING, 0, None)    # 连接管道
try:
    for i in range(1, 11):
        msg = str(i)
        print('send msg:', msg)
        win32file.WriteFile(file_handle, bytes(msg,encoding='utf-8'))   # 发送信息
        time.sleep(1)
        data = win32file.ReadFile(file_handle, 65535, None) # 接收信息(阻塞)
        print(data)
finally:
    try:
        win32file.CloseHandle(file_handle)  # 关闭连接
    except:
        pass
```

## C#中的命名管道

### server端
```C#
NamedPipeServerStream server = new NamedPipeServerStream("test_pipe", PipeDirection.InOut, 100, PipeTransmissionMode.Byte, PipeOptions.None, 65535, 65535);
server.WaitForConnection();

while (server.IsConnected)
    {
        int n = server.Read(res, 0, 65535); //接收信息

        string s = System.Text.Encoding.UTF8.GetString(res,0,n);

        Console.WriteLine(s);

        n = Encoding.UTF8.GetBytes(s, 0, s.Length, res, 0);

        server.Write(res, 0, n);    //发送信息
    }
```

### client端
```C#
    NamedPipeClientStream client = new NamedPipeClientStream("test_pipe");
    client.Connect();
    

    while (client.IsConnected)
    {
        int n = client.Read(res, 0, 65535);

        string s = System.Text.Encoding.UTF8.GetString(res,0,n);

        Console.WriteLine(s);

        n = Encoding.UTF8.GetBytes(s, 0, s.Length, res, 0);

        client.Write(res, 0, n);
    }
```

## python和C#交互代码示例
python端  
```python
import win32file
import win32pipe

PIPE_NAME = r'\\.\pipe\test_pipe'
PIPE_BUFFER_SIZE = 65535
import time

while True:
    named_pipe = win32pipe.CreateNamedPipe(PIPE_NAME,
                                           win32pipe.PIPE_ACCESS_DUPLEX,
                                           win32pipe.PIPE_TYPE_MESSAGE | win32pipe.PIPE_WAIT | win32pipe.PIPE_READMODE_MESSAGE,
                                           win32pipe.PIPE_UNLIMITED_INSTANCES,
                                           PIPE_BUFFER_SIZE,
                                           PIPE_BUFFER_SIZE, 500, None)

    try:
        while True:
            try:
                win32pipe.ConnectNamedPipe(named_pipe, None)

                win32file.WriteFile(named_pipe, bytes("hello", encoding='utf-8'))

                data = win32file.ReadFile(named_pipe, PIPE_BUFFER_SIZE, None)
                time.sleep(1)

                # data = str.encode()

                if data is None or len(data) < 2:
                    continue

                print('receive msg:', data)
            except BaseException as e:
                print("exception:", e)
                break
    finally:
        try:
            win32pipe.DisconnectNamedPipe(named_pipe)
        except:
            pass
```
C#端
```C#
 static void Main(string[] args)
    {
    byte[] res = new byte[65535];

        NamedPipeClientStream client = new NamedPipeClientStream("test_pipe");
        client.Connect();
        

        while (client.IsConnected)
        {
            int n = client.Read(res, 0, 65535);

            string s = System.Text.Encoding.UTF8.GetString(res,0,n);

            Console.WriteLine(s);

            n = Encoding.UTF8.GetBytes(s, 0, s.Length, res, 0);

            client.Write(res, 0, n);
        }
    }
```
