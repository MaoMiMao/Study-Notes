# 基础
## 基本概念

* 数据库
* 表/模式
* 列/数据类型
* 行
* 子句 子句由关键字和给的数据组成
## 数据操作
### 数据插入
* insert
* insert select 
* select into --mysql不支持
### 数据更新
* update
### 数据查询
* select
  * select column from table limit
### 数据删除
* delete

## 表操作
### 创建
* create table name ()
### 更新表
```sql
ALTER TABLE tablename
(
ADD|DROP column datatype [NULL|NOT NULL] [CONSTRAINTS], ADD|DROP column datatype [NULL|NOT NULL] [CONSTRAINTS],
...
);
```
### 删除表
* drop table
### 重命名
* rename table(mysql)

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

## 组合查询
* union 两条以上/每个查询必须包含相同的列/列数据类型必须兼容
* union 自动合并相同的行 /不合并使用union all

## 视图
* create view tablename as 语句

## 存储过程

```sql
CREATE
    [DEFINER = { user | CURRENT_USER }]
　PROCEDURE sp_name ([proc_parameter[,...]])
    [characteristic ...] routine_body
 
proc_parameter:
    [ IN | OUT | INOUT ] param_name type
 
characteristic:
    COMMENT 'string'
  | LANGUAGE SQL
  | [NOT] DETERMINISTIC
  | { CONTAINS SQL | NO SQL | READS SQL DATA | MODIFIES SQL DATA }
  | SQL SECURITY { DEFINER | INVOKER }
 
routine_body:
　　Valid SQL routine statement
 
[begin_label:] BEGIN
　　[statement_list]
　　　　……
END [end_label]
```

## 事务处理
用来管理 insert/update/delete语句 
* 事务
* 回退
* 提交
* 保留点

## 游标

## 约束
* 主键
* 外键
* 唯一约束 
* 检查约束

##索引
* mysql
```sql
CREATE INDEX indexname ON tablename (column, ...);
```
##触发器
##数据库安全
## 区别
* 限制返回
  * oracle: ROWNUM 
  * DB2: FETCH FIRST 5 ROWS ONLY
  * mysql mariaDB pgsql sqllite: limit num offfset num 
* inner join和 natural join 
  * inner会显示所有列明 natural会去除重复列明且不能指定条件字段
* 唯一约束和主键
  * 唯一约束列多个 主键只有一个
  * 唯一约束列可以包含null值
  * 唯一约束列可以修改更新 重复使用
  * 唯一约束不能用来定义外键
  

## Null值
  Null的解释
  * 未知值(value unknown)
  * 不适用的值(value inapplicable)
  * 保留的值(vaue withheld)
