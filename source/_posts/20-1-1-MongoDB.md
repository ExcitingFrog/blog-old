---
title: 20-1-1 MongoDB
date: 2020-01-01 09:05:37
tags:
- 2020
- MongoDB
- NoSql
---
### 简介
nosql指的是非关系型数据库，简单来说就是精简的数据库，去除掉很多不必要的功能，从而实现在性能上的提升。数据基于键值对，易于水平扩展。但却存在查询功能的有限性。
<!-- more-->
像是mongodb数据库，其数据的存储方式类似于json
![1.png](https://i.loli.net/2019/12/31/7CvwaD4yXSGbLUV.png)

### 基本语法
mongodb中database即是database，collection即是table。
linux环境下

#### 库的操作
> mongo #进入客户端<br>
show dbs #查看所有database<br>
db #显示当前库<br>
use test #使用test的库<br>
db.dropDatabase() #删除当前数据库，也可添加名字删除其中之一

#### 集合（表）的操作
> db.createCollection(name, options) #options是可选项，规定大小之类的内容<br>
> db.collectionname.drop() #删除某个集合<br>
> show collections #查看集合

#### 文档（数据）的操作
> db.collectionname.insert(doucument) #既可以直接插入json类型数据，也可以以变量插入<br>
> db.collectionname.find(query) #查询所有的数据操作，可以限定某一项或者多项，下面单列一个栏目<br>
> db.collectionname.remove(doucument) #单列其中一项就行

#### 查询语法
> db.collection.find(query, projection) #projection可选，使用投影操作符指定返回的键。查询时返回文档中所有键值， 只需省略该参数即可（默认省略）。<br>
> db.collectionname.find().pretty() #pretty让数据可读化<br>
> db.collectionname.find().limit() #限制查询数量，比如只要之前10个，skip()可以跳过数据<br>
> db.collectionname.find({'A':'xxx','B':'xx'}) #A and B 的查询<br>
> db.collectionname.find({$or:{'A':'xxx','B':'xx'}}) #A or B 的查询，and or 可以组合<br>
> db.collectionname.find({'A':{$gt:50}}) #查询A>50的数据，lt是<，lte是≤，gte是≥，ne是≠<br>
> db.collections.find().sort({'A':1}) #查询结果按A的正序排序，-1就是倒序，缺省1<br>
> db.collectionname.aggregate() #聚合查询，类似于group by，db.mycol.aggregate([{$group : {_id : "$user", num_tutorial : {$sum : 1}}}])  这里的_id，就是group by的某一项，num_tutorial就是显示的'num_tutorial':x ，$sum，表示每出现一次就加1。这个查询换成普通sql就是
select by_user, count(\*) from mycol group by by_user 。
当然也可以计算数据的总合，比如$sum:$A，就是查询每个user下A的总和。类似的还有avg，min，max等。

#### 更新语法
> db.collectionname.update(query,update,options) #这里的update可以直接设置{$set:{'A':'xxxx'}}，也可以进行一些操作，{$inc:{'A':1}}即为A更新为A+1。类似的还有$unst,$push,$pushAll等。options里的 1， upsert : 可选，这个参数的意思是，如果不存在update的记录，是否插入objNew,true为插入，默认是false，不插入。
2， multi : 可选，mongodb 默认是false,只更新找到的第一条记录，如果这个参数为true,就把按条件查出来多条记录全部更新。
3， writeConcern :可选，抛出异常的级别。<br>
> db.collection.save(doucument) #通过传入的文档来替换已有文档,记得要带'\_id':ObjectId('xxxx')

### 总结
这期把基本的内容写了下，下一期学点进阶的，nosql就算完了。

