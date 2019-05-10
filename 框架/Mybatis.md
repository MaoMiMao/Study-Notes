# Mybatis

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
