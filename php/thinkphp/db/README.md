### 数据库操作

> 目录

#### 查询
##### find, field, getField, select 方法比较
* field 是用于连贯操作，选取字段进行。其他三个方法都用于具体的查询操作，如
```
    $db->field('username, password')->find();
```