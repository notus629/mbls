### 数据库操作

> 目录
* [查询](#查询)
    * [几种查询方法的比较](几种查询方法的比较)

#### 查询

##### 几种查询方法的比较

* `field` 是用于连贯操作，选取字段进行。其他三个方法都用于具体的查询操作，如
```php
    $db->where("id=2")->field('username, password')->find();
```

* `find` 仅选取一行结果，是二维数组，其结果举例如下

```php
Array
(
    [0] => Array
        (
            [password] => $2y$12$22MclhPTdYEAoDqJAG/AjOnCEdMsNjLcEZssSrjevQVbj6TAzNjxi
            [status] => 1
        )

)
```

* `select` 选取所有结果，虽然可以限制其结果的行数，但结果是三维数组，结果举例如下

```php
Array
(
    [password] => $2y$12$22MclhPTdYEAoDqJAG/AjOnCEdMsNjLcEZssSrjevQVbj6TAzNjxi
    [status] => 1
)
```

* `getField` 根据字段查询结果，其结果维数不确定，对于`getField('username, password, status')`,其结如下

```php
Array
(
    [admin] => Array
        (
            [username] => admin
            [password] => $2y$12$22MclhPTdYEAoDqJAG/AjOnCEdMsNjLcEZssSrjevQVbj6TAzNjxi
            [status] => 1
        )

)
```


















