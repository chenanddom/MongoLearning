# zip包安装mongodb服务
1. 创建data目录，存放数据和日志文件
![创建data目录存放数据和日志](files/mongo-data-directory.png)
2. 添加mongodb的配置文件
![添加mongodb的配置文件](files/mongo-config-file.png)
文件内容如下:
```text
# 数据库路径
dbpath=D:\Develop\Mongo\mongo-data\mongodb-win32-x86_64-windows-5.0.2\data\db
# 日志输出文件路径
logpath=D:\Develop\Mongo\mongo-data\mongodb-win32-x86_64-windows-5.0.2\data\log\mongo.log
# 错误日志采用追加模式
logappend=true
# 启用日志文件(默认启用)
journal=true
# 这个选项可以过滤掉一些无用的日志信息，若需要调试使用请设置为false
quiet=true
# 端口号(默认为27017)
port=27017
```
3. 注册服务
mongod --config D:\Develop\Mongo\mongo-data\mongodb-win32-x86_64-windows-5.0.2\mongo.config --install --serviceName "MongoDB"
![mongo注册服务](files/mongo-config-file.png)
![成功注册服务之后](files/mongo-after-register-server.png)

4. 创建超级管理员和所有数据库管理员
![创建超级管理员和所有数据库管理员](files/mongo-create-root-user.png)
![用户登录](files/mongo-login.png)
```text
Built-In Roles（内置角色）：
    1. 数据库用户角色：read、readWrite;
    2. 数据库管理角色：dbAdmin、dbOwner、userAdmin；
    3. 集群管理角色：clusterAdmin、clusterManager、clusterMonitor、hostManager；
    4. 备份恢复角色：backup、restore；
    5. 所有数据库角色：readAnyDatabase、readWriteAnyDatabase、userAdminAnyDatabase、dbAdminAnyDatabase
    6. 超级用户角色：root  
    // 这里还有几个角色间接或直接提供了系统超级用户的访问（dbOwner 、userAdmin、userAdminAnyDatabase）
    7. 内部角色：__system

具体角色的功能： 

Read：允许用户读取指定数据库
readWrite：允许用户读写指定数据库
dbAdmin：允许用户在指定数据库中执行管理函数，如索引创建、删除，查看统计或访问system.profile
userAdmin：允许用户向system.users集合写入，可以找指定数据库里创建、删除和管理用户
clusterAdmin：只在admin数据库中可用，赋予用户所有分片和复制集相关函数的管理权限。
readAnyDatabase：只在admin数据库中可用，赋予用户所有数据库的读权限
readWriteAnyDatabase：只在admin数据库中可用，赋予用户所有数据库的读写权限
userAdminAnyDatabase：只在admin数据库中可用，赋予用户所有数据库的userAdmin权限
dbAdminAnyDatabase：只在admin数据库中可用，赋予用户所有数据库的dbAdmin权限。
root：只在admin数据库中可用。超级账号，超级权限
```