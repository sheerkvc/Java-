##### Arrays:

```
public static String toString(x)
把数组拼接成一个字符串
public static int binarySearch（数组，查找的元素）
二分查找法查找元素
public static int[] copyOf（原数组，新数组长度）
拷贝数组
public static int[] copyofRange（原数组，起始索引，结束索引）
拷贝数组（指定范围）
public static void fill（数组，元素）
填充数组
public static void sort(数组)
按照默认方式进行数组排序


public static void sort（数组，排序规则）
按照指定的规则排序
原理）：
利用插入排序 +二分查找的方式进行排序的。
默认把e索引的数据当做是有序的序列，1索引到最后认为是无序的序列。
遍历无序的序列得到里面的每一个元素，假设当前遍历得到的元素是A元素，把A往有序序列中进行插入，在捅入的时候，是利用二分查找确定A元素的插入点。
拿着A元素，跟插入点的元素进行比较，比较的规则就是compare方法的方法体
如果方法的返回值是负数，拿着A继续跟前面的数据进行比较
如果方法的返回值是正数，拿着A继续跟后面的数据进行比较
如果方法的返回值是0，也拿着A跟后面的数据进行比较，直到能确定A的最终位置为止
🌰↓
Arrays.sort(arr, new Comparator<?super?>() {
		@Override
		public int compare (Integer o1, Integer o2) {
		return XXX;
		｝
｝）;

XXX：o1 - o2:升序排列
o2-o1:降序排列
```

##### Lambda表达式：

```
(形参) -> {

}
```

> - Lambda表达式可以用来简化匿名内部类的书写
> - ﻿﻿Lambda表达式只能简化函数式接口的匿名内部类的写法
> - ﻿﻿函数式接口：
>    有且仅有一个抽象方法的接口叫做函数式接口，接口上方可以加@Functionallnterface注解

更省略规则：

> 1. ﻿﻿参数类型可以省略不写。
> 2. ﻿﻿如果只有一个参数，参数类型可以省略，同时（）也可以省略。
> 3. ﻿﻿如果Lambda表达式的方法体只有一行，大括号，分号，return可以省略不写，需要同时省略

```
形参 -> 单行语句;
(para1，para2) -> 单行语句;
```

------

##### Collections:

```
public static < T > boolean addAll（Collection< T > c，T... elements） 批量添加元素

public static void shuffle(List‹? > list) 打乱List集合元素的顺序
```

<img src="https://picgo172.oss-cn-qingdao.aliyuncs.com/img/image-20240120155558284.png" alt="image-20240120155558284" style="zoom:30%;" />
