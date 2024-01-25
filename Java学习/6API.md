##### Math：

![image-20240116120300263](https://picgo172.oss-cn-qingdao.aliyuncs.com/img/image-20240116120300263.png)

floor相当于去掉小数，ceil相当于去掉小数自增1

Math.floor（Math.random（ ） * 100）相当于取1~100随机数

> 判断质数：
>
> 任意一个数都可以用（小于其平方根的1个数）*（大于其平方根的1个数）相乘得到
>
> 若为质数，因子只有1和本身，所以在1~其平方根内无第二个可以整除的数，即为质数。

**自幂数判断：**

> 一个n位自然数等于自身各个数位上数字的n次幂之和
>
> 如果自幂数是一位数，也叫做：独身数
>
> 三位自幂数：水仙花数。四位自幂数：四叶玫瑰数。五位自幂数：五角星数。六位自幂数：六合数
>
> 七位自幂数：北斗七星数。八位自幂数：八仙数。九位自幂数：九九重阳数。十位自幂数：十全十美数



<img src="https://picgo172.oss-cn-qingdao.aliyuncs.com/img/image-20240116123455479.png" alt="image-20240116123455479" style="zoom:50%;" />

##### System：

```
public static void exit(int status)    终止当前运行的 Java 虚拟机

public static long currentTimeMillis()    返回当前系统的时间毫秒值形式
//时间进制为1000，begin：19790.1.1 0:0:0

Public static void arraycopy（数据源数组，起始索引，目的地数组，起始索引，拷贝个数）数组拷贝
//数据类型须一致，若为引用类型，父类可给子类
```

##### Runtime：

```
public static Runtime getRuntime ()    当前系统的运行环境对象
public void exit (int status)          停止虚拟机
public int availableProcessors()       获得CPU的线程数
public long maxMemory()                JVM能从系统中获取总内存大小（单位byte）
public long totalMemory()              JVM已经从系统中获取总内存大小（单位byte）
public long freeMemory（）              JVM剩余内存大小（单位byte）

public Process exec (String command)   运行cmd命令
//shutdown -s:1分钟后关机
//shutdown -s -t 指定时间
//shutdown -a  取消
```

#####  Object：

```
public String tostring（） 返回对象的字符串表示形式
public boolean equals (Object obj) 比较两个对象是否相等

protected object clone (int a) 对象克隆

```

```
protected object clone (int a) 对象克隆

需要throws exception
需要重写clone方法在本类中调用
javabean需实现cloneable标记接口
```

##### Objects：

省去空指针判断

```
public static boolean equals (Object a, object b)   先做非空判断，比较两个对象
public static boolean isNull(object obj)   判断对象是否为nul1，为nu11返回true，反之
public static boolean nonNull(Object obj)   判断对象是否为nul1，跟isNu11的结果相反
```

##### BigInteger：（once create，can't change，static finnal）

```
public BigInteger (int num, Random rnd)   获取随机大整数，范围：［e ~ 2的num次方-1］
public BigInteger (String val)  获取指定的大整数（val必须为整数）
public BigInteger (String val, int radix)   获取指定进制的大整数//格式转换

public static BigInteger valueof(long val) 静态方法获取BigInteger的对象
//val为 long的范围
//对-16~16做了优化
```

```
方法
public BigInteger add(BigInteger val)   加法
public BigInteger subtract(BigInteger val)  减法
public BigInteger multiply(BigInteger val)  乘法
public BigInteger divide (BigInteger val)  除法，获取商
public BigInteger[] divideAndRemainder (BigInteger val)  除法，获取商和余数
public boolean equals （Object x）  比较是否相同
public BigInteger pow(int exponent)  次幂
public BigInteger max/min(BigInteger val)  返回较大值/较小值

public int intValue (BigInteger val)  转为int类型整数，超出范围数据有误
//double/longValue
```

**存储方式：**

> signum记录正负号
>
> 将数字转为2进制，从右往左32位一组换为10进制，储存在 int[] mag数组中。

##### BigDecimal：

```
public BigDecimal(double val)
//no recommend，不精确   0.9(decimal)——>......（binary）

public BigDecimal(String val)

public static BigDecimal valueOf(double val)
如果我们传递的是0~10之间的 整数 ，包含0，包含10，那么方法会返回己经创建好的对象，不会重新inew


1.如果要表示的数字不大，没有超出double的取值范围，建议使用静态方法
2.如果要表示的数字比较大，超出了double的取值范围，建议使用构造方法
```

```
public static BigDecimal valueOf(double val)获取对象
public BigDecimal add (BigDecimal val)加法
public BigDecimal subtract(BigDecimal val)减法
public BigDecimal multiply(BigDecimal val)乘法
public BigDecimal divide(BigDecimal val)除法
//除不尽报错
public BigDecimal divide（BigDecima1 val，精确几位，舍入模式[RoundingMode]）除法

//RoundingMode枚举类
RoundingMode.XXX 舍：入？
```

**存储方式：**

> new的时候，新建byte[]，将传入数字**各个位**按ASCII码表保存（包含符号和.位）

### ﻿﻿~~JDK7以前时间相关类~~

##### ~~Date   时间~~

##### ~~SimpleDateFormat    格式化、解析时间~~

~~<img src="https://picgo172.oss-cn-qingdao.aliyuncs.com/img/image-20240118125401496.png" alt="image-20240118125401496" style="zoom: 33%;" />~~

~~字母对应的东西api有，应该也不会看~~

##### ~~Calendar		日历~~

~~Set get方法~~

> ~~月份：范围0~11 如果取出来的是e.那么实际上是1月。~~
>
> 
>
> ~~星期：星期日是一周中的第一天~~
>
> ~~1（星期日）2（星期一）3（星期二）4（星期三）5（星期四）6（星期五）7（星期六）~~

~~Calendar c  = Calender.getInstance();~~

```
//public int get(int field) ·			取日期中的某个字段信息
//public void set(int field, int value)				修改日历的某个字段信息
//public void add(int field,int amount)			为某个字段增加/減少指定的值

field对应的是数组中的位置（0,1,2......），有常量表示
```

#### JDK8新增时间相关类

<img src="https://picgo172.oss-cn-qingdao.aliyuncs.com/img/image-20240118145503765.png" alt="image-20240118145503765" style="zoom: 33%;" />

##### ZoneId

```
static Set<String> getAvailableZoneIds()获取Java中支持的所有时区
static ZoneId systemDefault()获取系统默认时区
static Zoneld of(String zoneId)获取一个指定时区
```

##### Instant：(时间不可变，只会new)

<img src="https://picgo172.oss-cn-qingdao.aliyuncs.com/img/image-20240118150603481.png" alt="image-20240118150603481" style="zoom: 33%;" />

##### ZoneDateTime：

<img src="https://picgo172.oss-cn-qingdao.aliyuncs.com/img/image-20240118154854375.png" alt="image-20240118154854375" style="zoom: 33%;" />

##### LocalDate, LocalTime, LocalDateTime：

同上

##### Duration：用于计算两个“时间”间隔（秒，纳秒）

##### Period：用于计算两个“日期”间隔（年、月、日）

##### ChronoUnit ：用于计算两个“日期” 间隔			chronometry  计时法

