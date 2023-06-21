|                             命令                             |               描述               |
| :----------------------------------------------------------: | :------------------------------: |
|                       show databases；                       |       显示当前所有的数据库       |
|                     use < database name>                     | 选择要在其上执行其他操作的数据库 |
|                         show tables;                         |     显示数据库中所有表的列表     |
|              create database < database name>;               |         创建一个新数据库         |
| create table < table name> (column1 datatype1, column2 datatype2, ...); |           创建一个新表           |
| insert into < table name> (column1, column2, ...) values (value1, value2, ...); |          向表中插入数据          |
| update < table name> set column1 = value1, column2 = value2 where some_column = some_value; |          更新表中的数据          |
|  delete from < table name> where some_column = some_value;   |          从表中删除数据          |
|                     desc < table name>;                      |            显示表结构            |
|                         show errors;                         |        显示最近的错误消息        |
|                            exit;                             |         退出 MySQL 程序          |



```javascript
net start MySQL57
net stop MySQL57   停止mysql
mysql -h127.0.0.1 -P3306 -uroot -p123456 链接数据库
```

# MySQL的登录和退出

登录:  mysql -h localhost -u root -p

-h  mysql服务器ip
-P  mysql端口号
-u  用户名
-p  密码

退出

exit
quit
\q

## SQL语句分类

DDL(数据定义语言): create、drop、alter、truncate
DQL(数据查询语言): select、show
DML(数据操作语言): insert、update、delete

# 数据类型

## 整型

| **数据类型** | **说明**       | **取值范围**                                          |
| ------------ | -------------- | ----------------------------------------------------- |
| TINYINT      | 非常小的整数   | 带符号位：-128~127无符号位：0~255                     |
| SMALLINT     | 较小的整数     | 带符号位：-32768~32767无符号位：0~65535               |
| MEDIUMINT    | 中等大小的整数 | 带符号位：-8388608~8388607无符号位：0-16777215        |
| INT          | 标准整数       | 带符号位：-2147483648~2147483647无符号位：0~429467295 |
| BIGINT       | 大整数         | 带符号位：-2^63~2^63-1无符号位：0~2^64-1              |

注意：
	int(10) unsigned  zerofill  //最大10位数字的无符号整数 

## 浮点型

| **数据类型** | **存储空间** | **说明**     | **取值范围**                                               |
| ------------ | ------------ | ------------ | ---------------------------------------------------------- |
| FLOAT        | 4或8字节     | 单精度浮点型 | 最小非零值：+-1.175494351E-38最打非零值：+-3.402823466E+38 |
| DOUBLE       | 8字节        | 双精度浮点型 | 最小非零值：+-2.225073E-308最打非零值：+-1.797693E+308     |

注意：
float[(总位数,小数点后位数)]           最大精确到小数点后7位
double[(总位数,小数点后位数)]       最大精确到小数点后15位
超过限定长度将进行四舍五入计算



## 字符型

| **数据类型** | **存储空间** | **说明**   | **取值范围** |
| ------------ | ------------ | ---------- | ------------ |
| CHAR[(M)]    | M字节        | 定长字符串 | M字节        |
| VARCHAR[(M)] | L+1字节      | 可变字符串 | M字节        |
| TEXT         | L+2字节      | 小文本串   | 2^16-1       |
| MEDIUMTEXT   | L+3字节      | 中等文本串 | 2^24-1       |
| LONGTEXT     | L+4字节      | 大文本串   | 2^32-1       |

## 日期型

| **数据类型** | **存储空间** | **说明**                         | **取值范围**                    |
| ------------ | ------------ | -------------------------------- | ------------------------------- |
| YEAR         | 1字节        | “YYYY”格式的年份                 | 1901~2155                       |
| TIME         | 3字节        | “hh-mm-ss”格式表示的时间值       | -835:59:59~835:59:59            |
| DATE         | 3字节        | “YYYY-MM-DD”格式表示的日期       | 1000-01-01~9999-12-31           |
| DATETIME     | 8字节        | “YYYY-MM-DD hh:mm:ss”格式        | 1000-01-01 00:00:00~9999-12-31  |
| TIMESTAMP    | 4字节        | “YYYYMMDDhhmmss”格式表示的时间戳 | 19700101000000~2037年的某个时刻 |

注意
实际开发当中，存储日期时，我们一般使用整型来存储时间戳，这样做便于我们进行日期的计算

## MySQL数据类型注意事项

注意：
CHAR是固定长度字符，VARCAHR是可变长度字符串。
在使用CHAR和VARCHAR类型时，当我们传入的实际的值的长度大于指定的长度，字符串会被截取至指定长度
在使用CHAR类型时，如果我们传入的值的长度小于指定长度，实际长度会使用空格补至指定长度
在使用VARCHAR类型时，如果我们传入的值的长度小于指定长度，实际长度即为传入字符串的长度，不会使用空格填补
CHAR要比VARCHAR效率更高，但占用空间较大
BLOB主要存储图片、音频信息等，而TEXT只能存储纯文本文件。





