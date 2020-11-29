# mysql数据迁移

## 步骤

1. 数据库备份
2. 清理账数据
3. 字段不一致处理
4. 插入数据时uid生成
5. 存储过程写法
6. 跨数据库执行sql

## 遇到的问题
1. mysql定义变量 
   DECLARE total INT DEFAULT 6; //定义存储过程变量只能在存储过程中用
   set @var = 1; //用户变量，作用域是整个会话

2. 内连接

   select user.id,nickname,name,avatar from user inner join app_user on user.id = app_user.uid;

3. Sql跨数据库
   在同一个连接下面用 UserCenter1.user用数据库名点表名
    select * from UserCenter1.`user`

4. 存储过程

5. 游标遍历

6. 视图

7. 特殊字符问题

   ```mysql
   show character SET;
   ```

   Charset  Description                Default collation. Maxlen

   big5	Big5 Traditional Chinese	big5_chinese_ci	2
   dec8	DEC West European	dec8_swedish_ci	1
   cp850	DOS West European	cp850_general_ci	1
   hp8	HP West European	hp8_english_ci	1
   koi8r	KOI8-R Relcom Russian	koi8r_general_ci	1

   ```
   show VARIABLES like '%character%';
   ```

   Variable_name    Value

   character_set_client	utf8mb4
   character_set_connection	utf8mb4

8. 保留关键字

   ```
   uid,email,avatar 这些不能用来定义变量
   ```
   
9. mysql if语句只能在存储过程或函数中用，set定义变量不能在函数中用

   
## 示例

- 存在就删除

  `DROP PROCEDURE IF EXISTS processData; `

- 打印

  `select 123; `

- 赋值

  ```mysql
  set @ab = 12;
  select 123 into @ab;
  ```

- 游标使用

  ```mysql
  DROP PROCEDURE IF EXISTS processData;
  CREATE PROCEDURE processData()
  BEGIN
  	DECLARE o INT DEFAULT 0;
  	DECLARE done INT DEFAULT 0;
  	DECLARE cur CURSOR FOR select id from `user`;
  	declare continue HANDLER for not found set done = true;
  	
  	OPEN cur;
  	read_loop:loop
  		fetch cur into o;
  		if done then
  			leave read_loop;   
  		end if;
  		
  	end loop;
  	CLOSE cur;
  	select o;
  END;
  CALL processData();
  ```

- 显示表创建SQL

  `show create table user`

- 存储过程

```mysql
 DROP PROCEDURE IF EXISTS processLiveAppData;
 CREATE PROCEDURE processLiveAppData()
 BEGIN
 
 	DECLARE live_app_id BIGINT(20) DEFAULT null;
 	DECLARE app_signature VARCHAR(100) DEFAULT null;
 	DECLARE create_time BIGINT(20) DEFAULT null;
	DECLARE publish_url VARCHAR(200) DEFAULT null;
 	DECLARE play_url VARCHAR(200) DEFAULT null;
 	DECLARE app_type INT DEFAULT 0;

 	DECLARE done INT DEFAULT 0;
 	DECLARE cur CURSOR FOR (select app_id,app_signature,create_timestamp,cdn_publish_url,cdn_play_url from live_app);
 	
 	declare continue HANDLER for not found set done = true;
 
 	OPEN cur;
 	-- 循环游标
 	read_loop:loop
 		fetch cur into live_app_id,app_signature,create_time,publish_url,play_url;
 		if done then
 			leave read_loop;
 		end if;
		
		if publish_url!=null or play_url!=null THEN
				INSERT into UserCenter1.live_app_extra_info(id,live_app_id,app_type,publish_url,play_url,create_time,update_time) values(id,live_app_id,app_type,publish_url,play_url,create_time,create_time);
		end if;
		
 		INSERT into UserCenter1.live_app(live_app_id,app_signature,create_time,update_time) values(live_app_id,app_signature,create_time,create_time);
 		INSERT into UserCenter1.roles(live_app_id,title,description,create_time,update_time) values(live_app_id,'Admin','管理员',create_time,create_time);
 		INSERT into UserCenter1.roles(live_app_id,title,description,create_time,update_time) values(live_app_id,'Anchor','主播',create_time,create_time);
 		INSERT into UserCenter1.roles(live_app_id,title,description,create_time,update_time) values(live_app_id,'Tourist','游客',create_time,create_time);
 	end loop;
 	CLOSE cur;
 	
 END ;

 call processLiveAppData();
```

# 参考

[mysql官方文档](https://dev.mysql.com/doc/refman/8.0/en/if.html)



