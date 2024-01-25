| 单列集合     | default Stream< E > stream)                       | Collection中的默认方法   |
| ------------ | ------------------------------------------------- | ------------------------ |
| 双列集合     | 无                                                | 无法直接使用stream流     |
| 数组         | public static < T > Stream< T > stream(T[] array) | Arrays工具类中的静态方法 |
| 一堆零散数据 | public static< T > Stream< T > ofT... values)     | Stream接口中的静态方法   |

双列集合：

> 第一种获取stream流	//键组
>
> hm. keySet().stream().forEach(s -> System.out.println(s));
>
> 第二种获取stream流	//键值对组
>
> hm. entrySet()). stream()

数组：

> Arrays.stream(XXX数组)...........

一堆零散数据

> Stream.of(XXXXXXXXX)........
>
> 但是传入基本数据类型forEach会返回地址值
>
> 引用数据类型正常

```
过程方法：
Stream<T> filter (Predicate<?super T> predicate) 过滤
Stream<T> limit(long maxsize)  获取前几个元素
Stream<T> skip(long n)  跳过前几个元素
Stream<T> distinct)  元素去重，依赖（hashCode和equals方法）
static <T> Stream<T> concat(Stream a, Stream b)  合井a和b两个流为一个流
Stream<R> map(Function<T, R> mapper)  转换流中的数据类型
```

```
ArrayList<String> list = new ArrayList<>();
        Collections.addAll(list, "张无忌-15", "周芷若-14", "赵敏-13", "张强-20", 
        													"张三丰-100", "张翠山-40", "张良-35", "王二麻子-37", 
        													"谢广坤-41");
        //需求：只获取里面的年龄并进行打印
        //String->int

        //第一个类型：流中原本的数据类型
        //第二个类型：要转成之后的类型

        //apply的形参s：依次表示流里面的每一个数据
        //返回值：表示转换之后的数据

        //当map方法执行完毕之后，流上的数据就变成了整数
        //所以在下面forEach当中，s依次表示流里面的每一个数据，这个数据现在就是整数了
        list.stream().map(new Function<String, Integer>() {
            @Override
            public Integer apply(String s) {
                String[] arr = s.split("-");
                String ageString = arr[1];
                int age = Integer.parseInt(ageString);
                return age;
            }
        }).forEach(s-> System.out.println(s));

        System.out.println("------------------------");



//更快的方法
        list.stream()
                .map(s-> Integer.parseInt(s.split("-")[1]))
                .forEach(s-> System.out.println(s));



    }
}

```

```
终结方法：
void forEach（Consumer action）			遍历
long count()			统计
toArray()		收集流中的数据，放到数组中



toArray(IntFunction<A[]> generator)
list. stream(). toArray(value-> new String[value]);

//String[] arr = list. stream() .toArray(new IntFunction<String[]>(> {
																								@Override
                                                public String[] apply(int value) {
                                                return new String[value];
																								}
}

```

```
collect (Collector collector)			收集流中的数据，放到集合中
collect (Collector.toList/Map() )
```



collect收集到键值对map中

<img src="https://picgo172.oss-cn-qingdao.aliyuncs.com/img/image-20240124152712361.png" alt="image-20240124152712361" style="zoom:50%;" />

list不，set去重

<img src="https://picgo172.oss-cn-qingdao.aliyuncs.com/img/image-20240124141012613.png" alt="image-20240124141012613" style="zoom:50%;" />