## 命令

```mysql
 -- show DATABASES;查看数据库
-- create DATABASE IF NOT EXISTS nice DEFAULT charset utf8; 创建数据库
-- SHOW CREATE DATABASE nice; 查看创建数据库的信息
-- DROP DATABASE ok1;删除数据库 

show tables  查看当前数据下有哪些数据表

创建表
CREATE TABLE students (
	name VARCHAR(50),
	age INT(3),
	sex INT(1)
);

查看表结构
	desc 表名

-- SELECT * from teacher; * 找所有列数   查
-- SELECT name,age from teacher; 找两列  查

-- INSERT INTO teacher (name,age) VALUES("小高02",33); 插入一条数据
-- INSERT  teacher (name,age) VALUES("小高03",31);插入一条数据
-- INSERT INTO teacher (age,name) VALUES(52,"小高08");插入一条数据
INSERT INTO teacher (name,age) 
  VALUES("小高09",34),
("小高10",35),
 ("小高11",36),
 ("小高12",33),
 ("小高13",30);
-- INSERT INTO teacher (name,age) VALUES("rose",34);

-- UPDATE teacher set name="小高老师" WHERE id=3; 修改一列 加条件
-- UPDATE teacher set name="小可";修改全部 不用加条件
-- UPDATE teacher set name="rose老师",hobby="玫瑰花" WHERE id=3;修改多列
-- UPDATE teacher SET name="abc";

-- DELETE FROM teacher WHERE id=100;删除一条数据

-- DELETE FROM teacher; 清表操作  delete 有记录

-- DELETE FROM teacher WHERE id in(111,112,113);


-- TRUNCATE TABLE teacher; 清表操作  TRUNCATE 没有记录


-- ---------------------------------------------------------------------

-- INSERT INTO goods (name,brand,carno,price) VALUES("辉腾","大众","豫A.9358120",1200000.00),
--   ("辉腾2","大众","豫A.988520",2200000.00),
--  ("辉腾3","大众","豫A.97510",200000.00),
--   ("辉腾4","大众","豫A.96180",1200000.00),
--   ("辉腾5","大众","豫A.95580",9200000.00);

-- UPDATE goods SET price=9.9,name="辉腾plus" WHERE id=11;


-- SELECT * from goods WHERE carno="豫A.98520";
-- SELECT * from goods WHERE price>9.9;

-- DELETE FROM goods WHERE price=9.9;
-- DELETE from goods; 有记录  清表
-- TRUNCATE TABLE goods;

-- SELECT * from goods;
-- SELECT name,price from goods;
-- SELECT name as "车名",price as "价格" from goods;  as是 别名
-- 找出 车名 和价格 大于50万

-- SELECT name,price from goods WHERE price>50; 

-- SELECT name,price from goods WHERE price IS NOT NULL;
-- SELECT * from goods WHERE name="宋" or brand="路虎";   or或者   and并且
--  SELECT * from goods WHERE  brand<>"路虎"; 不等于 !=  <>

-- SELECT * from goods WHERE  NOT brand="BYD"; 取反

-- SELECT DISTINCT brand from goods; 品牌   性别
-- 分页
-- SELECT * from goods LIMIT 2; 一个参数 要的条数


-- SELECT * from goods  LIMIT 2,2; 跳过2条数据 给我2条

-- 前端 页数 条数
-- SELECT * from goods  LIMIT 10; 第一页  10条数     1     10
-- SELECT * from goods  LIMIT 10,10; 第2页  10条数   2      10

-- SELECT * from goods  LIMIT 20,10; 第2页  10条数   3      10
-- （页数-1）*条数，条数 后端写

-- SELECT * from goods  LIMIT 30,10;

-- SELECT * FROM goods ORDER BY price; 默认升序排列
-- SELECT * FROM goods ORDER BY price ASC; asc升序
-- SELECT * FROM goods ORDER BY price ASC,id DESC; 价格升序 id 降序

-- SELECT * FROM goods  WHERE price<=100 ORDER BY price ASC,id DESC;

-- 字符串函数:
-- SELECT CONCAT("abc","mnc");拼接
-- SELECT LENGTH("12345");长度
-- SELECT UCASE("abc"); 转大写
-- SELECT lCASE("AMN");小写
-- SELECT LENGTH(LTRIM(" 888"));去除左边的空格

-- SELECT LENGTH(RTRIM("888 "));去除右边空格

-- SELECT LENGTH(TRIM("   888     "));去除左右空格

--  SELECT REPLACE("abcdeffm","f","k");替换 替换所有


-- 时间函数
-- SELECT NOW();年月日 时分秒
-- SELECT CURDATE();年月日
-- SELECT CURTIME(); 时分秒
-- SELECT UNIX_TIMESTAMP();1685090524 毫秒 1970年到现在

-- SELECT FROM_UNIXTIME(1685090524);年月日 时分秒

-- 数学函数
-- SELECT ABS(-100); 绝对值
-- SELECT CEIL(10.1); 向上取整数
-- SELECT FLOOR(10.8); 向下取整数
-- SELECT ROUND(10.9); 四舍五入
-- SELECT RAND(); 0~1之间随机数
-- SELECT MOD(5,2);  5%2 取余数 取模

-- SELECT DATABASE();当前数据库
-- SELECT USER();用户
-- SELECT VERSION();版本号
-- SELECT LAST_INSERT_ID();

--  SELECT LAST_INSERT_ID();查询插入最后一条数据的 主键 id
```

