##架构
###部署架构
* 一个master 多个regionserver:master负责维护表结构信息 实际数据存储在regionserver上 zookeeper负责管理HBase所有的RegionServer服务器
![图](../hbase/图片/部署架构.jpg)
###存储架构
* 基本单位列，每个列的不同版本值储存在单元格中，若干个列归类未一个列族，多个列构成行,行拥有唯一的行键，行键是决定row储存的唯一凭证
![图](../hbase/图片/存储架构.png)
