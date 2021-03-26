## hashset底层实现与去重原理

HashSet是基于HashMap实现的，底层数据结构是哈希表

特点：

* 因为HashMap是无序的，因此HashSet也**不能保证元素的顺序**
* 因为HashSet中没有对应同步的操作，因此是线程不安全的
* 支持null元素(因为hashMap也支持null键和null值)
* HashSet利用本身的值来计算hash值，因为值被当作hashmap的key，而hashmap是利用key来计算hash值的
* 因为hashset将value当作key来存储，所以根据map的key值唯一的原理，我们就可以实现set的无重复元素的功能

保证元素唯一性：

利用hashcode() equals()两个方法 缺一不可

它的add()方法实际上调用的是HashMap中的put()方法，把要添加进HashSet中的元素当做key存入，而value则是一个固定值：一个Object类对象。
先用hashCode()方法获得传入元素的哈希值，在集合中查找是否包含哈希值相同的元素，如果相同，则继续进行比较它们地址值，一般地址值都是不相同的，所以最后会用equals()方法比较对象内的属性值。
比较结果全为false就存入，如果比较结果有true则不存.

