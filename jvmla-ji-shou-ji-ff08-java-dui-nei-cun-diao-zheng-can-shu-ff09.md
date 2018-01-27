## 堆内存的参数调整（**调优关键**）

![](/assets/3081517039459_.pic_hd.jpg)

通过之前的分析可以发现，实际上每一块的子内存区都会存在有一部分的可变伸缩区。其基本流程为，则在可变的范围之内扩大内存空间，当一段时间之后发现内存空间没有这么紧张的时候，再将可变空间进行释放。

![](/assets/3091517047589_.pic_hd.jpg)

在这个堆内存的调整策略中，有经验的人基本上都只会调整两个参数：-Xmx（最大内存）、-Xms（初始化内存）。

如果要想取得这些内存的政体信息，直接利用Runtime类即可。

默认情况下分配的内存为总内存的1/4、而初始化内存为总内存的1/64。伸缩区为：491M~7276.5M之间，那么现在就有可能造成才程序的性能下降。最好的做法是让max和total保持一致。

java -Xmx16G -Xms16G TestDemo

那么这个时候就避免了伸缩去的可调策略，从而提升了整个的程序性能。

![](/assets/3101517048241_.pic_hd.jpg)

