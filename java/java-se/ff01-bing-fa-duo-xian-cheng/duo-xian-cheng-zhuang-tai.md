![](/assets/20190816122658582.png)

#### sleep()，wait()，yield()和join()方法的区别
https://blog.csdn.net/xiangwanpeng/article/details/54972952

join()方法会使当前线程等待调用join()方法的线程结束后才能继续执行

###　automInteger 原理

乐观锁：Volatile变量+CAS+自旋。 Unsafe在jdk8已经封装了getAndAddInt可以直接给AtomicXXXXX类使用

``` java

public final int incrementAndGet() {
        for (;;) {
            int current = get();
            int next = current + 1;
            if (compareAndSet(current, next))
                return next;
        }
    }

``` 
