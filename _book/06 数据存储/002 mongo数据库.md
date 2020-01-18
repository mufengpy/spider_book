[TOC]

## <font color="#0099CC">为什么使用Mongo</font>

性能较高，方便（不需要先定义表）

当然也可以使用其它存储方式，如Mysql，文件

## <font color="#0099CC">官网</font>

mongo

​	https://www.mongodb.com/

pymongo

​	https://api.mongodb.com/python/current/

## <font color="#0099CC">安装Mongo</font>

https://www.cnblogs.com/jpfss/p/11247703.html

## <font color="#0099CC">可视化工具</font>
robomongo
https://robomongo.org/download

## <font color="#0099CC">Python操作Mongo</font>

数据库和表可不存在

Moongo中的概念有些不一样，文档(数据库)，集合(表)

在 MongoDB 中，集合(表)只有在内容插入后才会创建

### <font color="#0099CC">连接数据库</font>

```python
from pymongo import MongoClient

client = MongoClient( 'localhost', 27017)
db = client. testdb # 使用testdb这个数据库col = db.users #使用users这个集合
```

### <font color="#F77A0B">新增</font>

> insert_one # 插入一条
>
> insert_many # 插入多条

```python
# 新增
from pymongo import MongoClient

client = MongoClient('localhost', 27017)
db = client.testdb  # 使用testdb这个数据库col = db.users #使用users这个集合

col = db.users  # 使用users这个集合
print(col)
rs = col.insert_one({'a': 1, 'b': 2})
rs2 = col.insert_many([
    {'a': 3, 'b': 4},
    {'a': 5, 'b': 6}
    {'a': 'hello', 'b': 'world'}
])
```

![image-20200111150732057](../media/images/image-20200111150732057.png)

### <font color="#F77A0B">查询</font>

> find_one()   # 查询一条
>
> find() # 查询全部(相当于sql的select *)
>
> sort("a", -1)  # 按照a字段排序，**1** 为升序，**-1** 为降序，默认为升序。
>
> limit(n) 返回记录数

<img src="../media/images/image-20200111153521292.png" alt="image-20200111153521292" style="zoom: 80%;" />

```python
from pymongo import MongoClient

client = MongoClient('localhost', 27017)
db = client.testdb  # 使用testdb这个数据库col = db.users #使用users这个集合
col = db.users  # 使用users这个集合

# 1.根据指定条件查询
doc = col.find_one({'a': 1})
print(doc)

# 2.高级查询; a字段中值大于1的数据
myquery = {"a": {"$gt": 1}}
lists = col.find(myquery)
for item in lists:
    print(item)

# 3.使用正则表达式查询
myquery = {"a": {"$regex": "^h"}}
mydoc = col.find(myquery)
for item in mydoc:
    print(item)
```

### <font color="#F77A0B">更新</font>

> update_one # 更新一条
>
> update_many # 更新多条

```python
from pymongo import MongoClient

client = MongoClient('localhost', 27017)
db = client.testdb  # 使用testdb这个数据库col = db.users #使用users这个集合
col = db.users  # 使用users这个集合

myquery = {"a": "hello"}
newvalues = {"$set": {"a": "jiaobaba"}}

col.update_one(myquery, newvalues)

# 输出修改后的"users"集合
for x in col.find():
    print(x)
```

<img src="../media/images/image-20200111154147389.png" alt="image-20200111154147389" style="zoom:80%;" />

### <font color="#F77A0B">删除</font>

> delete_one()   # 删除一条
>
> delete_many() # 删除多条

```python
from pymongo import MongoClient

client = MongoClient('localhost', 27017)
db = client.testdb  # 使用testdb这个数据库col = db.users #使用users这个集合
col = db.users  # 使用users这个集合

myquery = {"a": 5}

col.delete_one(myquery)

# 输出修改后的"users"集合
for x in col.find():
    print(x)
```

