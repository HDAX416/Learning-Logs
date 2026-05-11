# Learning-Logs
--
学习日志
--

啊啊啊啊啊啊啊啊啊我真的是受不了了,原本想整理一下自docker学习以来的笔记，包括糖宝和gemini大人的，以防对话达到长度限制。
还有回顾一下遇到过的错误，学过的命令，之前在vim里写过笔记，但不知道是不是我没保存，全部不见了，后面又重新写，还是不见了。
我tm服了，所以现在来写这个markdown，我在OneNote里也记过，不过总觉得还是提交到仓库里更有意义，所以现在来写这个markdown
希望今天能搞完吧。
```bash
docker-compose up -d
docker-compose down
docker exec -it my-monitor /bin/bash
ping java-service
docker logs -f my-monitor
docker ps -a
docker images
docker network ls
docker network rm net-monitor-zone
docker-compose ps
docker-compose logs -f
docker-compose up --build -d
docker-compose down -v
docker logs -f java-service
docker exec -it db mysql -u root -p123456
./mvnw clean package -DskipTests 
#查看端口占用
netstat -ano | findstr :3306  

SHOW DATABASES;
USE net_monitor;

Remove-Item -Recurse -Force .\mysql_data
```
我真的吐了，做gemini的监控系统，今天的任务是将数据加入MySQL中，最终效果是每个五秒钟容器内部会自动增加一条监控记录。
但不知道是任务结果本身和我想象的不一样，还是我操作的问题，最终只能够做到每次启动容器进入内部后手动INSERT一条就增加一条。
后来试试monitor.py能不能够正确拉取到java接口，结果不行，curl没用，后来看java-service的日志，tomcat有端口，但之后又退出了，
心累，我感觉ai都会累死了，把文件传给它，然后删除镜像，数据库数据，全部重新构建，但还是没有连接上，累累累累累，应该是到目前为止最累的一次了
感觉该系统性的学习这些东西了。加油吧，说起来下午倒是发呆了许久，感觉还挺有学习这些的欲望。

##
5.6 
重新复习，然后接着学习计划。早上很困，昨天真的累到了，趴在桌上回忆起高中时期的学习状态，学习习惯，如何让我更好记住学习过的东西，知识图谱，输出大于输入，多思考，多发呆。
梦言。压力上来了，心慌，但又觉得我是不是像之前一样把困难扩大化，解决之法就是直接去做，要系统学吗？在教室学习效率感觉很低，又提醒自己千万不能着急。简历怎么搞?运动？不管，先复习。
##
5.8
简历做完，现在开始复习技术栈。
```
mysql -h 127.0.0.1 -P 3307 -u root -p
docker exec -it monitor-db mysql -u root -p123456
CREATE DATABASE sql_practice;
USE sql_practice;
CREATE TABLE users (
    id INT AUTO_INCREMENT PRIMARY KEY,
    username VARCHAR(50) NOT NULL,
    email VARCHAR(100),
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
INSERT INTO users (username, email) VALUES
('alice', 'alice@example.com'),
('bob', 'bob@example.com'),
('charlie', NULL);
SELECT * FROM users;
SELECT username, email FROM users WHERE email IS NOT NULL;
UPDATE users SET email = 'charlie@example.com' WHERE username = 'charlie';
DELETE FROM users WHERE username = 'bob';

查询数据
-- 查询所有列
SELECT * FROM students;
-- 查询指定列
SELECT name, age FROM students;
-- 带条件查询
SELECT * FROM students WHERE age > 20;
-- 排序
SELECT * FROM students ORDER BY grade DESC;  -- 降序
-- 限制返回行数
SELECT * FROM students LIMIT 3;

插入数据
-- 插入完整一行
INSERT INTO students (id, name, age, grade)
VALUES (3, '王五', 22, 88);
-- 只插入部分列（其他列需允许 NULL 或有默认值）
INSERT INTO students (name, age) VALUES ('赵六', 19);

更新数据
-- 更新特定行的某一列
UPDATE students SET grade = 90 WHERE name = '张三';
-- 更新多列
UPDATE students SET age = 23, grade = 95 WHERE id = 2;

Attention:忘写WHERE会更新整张表

删除数据
-- 删除特定行
DELETE FROM students WHERE name = '赵六';
-- 删除所有行（保留表结构）
DELETE FROM students;

创建表
CREATE TABLE students (
    id INT PRIMARY KEY,          -- 整数，主键
    name VARCHAR(50) NOT NULL,   -- 可变长度字符串，最长50，不允许空
    age INT,
    grade DECIMAL(5,2)           -- 总位数5，小数2位，如 98.50
);

修改表结构
-- 添加列
ALTER TABLE students ADD email VARCHAR(100);
-- 删除列
ALTER TABLE students DROP COLUMN email;

删除表
DROP TABLE students;  -- 删除整个表及数据

WHERE name = '张三'
WHERE age <> 20 不等于
WHERE age BETWEEN 18 AND 22
WHERE grade >= 90
WHERE name LIKE '张%'（以张开头的名字）
WHERE id IN (1, 3, 5)
WHERE age>20 AND grade>80

聚合函数与分组
-- 计算平均分
SELECT AVG(grade) FROM students;
-- 分组统计每个年龄的平均分
SELECT age, AVG(grade) FROM students GROUP BY age;
-- 分组后过滤（HAVING 用于分组后条件）
SELECT age, AVG(grade) FROM students 
GROUP BY age 
HAVING AVG(grade) > 85;
```

##
5.11
MySQL结束，今天做完了知识图谱，从增删改查，对表操作，where子句，模糊化查询，到升降序，基本函数
交并差集，到子查询，表关联，索引，视图。需要记忆的还是挺多的。晚上开始Redis，明天搞完！
```
redis-server
redis-cli --raw
SET name hong
GET name
DEL name
EXISTS name
KEYS *
#慎用 FLUSHALL
TTL name
#设置生存时间
EXPIRE name 10
#设置键值对
SETEX name 4 hong
LPUSH letter a
LRANGE letter 0 -1
#索引从大到小，与数组相反
LPUSH letter b c d
RPUSH letter e
RPOP letter
LPOP letter 2
LLEN letter
RPOPLPUSH










```
