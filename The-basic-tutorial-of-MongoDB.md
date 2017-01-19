## MongoDB入门教程 ##

### 1.简介 ###
MongoDB 是一个介于关系数据库和非关系数据库之间的产品，是非关系数据库当中功能最丰富，最像关系数据库的。他支持的数据结构非常松散，是类似json的bson格式，因此可以存储比较复杂的数据类型。

### 2.安装与环境 ###
MongoDB可以在Windows、Linux、Mac OS X等主流平台运行，而且下载和安装非常简单，非常友好。
这篇文档的例子采用MongoDB 3.2.8版本，在windows 8.1测试过，有充足的理由相信，在其它平台也能顺利运行。

Windows的安装和设置可以参考官网：[Windows](https://docs.mongodb.com/manual/tutorial/install-mongodb-on-windows/)

在windows下启动mongodb,`cmd`取得管理员权限,启动mongodb服务`net start mongodb`,进入mongodb安装目录下bin文件夹，开发mongo.exe即可进入

Linux的安装和设置可以参考官网：[Linux](https://docs.mongodb.com/manual/administration/install-on-linux/)

Mac OS X安装和设置参考官网： [Mac OS X](https://docs.mongodb.com/manual/tutorial/install-mongodb-on-os-x/)

### 3.数据库与集合
* 创建/切换数据库 	`use database`
* 销毁数据库 		`db.dropDatabase()`
* 查看数据库 		`show dbs`
* 查看当前数据库对象 		`db`
* 创建集合		`db.creatCollection()`
* 查看集合		`show collections`
* 删除集合		`db.Name_collection.drop()`


### 4.文档的操作
对文档的增删查改是最基本的操作，接下来学习有关内容。  
* 插入文档  		`db.Name_collection.insert()`
* 保存文档		`db.Name_collection.save()` 
* 删除文档		``
* 更新文档
* 查询文档
* 条件操作



* 插入文档		`db.Name_collection.insert()`
插入数据时，如果集合没有创建会自动创建，如下自动创建users。 
##### example 
    >use mydb  
	switched to db mydb
	>db.users.insert([  
	...{   
	...name: "jam",  
	...email: "jam@qq.com"
	...},
	...{   
	...name: "Tom",  
	...email: "Tom@qq.com"
	...}  
	...])




* 保存文档		`db.Name_collection.save()`  
##### example
    >use mydb  
	switched to db mydb
	>db.users.save([  
	...{   
	...name: "jam",  
	...email: "jam@qq.com"
	...},
	...{   
	...name: "Tom",  
	...email: "Tom@qq.com"
	...}  
	...])

	> 注意save和insert的区别

* *查询文档*		`db.Name_collection.find()`  
`find()`方法以非结构化的方式来显示所有文档
如若更好的读取数据，可用`db.Name_collection.find().pretty()`
##### example
	>db.users.find().pretty()
	...{   
	...name: "jam",  
	...email: "jam@qq.com"
	...},
	...{   
	...name: "Tom",  
	...email: "Tom@qq.com"
	...}  
	...])




* 更新文档		`db.Name_collection.update()`   

在集合中users插入如下数据
##### example
	>userdoc1=({"user_id":1,
	"name":"cloud",
	"state":"active",
	"actor":"user",
	"e-mail":"test@qq.com",
	"VM_num":2,
	"time":[{"date":"2014-08-12","hour":"10:53 PM"}] 
	})  
	>userdoc2=({"user_id":2,
	"name":"testadmin",
	"state":"active",
	"actor":"admin",
	"e-mail":"test@qq.com",
	"VM_num":2,
	"time":[{"date":"2014-08-11","hour":"06:34 AM"}] })    
	> doc1=({"name":"peter","position":"teacher"})
	> db.users.insert(userdoc1)
	> db.users.insert(userdoc2)
	> db.users.insert(doc1)
更新文档users中user_id=2的文档的e-mail为group@qq.com

	>db.users.update({"user_id":"02","email":"test@qq.com"},
	{$set:{"e-mail":"group@qq.com"}})  



* 删除文档`db.Name_collection.remove()`  
删除name为cloud的文档：  
##### example
	/>db.users.remove({"name":"cloud"})  
	WriteResult({"nRemoved" : 1})  
	/>db.users.find() # 查询操作
	

	
* 条件操作符
在MongoDB中条件操作符有
<table>
    <tr>
        <th>></th>
        <th><</th>
        <th>>=</th>
        <th><=</th>
    </tr>
    <tr>
        <td>$gt</td>
        <td>$lt</td>
        <td>$gte</td>
        <td>$lte</td>
    </tr>
</table>





	


