https://zhuanlan.zhihu.com/p/59861022

# G1收集器的应用场景
- 服务端多核CPU、JVM内存占用较大的应用（至少大于4G）
- 应用在运行过程中会产生大量内存碎片、需要经常压缩空间
- 想要更可控、可预期的GC停顿周期，防止高并发下应用雪崩现象

#### G1之前的JVM内存模型
![](/assets/v2-f0dce4cd9774335782e20e01a14fb55a_hd.jpg)

#### G1收集器的内存模型
- 区域(Region)的大小可以通过-XX:G1HeapRegionSize参数指定，大小区间最小1M、最大32M，总之是2的幂次方
- 每个Region被标记了E、S、O和H，这些区域在逻辑上被映射为Eden，Survivor和老年代
- Humongous区域是为了那些存储超过50%标准region大小的对象而设计的，它用来专门存放巨型对象。如果一个H区装不下一个巨型对象，那么G1会寻找连续的H分区来存储。为了能找到连续的H区，有时候不得不启动Full GC
![](/assets/v2-8f3ff3c893b1460062885e5122adf4bb_hd.jpg)

# G1收集器的阶段分以下几个步骤
![](/assets/v2-2658c595b28461db9d6c25ae99d41508_hd.jpg)
#### 筛选回收
首先对各个Regin的回收价值和成本进行排序，根据用户所期待的GC停顿时间指定回收计划，回收一部分Region

# G1的GC模式 Young GC和Mixed GC
##### 1.YoungGC

- 根扫描,跟CMS类似，Stop the world，扫描GC Roots对象。
- 处理Dirty card,更新RSet.
- 扫描RSet,扫描RSet中所有old区到young区或者survivor区的引用。
- 拷贝扫描出的存活的对象到survivor2/old区
- 处理引用队列，软引用，弱引用，虚引用

##### 2. mixed gc

当越来越多的对象晋升到老年代old region时，为了避免堆内存被耗尽，虚拟机会触发一个混合的垃圾收集器，即mixed gc，该算法并不是一个old gc，除了回收整个young region，还会回收一部分的old region，这里需要注意：是一部分老年代，而不是全部老年代，可以选择哪些old region进行收集，从而可以对垃圾回收的耗时时间进行控制。

G1没有fullGC概念，需要fullGC时，调用serialOldGC进行全堆扫描（包括eden、survivor、o、perm）


