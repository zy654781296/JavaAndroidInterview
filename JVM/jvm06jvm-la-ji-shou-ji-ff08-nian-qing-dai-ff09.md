## 年轻代

所有的新对象都会在年轻代产生，如果年轻代空间不足无法产生对象则会引发Minor GC和Major GC(Full GC)，还会抛出OOM的异常。

![](/assets/3161517053379_.pic_hd.jpg)

所有使用关键字new新实例化的对象一定会在伊甸园区进行保存，而我们对于存活区保存的一定是已经在伊甸园区域中存在好久并且经过好几次Minor GC还保存下来的活跃对象。那么这个对象将晋升到存活区之中，存活区一定会有两块空间，这两块空间的大小一定是相等的，目的是：一块存活区为了晋升，另外一块存活区为了对象回收。这两个空间的from和to是可以互相换的。这两块内存空间一定有一块是空的。

![](/assets/3171517064875_.pic_hd.jpg)

在年轻代中使用的是Minor GC，这种GC的算法采用的是复制算法。

**本质：把一个空间的数据复制到另外一个空间，而后这个空间的空间将被省略下来进行释放。**

年轻代的GC只复制年轻代的扫描。

通过以上的分析可以发现，在整个的处理过程之中，伊甸园区里面保存的对象有可能大部分都属于临时对象，那就有可能频繁的发生Minor GC，所以在HotSpot虚拟机之中为了加快此空间的内存分配的操作形式，所以采用了两种技术：

![](/assets/3181517065884_.pic_hd.jpg)

1. 栈顶指向新对象：
![](/assets/3191517065935_.pic_hd.jpg)

2. 把伊甸园区分成若干个子区域，在各自的区域里面分别进行栈顶的操作：
![](/assets/3201517066804_.pic_hd.jpg)

![](/assets/3211517067045_.pic_hd.jpg)

改变存活区的比率：

![](/assets/3231517067551_.pic_hd.jpg)

小结：

1. 年轻代的GC用的是Minor GC，而Minor GC的算法用的是复制算法。

2. 总有一个存活区是空的，两个存活区的大小永远是相同的。