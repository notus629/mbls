### GitBook

>目录
* [工具书和手册](#工具书和手册)
* [基础](#基础)
* [插件](#插件)
    * [插件安装](#插件安装)
    * [插件列表](#插件列表)
    * [ace 插件](#ace-插件)
* [那些年，我所遇到的坑](#那些年，我所遇到的坑)

#### 工具书和手册
* *[GitBook Toolchain Documentation](https://www.gitbook.com/book/gitbookio/docs-toolchain/details)*. GitBook 详细参考文档。
* *[GitBook Plugins](https://plugins.gitbook.com/)*. GitBook 插件库。
* *[GitBook Help Center](https://help.gitbook.com/)*. 包含很多有用的 FAQ.
* *[GitBook Introduction](https://mlewistw.gitbooks.io/gitbook-introduction/content/)*. 截止到 2017-6-27，最后一次更新已是3年前。
* *[GitBook API Reference](https://developer.gitbook.com/)* . For developers.

#### 基础
1. `gitbook` 命令，如，在本地生成 web 版 book，并能以 * http://localhost:4000 * 的方式访问。
```
$ gitbook serve
```

#### 插件

##### 插件安装
1. 修改 **book.json** 文件，加入 *ace* 和 *katex* 插件。
```json
{
    "plugins" : ["ace", "katex"]
}
```
2. 执行 `gitbook install` 命令，安装所有插件. 注意: 如同 git 命令一样, git install 也需要在该 book 的当前目录执行（即 book.json 所在目录)

##### 插件列表
* *[-highlight](https://plugins.gitbook.com/plugin/highlight)*. GitBook 的缺省高亮插件, 即插件库的 *highlight* 和 *ponylang-highlight* 插件。
* *[ace](https://github.com/ymcatar/gitbook-plugin-ace "Ace")*. 代码高亮插件。 [示例](https://ymcatar.gitbooks.io/gitbook-test/content/testing_ace.html)
* *[disqus](https://plugins.gitbook.com/plugin/disqus)*. 评论插件。
* *[emphasize](https://plugins.gitbook.com/plugin/emphasize)*. 文字强调插件（可以指定不同的颜色）。
* *[katex](https://plugins.gitbook.com/plugin/katex)*. 使用 *KaTeX* 进行数学排版的插件。
* *[new-flowchart](https://plugins.gitbook.com/plugin/new-flowchart)*. 利用 *flow.js* 画流程图插件。
* *[sunlight-highlighter](https://plugins.gitbook.com/plugin/sunlight-highlighter)*. 代码高亮插件 *Sunlight highlighter*.

##### ace 插件

插件呈现的结果在 Web 中可以正常显示，在 GitBook Editor 中无法正确显示。

* 示例 - c++ 代码 

{%ace edit=true, lang='c_cpp'%}
// This is a hello world program for C.
#include <stdio.h>

int main(){
  printf("Hello World!");
  int a;
  return 1;
}
{%endace%}



#### 那些年，我所遇到的坑
1. 因为四个空格后是引用，此第一级的列表前不要打四个空格。否则在 * GitBook Editor* 中没有问题，但到了 *gitbook.io* 链接会显示源码，而不会正确的展示。

1. `{ %  raw  % } { %  endraw  % } `慎用，在 GitBookEditor 和 GitBook.com 上表现不一。（ { 或 } 与 % 之间无空格）.

1. GitBook 表格中，使用 `gitbook serve` 解析时，出现 'unexpected variable' 的错误，将这段错误用 `{ % raw % }` 
和 `{ % endraw % }` 包起来后错误消失。

1. flow, new-flowchart 两个插件都不起作用。前者似乎语法都有误，无法开启 `gitbook serve`, 后者没法使用。

1. 对于 GitBook.com 在线编辑器以及 Mac OS X 版的 GitBook Editor，都不能正确的预览插件的效果（如 ace 插件，其它插件没有尝试）。但插件的效果能在在线的 book 和本地的 web 版中正确的显示。

1. 原生的代码高亮中不能有空行，否则判定代码高亮结束。

1. 对于标题的 id，可以查看网页源码。特殊的举例
    * Power Designer -> power-designer
    * Workbench -> workbench
    * 中文 -> 中文
    
    
    
    
    
    
    
    
    
    
    
    
    
    
    
    
    
    
    
    
