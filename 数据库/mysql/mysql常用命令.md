```mysql
show tables;
show databases;
use xf_live;
#连上数据库
mysql -h 10.11.65.15 -uroot -p'7#8Zk&r!Y%v7N*&N';
#显示表字段
desc users;
#删除外键
alter table 表名  drop foreign key 外键名字
#删除列
alter table `rooms` drop column `identity`
```

