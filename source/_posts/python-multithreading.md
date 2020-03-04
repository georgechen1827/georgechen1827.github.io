---
title: python多线程、多进程
categories: notes
tags: [python,learning]
date: 2020-03-04 11:36:58
---

浅尝辄止,能用就行

---

## 多线程

```python
import threading

lock = threading.Lock() # 设置一个全局线程锁,某个线程在获得此锁之后其他线程不能再获得

sem = threading.Semaphore(12) # 设置最大线程数量

with sem:
    t = threading.Thread(target=function,args=(a,b,c))  # 用function(a,b,c)创建一个线程
    t.setDaemon(True)   #   设置t线程为主线程的守护线程,即主线程结束后会自动杀死子线程(默认为false)
    t.start()   # 启动线程
    t.join(60)  # 线程同步，主线程任务结束之后，进入阻塞状态，一直等待其他的子线程执行结束之后，主线程再终止;如果超时主线程也会终止(默认为无)
    
#   若在function中执行lock.acquire(),则线程阻塞直到其他线程释放此锁
#   function中执行完lock.acquire()后必须进行lock.release(),否则其他线程将永远无法获得此锁
```

## 多进程

多进程与多线程运用方式相仿

```python
import multiprocessing

lock = multiprocessing.Lock()   # 设置一个全局进程锁,某个进程在获得此锁之后其他进程不能再获得

p = multiprocessing.Pool(72)    # 建立一个进程池,设置最大的进程数量

p.apply_async(func=function,args=(a,))  # 用function(a)创建一个进程

p.close()   #   关闭进程池,不再接受新的进程
p.join()    #   主进程阻塞,等待其他进程结束
```

注: windows中多线程的代码应当写道`if __name__ == 'main'`中
