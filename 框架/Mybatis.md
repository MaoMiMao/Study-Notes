# Mybatis

## 作用域(scope)和生命周期

* SqlSessionFactoryBuilder
* SqlSessionFactory
* SqlSession

## XML映射文件

``` text
SQL映射文件顶级元素9个(其中paramterMap已经被废弃)
cache – 对给定命名空间的缓存配置。
cache-ref – 对其他命名空间缓存配置的引用。
resultMap – 是最复杂也是最强大的元素，用来描述如何从数据库结果集中来加载对象。
sql – 可被其他语句引用的可重用语句块。
insert – 映射插入语句
update – 映射更新语句
delete – 映射删除语句
select – 映射查询语句
```

### 标签属性

* select
* insert、update、delete
* sql
  * 这个元素可以被用来定义可重用的 SQL 代码段，这些 SQL 代码可以被包含在其他语句中。它可以（在加载的时候）被静态地设置参数。属性值也可以被用在 include 元素的 refid 属性里或 include 元素的内部语句中
* 参数
  * #{property,javaType=int,jdbcType=NUMERIC,typeHandler=MyTypeHandler
  ,numericScale=2,javaType=ResultSet, resultMap=departmentResultMap}
  * 字符串替换 默认情况下,使用 #{} 格式的语法会导致 MyBatis 创建 PreparedStatement 参数占位符并安全地设置参数（就像使用 ? 一样）。 这样做更安全，更迅速，通常也是首选做法，不过有时你就是想直接在 SQL 语句中插入一个不转义的字符串 例如 ORDER BY ${columnName}
* 结果映射
  * 简单的语句根本不需要配置显式的结果映射，而对于复杂一点的语句只需要描述它们的关系就行了。`<id>`和`<result>`区别: 都用将一个列的值映射到一个简单数据类型 id表示的结果是对象的标识属性
  * 构造方法 `<constructor>`
  * 简单结果 `<result>`
  * 关联 `<association>` 有一个关联
  * 集合 `<collection>` 多个关联
  * 鉴别器 `<discriminator>` 一个鉴别器的定义需要指定 column 和 javaType 属性。column 指定了 MyBatis 查询被比较值的地方。 而 javaType 用来确保使用正确的相等测试（虽然很多情况下字符串的相等测试都可以工作）
  * 自动映射 `mapUnderscoreToCamelCase`配置javaBean命名与数据库命名的区别
  映射等级: NONE-手动映射 PARTIAL-对除在内部定义了嵌套结果映射（也就是连接的属性）以外的属性进行映射 FULL-自动映射所有属性
* 缓存 默认会话缓存 
  * `<cache eviction="FIFO" flushInterval="60000" size="512" readOnly="true"/>`启用二级缓存映射
    * 语句文件中的所有 select 语句的结果将会被缓存。
    * 映射语句文件中的所有 insert、update 和 delete 语句会刷新缓存。
    * 缓存会使用最近最少使用算法（LRU, Least Recently Used）算法来清除不需要的缓存。
    * 缓存不会定时进行刷新（也就是说，没有刷新间隔）。
    * 缓存会保存列表或对象（无论查询方法返回哪种）的 1024 个引用。
    * 缓存会被视为读/写缓存，这意味着获取到的对象并不是共享的，可以安全地被调用者修改，而不干扰其他调用者或线程所做的潜在修改。

## 动态SQL

* if
* choose (when, otherwise)
* trim (where, set)
* foreach