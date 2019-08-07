# 基础
## 基本概念

* 数据库
* 表/模式
* 列/数据类型
* 行
* 子句 子句由关键字和给的数据组成
## 数据操作

```txt

```

* insert
* update
* select
  * select column from table limit
* delete

## 表操作

## 关键字

* DISTINCT: 显示不同的值 列名之前 对所有的列都有效
* order by: 语句的最有一条子句 排序按照字段顺序(列的相对位置)排序 以字节码为依据排序
* DESC/ASC: 排序方向
* where 过滤条件 (<>不等于 !>不大于)

## 区别
* 限制返回
  * oracle: ROWNUM 
  * DB2: FETCH FIRST 5 ROWS ONLY
  * mysql mariaDB pgsql sqllite: limit num offfset num 

## Null值
  Null的解释
  * 未知值(value unknown)
  * 不适用的值(value inapplicable)
  * 保留的值(vaue withheld)
