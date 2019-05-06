#### RDD创建方式

- 读取外部数据集
- 对已经存在的集合并行化 parallelize

####  传递函数

- 标准函数接口 

  >  Function<T,R>  R call(T)	 接受一个输入 返回一个输出
  >
  >  Function<T1,T2,R>  R call（T1,T2） 接受两个输入 返回一个输出
  >
  >  FlatMapFunction< T,R >  Iterable< R >  call(T)  接受一个输入 返回任意个输出

#### 转换操作(Basic)

>  - 单个
>
>    map()、flatmap()、filter()、distinct()、sample(withReplacement,fraction,[seed])
>
>  - 两个
>
>    union()、
>
>    intersection()--求共同、
>
>    subtract()--移除一个rdd内容、
>
>    cartesian()--笛卡儿积


#### 行动操作(Basic)

> collect()、count()、countByValue()--各元素出现次数、
>
> take(num)--从Rdd中返回num个元素、
>
> top(num)--返回最前面num个元素、
>
> takeOrdered(num)(ordering)--按照ordering返回最前面num个元素
>
> takeSample(withReplacement，num，[seed] ) --从Rdd中返回任意一些元素、
>
> reduce(func)--整合数据
>
> fold(zero)(func)--同reduce但是先提供初值、
>
> aggregate(zero)(seqOp,combOp)、foreach(func)--递归使用函数

### 特殊类型RDD转换(key-value)

>函数接口
>
>| 函数名                     | 等价函数                          | 作用                               |
>| -------------------------- | --------------------------------- | :--------------------------------- |
>| DoubleFlatMapFunction<T>   | Function<T, Iterable<Double>>     | 用于flatMapToDouble,生成DoubleRDD  |
>| DoubleFunction<T>          | Function<T ,Double>               | 用于MapToDouble,生成DoubleRDD      |
>| PairFlatMapFunction<T,K,V> | Function<T,Iterable<Tuple2<K,V>>> | 用于flatMapToPair,生成PairRDD<K,V> |
>| PairFunction<T,K,V>        | Function<T,Tuple<K,V>>            | 用于mapTopair,以生成PairRDD<K,V>   |

### 持久化(缓存)

由于RDD惰性求值，避免重复计算写入缓存。主要实现方法persist(),unpersist(),cache()

>Scala&Java默认序列化到JVM的堆空间中
>
>| 级别                                  | 使用空间 | CPU时间 | 是否在内存中 | 是否在磁盘上 | 备注                                                |
>| ------------------------------------- | -------- | ------- | ------------ | ------------ | --------------------------------------------------- |
>| MEMORY_ONLY                           | 高       | 低      | 是           | 否           |                                                     |
>| MEMORY_ONLY_SER                       | 低       | 高      | 是           | 否           |                                                     |
>| MEMORY_AND_DISK                       | 高       | 中等    | 部分         | 部分         | 超过内存部分溢写到磁盘                              |
>| MEMORY_AND_DISK_SER                   | 低       | 高      | 部分         | 部分         | 超过内存部分溢写到磁盘。内存中数据为序列化后的数据D |
>| DISK_ONLY                             | 低       | 高      | 否           | 是           |                                                     |
>| MEMORY_ONLY_2, MEMORY_AND_DISK_SER_2. |          |         |              |              | 保存到另外集群上                                    |

### PairRDD的转化操作

> 除了标准的RDD操作外
>
> - 单个
>
> | 函数名                                                       | 目的                                                         | 实例                        |
> | ------------------------------------------------------------ | ------------------------------------------------------------ | :-------------------------- |
> | reduceByKey(func)                                            | 合并具有相同键的值                                           | rdd.reduceByKey((x,y)->x+y) |
> | groupByKey()                                                 | 对具有相同键的值进行分组                                     | rdd.groupByKey()            |
> | combineByKey(createCombiner ,mergeValue,MergeCombiners,parttitioner) | 使用不同返回类型合并具有相同键的值                           |                             |
> | mapValues(func)                                              | 对pair RDD中的每个值应用一个函数而不改变键                   | rdd.mapValues(x->x+1)       |
> | flatMapValues(func)                                          | 对pairRDD中的每个值应用一个返回迭代器函数，然后对返回的每个元素都生成一个对应原键的键值对记录。通常用于符号化 |                             |
> | keys()                                                       | 返回一个仅包含键的RDD                                        |                             |
> | values()                                                     | 返回一个仅包含值的RDD                                        |                             |
> | sortByKey()                                                  | 返回一个根据键排序的RDD                                      |                             |
>
> - 两个
>
> | 函数名                   | 目的                                   | 示例 |      |
> | ------------------------ | -------------------------------------- | ---- | ---- |
> | subtractByKey(other)[^1] | 删除RDD中键与other RDD中的键相同的元素 |      |      |
> | join(other)[^2]          | 对两个RDD进行内链接                    |      |      |
> | rightOutJoin(other)      | 右外链接                               |      |      |
> | leftOutJoin(other)       | 左外链接                               |      |      |
> | cogroup                  | 将两个RDD中拥有相同键的数据分组到一起  |      |      |
>
> [^1]: Scala中没有括号
> [^2]: Scala中没有括号

