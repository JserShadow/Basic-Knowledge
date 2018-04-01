#mongoDB指令
>use test 连接到`test`数据库
>show dbs 显示当前所有的数据库
>show tables 显示当前连接的数据库的所有表
>db.collection.find() 查找当前表里的所有数据(压缩输出)
>db.collection.find().pretty() 功能同上(正常输出)
>db.collection.find(options).pretty() 根据options里的条件查找对应数据
>db.collextion.findOne(options) 根据options查找对应数据(只返回查找到的第一个)
>db.collection.find().sort(num) 排序返回查找到的数据 num可为1或-1
>db.collection.update(options,newdata) 找到符合options的数据并更新为newdata
>db.save() 直接保存数据(不管会不会重复)
>$set:{} 更改某键值对的数据
>db.collection.count() 返回某表数据量
>$lt/$gt 小于/大于某条件