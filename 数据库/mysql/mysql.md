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
* 通配符 %-多个 _ -单个
* GROUP BY & HAVING  having过滤分组后数据

## 函数
### 字符串函数
  * TRIM/RTRIM/LTRIM 去除空格
### 日期函数
### 聚集函数
  * AVG() --忽略null值
  * COUNT() -- * 对行数目计数包含null值 --column 对特定的列技术 忽略null值
  * MAX() --忽略null值
  * MIN() --忽略null值
  * SUM() --忽略null值
  
## 子查询
* 子查询总是从内向外处理 作为子查询的select语句只能查询单个列
  
## 表连接
* 自联结(self-join)\自然连接(natural join)\外连接(outer join)
* 没有连接条件的表关系返回笛卡尔积(叉积)
*  

## 区别
* 限制返回
  * oracle: ROWNUM 
  * DB2: FETCH FIRST 5 ROWS ONLY
  * mysql mariaDB pgsql sqllite: limit num offfset num 
* inner join和 natural join 
  * inner会显示所有列明 natural会去除重复列明且不能指定条件字段
  
## Null值
  Null的解释
  * 未知值(value unknown)
  * 不适用的值(value inapplicable)
  * 保留的值(vaue withheld)
