### 特性

目录
* [命名空间](#命名空间)
    * [声明命名空间](#声明命名空间)
    * [导入和别名](#导入和别名)


#### 命名空间

命名空间（或子命名空间）的作用是封装和组织相关的 PHP 类。

PHP 解释器会将其作为前缀添加到类、接口、函数和常量的名称前面。

##### 声明命名空间

声明命名空间的代码始终应该放在 `<?php` 标签后的第一行。

同一个全名空间或子命名空间中的所有类没必要在同一个 PHP 文件中声明，可以在不同的文件中编写属于同一个命名空间的多个类。

```php
<?php
// 注意(建议?)：在 namespace 声明后的命名空间最前面不用加上 `\` 符号，
// - 默认就是从全局命名空间开始。
namespace Symfony\Component\HttpFoundation;
```

##### 导入和别名

**导入**，是指在每个 PHP 文件中告诉 PHP 想使用哪个命名空间、类、接口、函数和常量。导入后就不用输入全名了。

**创建别名**，是指告诉 PHP 我要使用简单的名称引入导入的类、接口、函数或常量。

* 示例1：使用命名空间，没导入，也没创建别名
```php
<?php
// 注意：若类名前面若省略 \ 符号，则表示相对与当前所在的命名空间
//  -（或导入的命名空间?)
$response = new \Symfony\Component\HttpFoundation\Response('Oops', 400);
$response->send();
```

* 示例2：使用命名空间和默认的别名
```php
<?php
// 建议
//    1. use 放在顶部，namespace 之后
//    2. use 导入代码时无需在开头加上 \ 符号，因为 PHP 假定导入的是完全限定的命名空间。
//    3. use 必须出现在全局作用域（不能在类或函数中）
use Symfony\Component\HttpFoundation\Response;
$response = new Response('Oops', 400);
$response->send();
```

* 示例3：使用命名空间，并自定义别名
```php
<?php
use Symfony\Component]HttpFoundation\Response as Res;
//
$r = new Res('Oops', 400);
$r->send();
```

* 导入函数： 
```php 
<?php
use func Namespace\functionName;
//
functionName();
```

* 导入常量
```php
<?php
use constant Namespace\CONST_NAME;
//
echo CONST_NAME;




























