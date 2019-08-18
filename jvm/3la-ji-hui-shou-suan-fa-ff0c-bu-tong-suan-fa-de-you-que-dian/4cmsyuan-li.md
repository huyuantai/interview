#1.初次标记 Stop the World
- 1.标记老年代中所有的GC Roots；
- 2.标记被 年轻代中 活着的对象 引用的老年代对象
![](/assets/图片1.png)

#2.并发标记