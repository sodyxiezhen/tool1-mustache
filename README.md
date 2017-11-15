### mustcache模板引擎 简易教程
    mustcache是一款流行的模板引擎，所谓模板引擎就是将数据渲染到事先做好的模板上面，得到最终的数据。
    template.replace(reg,data) 核心原理是正则替换
    
#### mustcache 核心API
```
    Muscache.render(template,object);
    template 是 模板内容
    object 是 需要放入的数据
```
    
#### 最佳实践

```
 	模板单独放置
    <script id="tmp1" type="text/x-mustache-template">
    	你好，{{name}}
    </script>
    <script>
        var template = $.trim($('#tmp1').html());
        var content = Mustache.render(template,{name:'sody'});
    </script>
```


> script标签给一个浏览器不认识的type,浏览器就不会解析，不会执行
    
#### 文档链接
[mustache官方git 仓库](https://github.com/janl/mustache.js)

[网上简易教程一篇~~](http://web.jobbole.com/84906/)
    
#### 懒人往下看
元素赋值
```
<script id="tmp1" type="text/x-mustache-template">
你好，{{name}}
</script>
//变量
var template = $.trim($('#tmp1').html());
var content = Mustache.render(template,{name:'sody'});
```

bool值
```
<script id="tmp2" type="text/x-mustache-template">
	{{#bool}}
	输入的是正
	{{/bool}}
	{{^bool}}
	输入的是负
	{{/bool}}
</script>
//分支结构
	var template2 = $.trim($('#tmp2').html());
	var content2 = Mustache.render(template2,{bool:false});
```

list结构
```
<script id="tmp3" type="text/x-mustache-template">
	{{#names}}
	{{.}}
	{{/names}}
</script>
//遍历list
	var template3 = $.trim($('#tmp3').html());
	var content3 = Mustache.render(template3,{names:['xuexue', 'sody']});
```

map结构
```
<script id="tmp4" type="text/x-mustache-template">
	{{#stu}}
	name == {{name}}
	age == {{age}}
	addr == {{addr}}
	{{/stu}}
</script>
//遍历map
	var template4 = $.trim($('#tmp4').html());
	var content4 = Mustache.render(template4,{stu:{'name':'xuexue','age':18,'addr':'深圳'}});
```