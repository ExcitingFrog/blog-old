---
title: 20-1-4 MongoDB
date: 2020-01-04 19:04:24
tags:
- 2020
- MongoDB
- NoSql
---
### 远程服务
#### linux安装mongodb
首先配置在云服务器（centos）的yum源
[官网源](https://docs.mongodb.com/manual/tutorial/install-mongodb-on-red-hat/)

<!-- more-->

```js
[mongodb-org-4.2]
name=MongoDB Repository
baseurl=https://repo.mongodb.org/yum/redhat/$releasever/mongodb-org/4.2/x86_64/
gpgcheck=1
enabled=1
gpgkey=https://www.mongodb.org/static/pgp/server-4.2.asc
```
接着直接sudo yum install -y mongodb-org就行

接着开放端口，云服务器商提供者可能会提供图形化界面，直接设置就好。然后配置。
```js
#图形化操作忽略这个
systemctl status firewalld  # 查看防火墙状态
firewall-cmd --zone=public --add-port=27017/tcp --permanent # mongodb默认端口号
firewall-cmd --reload  # 重新加载防火墙
firewall-cmd --zone=public --query-port=27017/tcp # 查看端口号是否开放成功，输出yes开放成功，no则失败


或者
iptables -A INPUT -p tcp -m state --state NEW -m tcp --dport 27017 -j ACCEPT

```
```js
vim /etc/mongod.conf
# network interfaces
net:
  port: 27017
  bindIp: 0.0.0.0  # Enter 0.0.0.0,:: to bind to all IPv4 and IPv6 addresses or, alternatively, use the net.bindIpAll setting.
sudo service mongod restart #最后重启下服务
```
接着在比如自己的win电脑上连接，打开cmd或者powershell
> .\\mongo ipadress:port

#### 身份认证
> \>use test<br>
> \>db.createUser({ user:"admin", pwd:"123456", roles:["readWrite", "dbAdmin"] }) #roles里可以配置权限

接着配置文件里修改内容
```js
vi /etc/mongod.conf
security:
  authorization: "enabled"   # disable or enabled

sudo service mongod restart #最后重启下服务
```
接着就可以连接
```js
// 终端连接
mongo ipadress:port/database -u username -p password

// mongoose方式连接
mongoose.connect('mongodb://username:password@host:port/database?options...', {useNewUrlParser: true});

// 通过客户端连接

```

#### 分片
分片就是水平分布式扩展mongodb，这样能以低成本的方式提高性能。
这一部分没怎么尝试。
> [教程1](https://www.runoob.com/mongodb/mongodb-sharding.html)<br>
[教程2](https://www.jianshu.com/p/cb55bb333e2d)

### 备份
比如在自己的win电脑。按照普通安装方法，可能mongod会自动加入到系统服务
> win+r services.msc 找到mongo服务关闭

服务器端启动，并配置路径，配置内容也可以保存为一个文件，在命令中引用
>.\\mongod -dbpath c:\\software\\mongodb\\data

备份 h后是地址，本机就是localhost d后是数据库名字 o后是保存的地址
 > .\\mongodump -h 127.0.0.1 -d xingo -o C:\\software\\mongodb\\dump

恢复 可以选择参数是否删除之前的
> .\\mongorestore -h 127.0.0.1 -d xingo C:\\software\\mongodb\\dump\\xingo


### \_id
mongobd的文档会生成一个默认的ObjectID，记录时间等信息，表内数据按照其排序。
> var objid = ObjectId() #可以生成一个id

#### 引用
数据插入时可以引用其他数据
> db.collectionname.insert({'title':'a','content':ObjectId('xxxxxxxx')})<br>
> var rea = db.collectionname.findOne({'title':'a'})<br>
> db.collectionname.find({'\_id':{'$in':rea['content']}})


#### 索引
简单的说，索引就是将文档按照某个（或某些）字段顺序组织起来，以便能根据该字段高效的查询。<br>
mongodb按照默认的生成的_id查询，就会带来往往需要扫描全体，因此建立索引排序，在查找时就能快速查询。
>  db.collectionname.createIndex( {age: 1} ) #建立age正序排序 <br>
db.collectionname.createIndex( {name: 1, age: 1} ) #复合索引<br>
> db.collectionname.getIndexes() #查看索引<br>
> db.collectionname.dropIndex("") #删除索引

