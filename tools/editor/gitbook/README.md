### GitBook

### 工具书和手册
* [GitBook Toolchain Documentation](https://www.gitbook.com/book/gitbookio/docs-toolchain/details). GitBook 格式详细参考文档.
* [GitBook Plugins](https://plugins.gitbook.com/)
* [GitBook Help Center](GitBook Help Center). 包含很多有用的 FAQ.
* [GitBook Introduction](https://mlewistw.gitbooks.io/gitbook-introduction/content/). 截止到 2017-6-27，最后一次更新已是3年前。
* [GitBook API Reference](https://developer.gitbook.com/) . For developers.

#### 插件

##### 插件安装
1. 修改 **book.json** 文件，加入 *new-flowchart* 插件。
```
{
    "plugins" : ["new-flowchart"]
}
```
2. 执行 `gitbook install` 命令，安装所有插件. 注意: 如同 git 命令一样, git install 也需要在该 book 的当前目录执行（即 book.json 所在目录)

##### 插件列表
* [GitBook Ace Plugin](https://github.com/ymcatar/gitbook-plugin-ace "Ace") 代码高亮插件。 [示例](https://ymcatar.gitbooks.io/gitbook-test/content/testing_ace.html)
* [new-flowchart](https://github.com/nsdont/gitbook-plugin-new-flowchart#readme). 画流程图插件
* [disqus](https://github.com/GitbookIO/plugin-disqus). 评论插件




#### 那些年，我遇到的坑
* 因为四个空格后是引用，此第一级的列表前不要打四个空格。否则在 * GitBook Editor* 中没有问题，但到了 *gitbook.io* 链接会显示源码，而不会正确的展示。
* `{% raw %} {% endraw %}` 似乎不起作用
    
