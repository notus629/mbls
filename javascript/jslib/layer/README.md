### layer

> 目录
* [介绍](#介绍)
* [参考示例](#参考示例)

#### 介绍
* *[layer](http://layer.layui.com/)*  Web 弹出层组件，用于网页上的弹出框。
* [layer 文档](http://www.layui.com/doc/modules/layer.html)

#### 参考示例
{%ace edit=true lang='javascript'%}
$(function () {

    dialog = {

        // 失败弹出层
        error: function (message) {
            layer.open({
                title: '错误提示',
                content: message,
                icon: 2,
            });
        },

        // 成功弹出层
        success: function (message, url = location.href) {
            layer.open({
                title: '完成',
                content: message,
                icon: 1,
                yes: function () {
                    location.href = url;
                }
            })
        },

        // 确认弹出层
        confirm: function (message, url) {
            layer.open({
                title: '请确认',
                content: message,
                button: ['是', '否'],
                yes: function () {
                    location.href = url;
                }
            })
        }


    }

});
{%endace%}