### GitBook

#### 工具书和手册
* *[GitBook Toolchain Documentation](https://www.gitbook.com/book/gitbookio/docs-toolchain/details)*. GitBook 详细参考文档。
* *[GitBook Plugins](https://plugins.gitbook.com/)*. GitBook 插件库。
* *[GitBook Help Center](https://help.gitbook.com/)*. 包含很多有用的 FAQ.
* *[GitBook Introduction](https://mlewistw.gitbooks.io/gitbook-introduction/content/)*. 截止到 2017-6-27，最后一次更新已是3年前。
* *[GitBook API Reference](https://developer.gitbook.com/)* . For developers.

#### 插件

##### 插件安装
1. 修改 **book.json** 文件，加入 *new-flowchart* 和 *katex* 插件。
```json
{
    "plugins" : ["new-flowchart", "katex"]
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


#### 那些年，我遇到的坑
1. 因为四个空格后是引用，此第一级的列表前不要打四个空格。否则在 * GitBook Editor* 中没有问题，但到了 *gitbook.io* 链接会显示源码，而不会正确的展示。
1. { %  raw  % } { %  endraw  % }慎用，在 GitBookEditor 和 GitBook.com 上表现不一。
1. flow, new-flowchart 两个插件都不起作用。前者似乎语法都有误，无法开启 `gitbook serve`, 后者没法使用。
1. 对于 GitBook.com 在线编辑器以及 Mac OS X 版的 GitBook Editor，都不能正确的预览插件的效果（如 ace 插件，其它插件没有尝试）。但插件的效果能在在线的 book 和本地的 web 版中正确的显示。
    
    
    
    
    
    
    
    
    
    
    
    
    
    
    
    
    
    
    
    
