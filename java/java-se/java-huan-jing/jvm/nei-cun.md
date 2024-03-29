http://dbaplus.cn/news-21-173-1.html
https://hacpai.com/article/1519403810488
https://tech.meituan.com/jvm_optimize.html


# 线程cpu占用bash 工具
``` java
#线程cpu占用
#!/bin/bash

[ $# -ne 1 ] && exit 1

jstack $1 >/tmp/jstack.log

for cpu_tid in `ps -mp $1 -o THREAD,tid,time|sort -k2nr| sed -n '2,15p' |awk '{print$2"_"$(NF-1)}'`;do

cpu=`echo $cpu_tid | cut -d_ -f1`

tid=`echo $cpu_tid | cut -d_ -f2`

xtid=`printf "%x\n" $tid`

echo -e "\033[31m========================$xtid $cpu%\033[0m"

cat /tmp/jstack.log | sed -n -e "/0x$xtid/,/^$/ p"

#cat /tmp/jstack.log | grep "$xtid" -A15

done

rm /tmp/jstack.log
```



# 故障排除流程

表现  
定性  
定位  
解决

# 具体排查流程
cpu高（应用超时，应用慢）->内存高->oom
1.确认进程线程     jstack信息，是VM线程则下一步GC
2.确认是否是GC问题  GC日志(软件system gc，内存大小) jamp dump(代码泄漏)
3.确认是否OOM  应用日志和GC日志（内存太小即类型）、dump(代码内存泄漏)



#### 确认进程线程 [jstack信息]
从jstack栈信息查看是否线程死循环、死锁、密集计算、sql查询
都不是且线程为VM线程一直GC，则确认是下一步GC问题
> top得进程ID---\> top -Hp \[进程 ID\]得线程ID
> jstack -l \[进程 ID\] &gt;jstack.log 得线程信息
> printf "%x\n" \[十进制数字\] ，可以将 10 进制转换成 16 进制
> 用16进制查看线程信息


#### 确认GC问题 [GC日志、jmap dump堆信息]
确认是Full GC：1.软件显示周期system gc、内存设置太小、代码内存泄漏
都不是下一步

> 确认Full GC：从GC日志可看出
> 周期system gc：从GC日志或jstat -gcutil可看出
(a.利用bTrance 确认谁调用systemgc b.确认是cxf工具包)


> 内存设置太小：查看jvm 参数
> 代码内存泄漏：dump文件 eclipse mat 可看出


#### 确认是否OOM [应用日志、jmap dump堆信息]
从应用日志查看是否outofmemory： 1内存设置太小、代码内存泄漏

> outofmemory：应用日志和是否自动生成dump文件
> 内存设置太小：查看jvm 参数
> 代码内存泄漏：dump文件 eclipse mat 可看出

应用日志可以看出outofmemory
1.heap space
2.perm space
3.direct memory
4.gc limt





先找到最耗CPU线程的信息，查看该线程是否死循环、死锁、密集计算、sql慢查询
如果是VM GC线程，则确认是GC问题
先查GC日志，确认是否是频繁Full GC 
再查JVM 参数，确实是否是内存太小   不是-->
再查GC日志，确认Full gc前后内存是否相差不大  不是-->
再查GC日志,确认Full gc是否是system gc 周期性调用







# 表现现象

cpu高、内存高、OOM、Full gc 频繁超时（应用超时 应用很慢）

##### 表现来源

* 1.提醒方式 推送模式： 监控软件超过阀值指标 推送短信或邮件提醒！！！！
* 2.人工观察 拉模式  ： 出现问题或压测时 输入命令如jstat -gcutil 观察gc情况定位问题
  > 无论是推送模式还是拉模式，都是呈现现象来源  
  > 如推送：监控Cpu高提醒短信；如手拉：top 观察到Cpu高

# cpu 高（可能内存也高）

| 定位Java进程、线程 | 如果线程是VM线程 并一直GC | 如果线程非VM线程，即查看该线程问题 |
| :--- | :--- | :--- |
|  | 1.查看GC日志情况，是不是频繁Full gc | 线程死循环、死锁、锁、密集运算、sql慢操作 |
|  | 2 jmap -dump 内存情况 dump 文件 |  |
|  | 3 eclipse mat 分析dump文件没问题 |  |
|  | 4.利用bcTrance 确认谁调用systemgc |  |
|  | 5确认是cxf工具包 |  |
|  |  |  |
|  |  |  |

* 1.先定位java进程、线程
* 2.知道是GC 回收线程,或线程在干嘛
* 3.dump文件 mat 定位对象
* 4.GC 文件分析 确定 内存、对象没问题   确定是不是软件的问题定时调用
* 5.理由bcTrance 确认谁调用system gc
* 6.确认是cxf工具包1.先定位java进程、线程

##### 定位进程、线程

* 1.通过 top 命令找到 CPU 消耗最高的进程，并记住进程 ID。
* 2.再次通过 top -Hp \[进程 ID\] 找到 CPU 消耗最高的线程 ID，并记住线程 ID.
* 3.通过 JDK 提供的 jstack 工具 dump 线程堆栈信息到指定文件中。具体命令：\* 4.jstack -l \[进程 ID\] &gt;jstack.log。
* 5.由于刚刚的线程 ID 是十进制的，而堆栈信息中的线程 ID 是 16 进制的，因此我们需要将 10 进制的转换成 16 进制的，并用这个线程 ID 在堆栈中查找。使用 printf "%x\n" \[十进制数字\] ，可以将 10 进制转换成 16 进制。
* 6.通过刚刚转换的 16 进制数字从堆栈信息里找到对应的线程堆栈。就可以从该堆栈中看出端倪

###### 



