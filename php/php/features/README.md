### 专题

>目录
* [命名空间](#命名空间)
    * [声明命名空间](#声明命名空间)
    * [导入和别名](#导入和别名)
    * [全局命名空间](#全局命名空间)
    * [参考](#参考)
* [接口](#接口)
    * [示例](#示例)
    * [参考](#参考)


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
```

##### 全局命名空间

若引用类、接口、函数或常量时没有使用命名空间，PHP 假定引用的类、接口、函数或常量在当前命名空间中。

需要引用其他命名空间中的类、接口、函数或常量时，必须使用完全限定的 PHP 类名（命名空间 + 类名）

如，命名空间中（非全局命名空间）中引用全局命名空间的代码时，要在类、接口、函数或常量的名称最前面加上 `\` 符号。

##### 参考
1. "Modern PHP (中文版)"，Josh Lockhart 著，安道译，中国电力出版社，2015. pp12-19.
2. GitHub: codeguy/modern-php/02-features/interfaces/. https://github.com/codeguy/modern-php/tree/master/02-features/namespaces/


#### 接口

##### 示例
定义一个接口 Documentable, 然后三个对象实现此接口，形成一致的操作。

* 定义 `Documentable` 接口
```php
<?php
interface Documentable
{
    public function getId();
    public function getContent();
}
```

* 定义 `HtmlDocument` 类，实现了 `Documentable` 接口
```php
<?php
class HtmlDocument implements Documentable
{
    protected $url;
    public function __construct($url)
    {
        $this->url = $url;
    }
    public function getId()
    {
        return $this->url;
    }
    public function getContent()
    {
        $ch = curl_init();
        curl_setopt($ch, CURLOPT_URL, $this->url);
        curl_setopt($ch, CURLOPT_RETURNTRANSFER, 1);
        curl_setopt($ch, CURLOPT_CONNECTTIMEOUT, 3);
        curl_setopt($ch, CURLOPT_FOLLOWLOCATION, 1);
        curl_setopt($ch, CURLOPT_MAXREDIRS, 3);
        $html = curl_exec($ch);
        curl_close($ch);
        return $html;
    }
}
```

* 定义 `StreamDocument` 类，实现 `Documentable` 接口
```php
<?php
class StreamDocument implements Documentable
{
    protected $resource;
    protected $buffer;
    public function __construct($resource, $buffer = 4096)
    {
        $this->resource = $resource;
        $this->buffer = $buffer;
    }
    public function getId()
    {
        return 'resource-' . (int)$this->resource;
    }
    public function getContent()
    {
        $streamContent = '';
        rewind($this->resource);
        while (feof($this->resource) === false) {
            $streamContent .= fread($this->resource, $this->buffer);
        }
        return $streamContent;
    }
}
```

* 定义 `CommandOutputDocument` 类，实现 `Documentable` 接口
```php
<?php
class CommandOutputDocument implements Documentable
{
    protected $command;
    public function __construct($command)
    {
        $this->command = $command;
    }
    public function getId()
    {
        return $this->command;
    }
    public function getContent()
    {
        return shell_exec($this->command);
    }
}
```


* `DocumentStore` 类来操作具有统一 `Documentable` 接口的对象
```php
<?php
class DocumentStore
{
    protected $data = [];
    public function addDocument(Documentable $document)
    {
        $key = $document->getId();
        $value = $document->getContent();
        $this->data[$key] = $value;
    }
    public function getDocuments()
    {
        return $this->data;
    }
}
```

* 使用 `DocumentStore` 类
```php
<?php
require 'Documentable.php';
require 'DocumentStore.php';
require 'HtmlDocument.php';
require 'StreamDocument.php';
require 'CommandOutputDocument.php';
$documentStore = new DocumentStore();
// Add HTML document
$htmlDoc = new HtmlDocument('http://php.net');
$documentStore->addDocument($htmlDoc);
// Add stream document
$streamDoc = new StreamDocument(fopen('stream.txt', 'rb'));
$documentStore->addDocument($streamDoc);
// Add terminal command document
$cmdDoc = new CommandOutputDocument('cat /etc/hosts');
$documentStore->addDocument($cmdDoc);
print_r($documentStore->getDocuments());
```


##### 参考
1. "Modern PHP (中文版)"，Josh Lockhart 著，安道译，中国电力出版社，2015. pp19-22.
2. GitHub: codeguy/modern-php/02-features/interfaces/. https://github.com/codeguy/modern-php/tree/master/02-features/interfaces























