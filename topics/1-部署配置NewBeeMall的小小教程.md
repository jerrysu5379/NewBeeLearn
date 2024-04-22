# 1. 部署配置NewBeeMall的小小教程

## 1.1 需要什么
- JDK>=17
- Maven>=3.8.1
- Git>=2.33.0
- MySQL>=8.0.26
- Redis>=6.2.5
- RabbitMQ>=3.9.7

## 1.2 如何安装
### 我们基于Ubuntu 22.04的服务器环境，以下是安装步骤
- JDK: `sudo apt install openjdk-17-jdk`
- Maven: `sudo apt install maven`
- Git: `sudo apt install git`
- MySQL: `sudo apt install mysql-server`
- Redis: `sudo apt install redis-server`
- RabbitMQ: `sudo apt install rabbitmq-server`
- Git: `sudo apt install git`

## 1.3 如何配置
### 1.3.1 Clone项目
- `git clone -b spring-boot-3.x --single-branch https://github.com/newbee-ltd/newbee-mall.git`
- `cd newbee-mall`
### 1.3.2 配置MySQL
- 进入MySQL: `mysql -u root -p`
- 创建数据库: `create database newbee-mall-datasource;`
- 创建用户: `create user 'newbee'@'%' identified by 'Test123456';`
- 授权: `grant all privileges on newbee-mall-datasource.* to 'newbee'@'%';`
- 刷新: `flush privileges;`
- 退出: `exit;`
- 进入sql文件夹: `cd newbee-mall/src/main/resources`
- 导入数据: `mysql -u newbee_mall -p newbee_mall < newbee_mall.sql`
### 1.3.3 配置项目
- 修改配置文件: `vim application.properties`
- 将’spring.datasource.username‘和’spring.datasource.password‘改为’newbee‘和’Test123456‘（按 *i键* 进入插入模式）
- 按下’ESC‘键，输入’:wq‘保存并退出
- 输入'cd'返回主目录
- 输入‘cd newbee-mall’进入项目目录
- 打包项目: `mvn clean package -Dmaven.test.skip=true`
- 运行项目: `java -jar target/newbee-mall-1.0.0.jar`
- 访问: `http://localhost:28089`
- 如果成功进入页面，说明部署成功