# 数据完整性

## 主键约束

[primary] key       
每张表只能存在一个主键
主键必须保证记录的唯一性
主键自动为not null
主键不必与自增长约束同时存在

语法 :
列名 数据类型 PRIMARY KEY [默认值]

## 自增长约束

auto_increment

一个表中只能有一个字段使用AUTO_INCREMENT
必须与主键组合使用
默认情况下，起始值为1，增量为1
更改AUTO_INCREMENT初始值:
ALTER TABLE 表名称 AUTO_INCREMENT=1
语法:
列名 数据类型 AUTO_INCREMENT PRIMARY KEY

##  非空约束

null | not null     
空约束，字段值允许为null
非空约束，字段值不允许为null，必须赋值
语法 :
字段名 数据类型 not null

## 默认约束

default     
默认约束，当插入记录时，如果没有明确为字段赋值，则自动赋予默认值
语法
字段名 数据类型 default 默认值
注意
默认值只能约束一个列，不能在多个列上做约束，不能用于AUTO_INCREMENT列、TIMESTAMP列，如果对一个已经有数据的表添加默认约束，原来的数据不能得到默认值

## 唯一约束

unique [key]       
用来保证记录的唯一性 
唯一约束的字段可以为空值(null)
每张表中可以存在多个唯一约束
语法
字段名 数据类型 UNIQUE

## 外键约束

foreign key          
数据表的存储引擎只能为InnoDB
外键列和参照列必须具有相似的数据类型
参照列必须存在索引
语法
[CONSTRAINT 外键名] FOREIGN KEY 字段名1 [,字段名2,….]
REFERENCES 主表名 主键列1 [,主键列2,….]
CONSTRAINT student_teacher FOREIGN KEY student(t_id) REFERENCES teacher(id)





# node与MySQL链接

## 模糊查询

like  % 通配符  _占位

```mysql
-- SELECT * from goods WHERE brand LIKE "%小%";包含
-- SELECT * from goods WHERE brand LIKE "小%";开头
-- SELECT * from goods WHERE brand LIKE "%众"; 结尾
-- SELECT * from goods WHERE brand LIKE "小__"; _就是一个字符
-- SELECT * from goods WHERE brand LIKE "_小"; 两个字符 第二个字符小
-- SELECT * from goods WHERE brand LIKE "_小_"; 三个字符第二个字符小
-- SELECT * from goods WHERE brand LIKE "_小%";
-- SELECT * from goods WHERE carno LIKE "%9%" OR "%8%" OR "%5%";
-- SELECT * from goods WHERE carno LIKE "%985%"
-- SELECT name,brand from goods WHERE name="辉腾";
```

##  聚合函数 

```mysql
-- SELECT avg(price) as "价格" from goods;平均数
-- SELECT * from goods WHERE brand="路虎";
-- SELECT COUNT(*) from goods;所有
-- SELECT COUNT(price) from goods; 计数  null不计算

-- SELECT min(price) from goods; 最小

-- SELECT max(price) from goods;最大

-- SELECT SUM(price) from goods;求和
```

## 分组查询

```mysql
-- 查询不同班级的人数

-- SELECT classname,count(*) from student GROUP BY classname;
-- SELECT 后面的列名 必须出现在 GROUP BY 的后面，聚合函数除外

-- 统计不同班级 男生和女生各多少人
-- SELECT classname,sex,count(*) from student GROUP BY classname,sex;
-- sELECT 后面的列名 必须出现在 GROUP BY 的后面，聚合函数除外

-- 班级的性别
-- SELECT classname,sex from student GROUP BY  classname,sex;
-- sELECT 后面的列名 必须出现在 GROUP BY 的后面，聚合函数除外

-- 查询出每个班级中学生年龄的最小年龄，其结果按照升序排列 
-- SELECT classname,min(age) from student GROUP BY classname ORDER BY min(age) DESC ;

-- sELECT 后面的列名 必须出现在 GROUP BY 的后面，聚合函数除外

Having子句筛选：having后面跟的是统计函数

-- SELECT classname,sex,count(*) from student GROUP BY classname,sex HAVING count(*)>3;

-- SELECT classname,sex,count(*) from student WHERE sex=0  GROUP BY classname,sex HAVING count(*)>3;
-- 
-- WHERE>GROUP BY> HAVING  执行顺序
```





































































