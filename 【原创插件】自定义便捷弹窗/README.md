## 简介

一个轻量级的、可高度自定义的、可自动收集数据的弹窗对话框插件。

## 快速上手

插件依赖(这些需要引入)

- jquery_3.4.1
- dialog.css
- dialog.js

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8" />
		<title></title>
		<link rel="stylesheet" type="text/css" href="css/dialog.css" />
	</head>
	<body>
		<button type="button" id="openDialog">点我打开对话框</button>

		<script src="js/jquery.js" type="text/javascript" charset="utf-8"></script>
		<script src="js/dialog.min.js" type="text/javascript" charset="utf-8"></script>
		<script type="text/javascript">
			$("#openDialog").dialog({
				id: "superDialog",   //必填,必须和已有id不同
				title: "我的标题",   //对话框的标题 默认值: 我的标题
				type: 0, //0 对话框有确认按钮和取消按钮 1 对话框只有关闭按钮
				form: [{
					description: "用户名",
					type: "text",
					name: "username",
					value:"tom"
				}, {
					description: "密码",
					type: "text",
					name: "password",
					value:"123456"
				}], //form 是填充表单的数据,必填
				submit: function(data) {
					//data是表单收集的数据
					console.log(data);
				}
			})
		</script>
		
	</body>
</html>
```

**当你点击确定的时候，就会执行submit里面的函数，**

**submit里面的参数data,就是收集整理后的数据。**



![](http://imgbed-xia-2.oss-cn-hangzhou.aliyuncs.com/img/image-20200816171105462.png)

可以直接通过 data.属性名 获取 详细数据



## 参数解析

> id
>
> 	> 创建成功后弹窗的id
>
> title
>
> 	> 窗口的标题，默认值：我的标题
>
> type
>
> > 0 对话框有确认按钮和取消按钮 
> >
> > 1 对话框只有关闭按钮
>
> form
>
> > 渲染表单的数据来源
> >
> > 	> 数组里面有几个对象，就渲染几个输入框
> > 	 	- description： 输入框的具体描述，对应输入框前面的文字描述
> > 	    - type：对应生成的input标签的type  <input type="text" }/>
> > 	    - name: 对应收集数据后对应的属性名
> > 	    - value： 输入框的初始值，可以不设置
> > 	    - easyClose： 点击遮罩层或者按下Esc都可以快速关闭窗口,默认值false
> >         - afterInit：用于初始化后运行函数
> 内置函数，可以用于配置一些参数
> >         - clearAllData(id)  去除对应id的对话框里的所有数据，可用于提交成功后
> >  		- moveBtn(id, height)  向下移动按钮，参数id是对话框的id,参数height是向下移动的高度


## 兼容性

IE9+都兼容，因为使用了ES6语法，IE8无法模拟。

里面有dialog.js和dialog.min.js , 其中dialog.min.js是经过压缩和Bable转换的，直接调用dialog.min.js就好了。



