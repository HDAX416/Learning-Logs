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

--
5.6 
重新复习，然后接着学习计划。早上很困，昨天真的累到了，趴在桌上回忆起高中时期的学习状态，学习习惯，如何让我更好记住学习过的东西，知识图谱，输出大于输入，多思考，多发呆。
梦言。压力上来了，心慌，但又觉得我是不是像之前一样把困难扩大化，解决之法就是直接去做，要系统学吗？在教室学习效率感觉很低，又提醒自己千万不能着急。简历怎么搞?运动？不管，先复习。
