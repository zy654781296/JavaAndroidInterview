### 法1：
- 创建一个HashMap，以1到100为键，值都是0 。然后遍历整个数组，每读到一个整数，就找到HashMap当中对应的键，让其值加一。由于数组中缺少一个整数，最终一定有99个键值等于1, 剩下一个键值等于0。遍历修改后的HashMap，找到这个值为0的键。假设数组长度是N，那么该解法的时间复杂度是O（1），空间复杂度是O（N）

### 法2：
- 先把数组元素进行排序，然后遍历数组，要么有其中两个相邻元素之间的差不是1，要么缺失的整数是1或100。假设数组长度是N，如果用时间复杂度为O（N*LogN）的排序算法进行排序，那么该解法的时间复杂度是O（N*LogN），空间复杂度是O（1）。

### 法3：
- 很简单也很高效的方法，先算出1+2+3....+100的合，然后依次减去数组里的元素，最后得到的差，就是唯一缺失的整数。假设数组长度是N，那么该解法的时间复杂度是O（N），空间复杂度是O（1）

_原文链接:_[https://mp.weixin.qq.com/s?__biz=MzIxMjE5MTE1Nw==&mid=2653189951&idx=1&sn=0181c95484b67d108672235b14e5ebbb&chksm=8c9905e5bbee8cf3362ccc4c7e091caa18b5783183ce4475b6f011c09c1cb03847ea4cb5220c&scene=21#wechat_redirect](https://mp.weixin.qq.com/s?__biz=MzIxMjE5MTE1Nw==&mid=2653189951&idx=1&sn=0181c95484b67d108672235b14e5ebbb&chksm=8c9905e5bbee8cf3362ccc4c7e091caa18b5783183ce4475b6f011c09c1cb03847ea4cb5220c&scene=21#wechat_redirect)
