# docker 部署

docker run --name pgsql -p 5433:5432 -e POSTGRES_PASSWORD=12345 -v /data/pgsqldata:/var/lib/postgresql/data -d postgres      
docker exec -it pgsql bash
psql -U postgres

# 常用的命令
不能同时访问两个数据库，但是可以通过schema 访问两个数据库
/l  查看库列表
/dt   查看表
/d  查看表结构
/dn 查看schema 

# 与 mysql 的区别
MySQL 移植过来应该用库名对应模式，保持库之间的互操作性

# 特有属性
表继承是查父表会有子表的数据，查子表没有父表的数据，多个父表同类型的字段会融合

分区使用表继承来实现
创建索引的时候，更新操作会阻塞，需要采用并发创建索引的方式  CREATE INDEX CONCURRENTLY

可以对函数支持索引，在数据插入或者更新的时候，会计算出结果，所以略影响更新速度，可以利用lower 函数索引实现大小写不敏感

可以创建序列，类似自增id，可以进行表间共享

# 查询优化

