##  equals与hashcode

### java八大基本数据类型

byte 1

short char 2

int float 4

double long 8

boolean 1

### equals 和 ==

equals是判断两个变量或者实例指向同一个内存空间的值是不是相同

而==是判断两个变量或者实例是不是指向同一个内存空间

**总结**

==对于基本类型是值比较，对于引用类型比较的是引用

equals默认情况下是引用比较，String、Integer等重写方法改为了值比较

### 覆盖equals方法遵守的约定

**自反性**
对于任意非null的引用值x，x.equals(x)必须返回true。

**对称性**
对于任意非null的引用值x、y，当且仅当y.equals(x)返回true时，x.equals(y)必须返回true。

**一致性**
对于任意非null的引用值x、y，只要equals方法的比较操作在对象中所用的信息没有发生改变，那么多次调用x.equals(y)应该一致的返回true或false。

**传递性**
对于任意非null的引用值x、y、z，如果x.equals(y)返回true，并且y.equals(z)返回true，那么x.equals(z)必须返回true。

对于任意非null的引用值x，x.equals(null)必须返回false。


### equals与hashcode的关系

equals()相等的两个对象，hashcode()一定相等；

equals()不相等的两个对象，hashcode()有可能相等。

hashcode()不等，一定能推出equals()也不等；

hashcode()相等，equals()可能相等，也可能不等。

### 为什么要使用hashcode

~~~java
var s = "OK";
var t = new String("OK");
var sb = new StringBuilder(s);
var tb = new StringBuilder(t);
~~~

s与t hashcode相同

sb与tb hashcode不同

字符串散列码由内容导出，但是StringBuilder类没有定义hashcode方法，默认hashcode从对象存储地址得出。

hashCode()效率是比equals()效率高的。所以HashSet判断元素是否相等时先用hashCode()判断，如果hashCode()不同，则对象不等，如果hashCode()相同，再比较equals() ，大大提高了效率。

如果重写了equals()，必须重写hashCode()。
