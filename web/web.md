# 1.快速开发网站
```
pip install flask
```

```python
from flask import Flask

app = Flask(__name__)

#创建了网址/show和函数index的对应关系
#用户在浏览器访问/show，自动执行index
@app.route('/show')
def index():
    return "succeed"

if __name__ == '__main__':
    app.run()
```

太丑

新建一个templates文件夹，也可为其它文件夹，但是Flask默认templates，可通过template_folder='xxx'进行修改，文件夹中新建一个index.html

```html
<!doctype html>
<html>
<head>
    <meta charset="UTF-8">
    <title>段落文本</title>
</head>

<body>
	<h2 align="center">这是一个h2标签层级的居中标题</h2>
	<p align="left">这是一个使用了P段落标签的文章的开头</p>
	<p align="center"> 类型：实例</p>
	<p>这是文章的正文，通过使用两个段落标签p可以实现两个
		段落文本的分层</p>
</body>
</html>
```

web.py修改为一下内容，就和浏览器直接打开index.html效果一样
```python
from flask import Flask, render_template

app = Flask(__name__)

@app.route('/show')
def index():
    return render_template('index.html')

if __name__ == '__main__':
    app.run()
```
也可以修改主机名和端口号
```python
app.run(host='', port=)
```


# 2.HTML

## 2.1 编码(head)
```html
<meta charset="UTF-8">
```
## 2.2 Title(head)
网页名称
```html
<title>Title</title>
```

## 2.3 标题
```html
<hx>x级标题</hx>
```

## 2.4 div, span
- div 占一整行 块级标签
- span 该多少占多少 行内标签

## 2.5 超链接
相对，绝对都可以
```html
<a href='https://www.baidu.com/'>点击跳转</a>
<a href='/show'>点击跳转</a>
<a href=' ' target='_blank'>在新标签页打开</a>
```

## 2.6 图片
行内标签

网络url，本地地址都可以
```html
<img src='https://i0.hdslb.com/bfs/banner/3901b731ec20bc12cce3b44728147a6bbe02e2ab.png' />
```
<img src='https://i0.hdslb.com/bfs/banner/3901b731ec20bc12cce3b44728147a6bbe02e2ab.png' style='height: 100px'/>

可以调整大小
```html
<img style="height: 100px; width: 100px" src='' />
```

- 小结
  - 划分  
    块级标签
    ```html
    <h1></h1>
    <div></div>
    ```
    行内标签
    ```html
    <span></span>
    <a></a>
    <img />
  - 嵌套  
    ```html
    实现点击图片跳转到链接
    <a href=" ">
        <img src='' />
    </a>
    ```
## 2.7 列表
```html
<ul>
    <li>1</li>块级标签
    <li>2</li>
    <li>3</li>
</ul>
<ol>
    <li>1</li>
    <li>2</li>
    <li>3</li>
</ol>
```
<ul>
    <li>1</li>
    <li>2</li>
    <li>3</li>
</ul>
<ol>
    <li>1</li>
    <li>2</li>
    <li>3</li>
</ol>

## 2.8 表格
```html
<table board='1'> #board用来加边框
    <thead>
        <tr> <th>ID</th> <th>name</th> <th>age</th> </tr>
    </thead>
    <tbody>
        <tr> <td>5</td>  <td>cz</td>   <td>20</td>  </tr>
        <tr> <td>5</td>  <td>cz</td>   <td>20</td>  </tr>
        <tr> <td>5</td>  <td>cz</td>   <td>20</td>  </tr>
    </tbody>
</table>
```
<table>
    <thead>
        <tr> <th>ID</th> <th>name</th> <th>age</th> </tr>
    </thead>
    <tbody>
        <tr> <td>5</td>  <td>cz</td>   <td>20</td>  </tr>
        <tr> <td>5</td>  <td>cz</td>   <td>20</td>  </tr>
        <tr> <td>5</td>  <td>cz</td>   <td>20</td>  </tr>
    </tbody>
</table>

```html
<table board='1'>
    <thead>
        <tr> 
            <th>ID</th> 
            <th>name</th> 
            <th>age</th> 
            <th>photo</th>
            <th>more</th>
            </tr>
    </thead>
    <tbody>
        <tr> 
            <td>5</td>  
            <td>cz</td>   
            <td>20</td>
            <td>
                <img src='https://i0.hdslb.com/bfs/banner/3901b731ec20bc12cce3b44728147a6bbe02e2ab.png' />
            </td>  

        </tr>
        <tr> 
            <td>5</td>  
            <td>cz</td>   
            <td>20</td>  
            <td>
                <a href='https://www.baidu.com/'>更多信息</a>
            </td>
        </tr>
    </tbody>
</table>
```
<table board='1'>
    <thead>
        <tr> 
            <th>ID</th> 
            <th>name</th> 
            <th>age</th> 
            <th>photo</th>
            <th>more</th>
            </tr>
    </thead>
    <tbody>
        <tr> 
            <td>5</td>  
            <td>cz</td>   
            <td>20</td>
            <td>
                <img src='https://i0.hdslb.com/bfs/banner/3901b731ec20bc12cce3b44728147a6bbe02e2ab.png' />
            </td>  
        </tr>
        <tr> 
            <td>5</td>  
            <td>cz</td>   
            <td>20</td> 
            <td>no photo</td>
            <td> 
                <a href='https://www.baidu.com/'>更多信息</a>
            </td>
        </tr>
    </tbody>
</table>

## 2.9 Input
```html
<input type='text'>行内标签
<input type='password'>
<input type='file'>选择文件上传
<input type='radio' name=''>单选框，name相同时互斥，即单选
<input type='checkbox'>复选框，即多选
<input type='button' value="按钮">
<input type='submit' value="提交">
```
<input type='text'>
<input type='password'>
<input type='file'>

<input type='radio'>
<input type='radio'>可都点

<input type='radio' name='n'>
<input type='radio' name='n'>只能点一个

<input type='checkbox'>篮球
<input type='checkbox'>足球
<input type='checkbox'>乒乓球

<input type='button' value="按钮">
<input type='submit' value="提交">

## 2.10 下拉框
```html
<select>单选
    <option>1</option>
    <option>2</option>
    <option>3</option>
</select>

<select multiple>多选，按住CTRL或shift
    <option>1</option>
    <option>2</option>
    <option>3</option>
</select>
```
<select>
    <option>1</option>
    <option>2</option>
    <option>3</option>
</select>

<select multiple>多选
    <option>1</option>
    <option>2</option>
    <option>3</option>
</select>

## 2.11 多行文本
```html
<textarea></textarea>
```
<textarea></textarea>

## 2.12 提交
```html
<form></form>

<form method="get/post提交方式" action="提交的地址">
    用户名：<input type="text" name="user name"/>
    密码：<input type="password" name="password"/>

    <input type="submit" value="submit" />
</form>
input都必须被form包裹
name一定要加，相当于变量名
```
<form method="get" action="提交的地址">
    用户名：<input type="text" name="user name"/>
    密码：<input type="password" name="password"/>
    <input type="submit" value="submit" />
</form>

# 3.网络请求
- 在浏览器的URL中写入地址，点击回车，访问
```
浏览器会发数据过去，本质上发送的是字符串：
"GET /show http1.1\r\n host:...\r\n user-agent\r\n .. \r\n"
"POST /show http1.1\r\n host:...\r\n user-agent\r\n .. \r\n"
```
- 浏览器向后端发送请求时
  - GET请求【URL访问、表单提交】
    - 现象：GET请求、跳转、向后台传入数据会拼接在URL上
    https://www.google.com/search?q=周杰伦oq=周杰伦&aqs=chrome...
    - 注意：GET请求数据会在URL中体现
  - POST请求【表单提交】
    - 现象：提交表单、登录
    - 注意：不会在URL中体现

# 4.用户注册
web.py
```python
from flask import Flask, render_template, request

app = Flask(__name__)

@app.route('/register')
def register():
    return render_template('register.html')

@app.route('/get/register', methods=['GET'])
def get_register():
    print(request.args)
    return 'succeed'

@app.route('/post/register', methods=['POST'])
def post_register():
    print(request.form)
    return 'succeed'

if __name__ == '__main__':
    app.run()
```
register.html
```html
<!doctype html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>

<body>
	<h1>Register</h1>

    <form method="post" action="post/register">
        用户名：<input type="text" name="user name"/>
        密码：<input type="password" name="password"/>

        <input type="submit" value="submit" />
    </form>

    <!-- <form method="get" action="get/register">
        用户名：<input type="text" name="user name"/>
        密码：<input type="password" name="password"/>

        <input type="submit" value="submit" />
    </form> -->
</body>
</html>
```
Pro

web.py
```python
from flask import Flask, render_template, request

app = Flask(__name__)

@app.route('/register', methods=['GET', 'POST'])
def register():
    if request.method == 'GET':
        return render_template('register.html')

    else:
        user_name = request.form.get('user name')
        pwd = request.form.get('pwd')
        gender = request.form.get('gender')
        hobby_list = request.form.getlist('hobby')
        city = request.form.get('city')
        skill_list = request.form.getlist('skill')
        more = request.form.get('more')

        print(user_name, pwd, gender, hobby_list, city, skill_list, more)
        return 'succeed'

if __name__ == '__main__':
    app.run()
```
register.html
```html
<!doctype html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>

<body>
	<h1>Register</h1>

    <form method="post" action="register">
        <div>
            用户名：<input type="text" name="user name"/>
        </div>

        <div>
            密码：<input type="password" name="pwd"/>
        </div>

        <div>
            性别：
            <input type="radio" name="gender" value="男">男
            <input type="radio" name="gender" value="女">女
        </div>
        
        <div>
            爱好：
            <input type="checkbox" name="hobby" value="篮球">篮球
            <input type="checkbox" name="hobby" value="足球">足球
        </div>

        <div>
            城市：
            <select name="city">
                <option value="北京">北京</option>
                <option value="上海">上海</option>
            </select>
        </div>

        <div>
            技能：
            <select name="skill" multiple>
                <option value="吃饭">吃饭</option>
                <option value="睡觉">睡觉</option>
            </select>
        </div>

        <div>
            更多信息：
            <textarea name="more"></textarea>
        </div>
        <input type="submit" value="submit" />
    </form>
</body>
</html>
```
web.py.login()
```python
@app.route('/login', methods=['GET', 'POST'])
def login():
    if request.method == 'GET':
        return render_template('login.html')
    
    else:
        user_name = request.form.get('user name')
        pwd = request.form.get('pwd')

        print(user_name, pwd)
        return 'succeed'
```
login.html
```html
<!doctype html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>

<body>
	<h1>Register</h1>

    <form method="post" action="login">
        <div>
            用户名：<input type="text" name="user name"/>
        </div>

        <div>
            密码：<input type="password" name="pwd"/>
        </div>

        <input type="submit" value="submit" />
    </form>
</body>
</html>
```
# 5.CSS
## 5.1 快速了解
用来美化html
```html
<img src='' style="height:100px"/>
<div style="color:red">红色</div>
```
## 5.2 应用方式
### 5.2.1 直接
```html
<img src='' style="height:100px"/>
<div style="color:red">红色</div>
```
### 5.2.2 在head中定义
```html
<head>
    <style>
        .c1{
            color:red;
        }
        .c2{
            height:100px;
        }
    </style>
</head>
<body>
    <h1 class='c1'>red</h1>
    <h2 class='c2'>height</h2>
</body>
```
### 5.2.3 写CSS文件
common.css
```css
.c1{
    color:red;
}
.c2{
    height:100px;
}
```
.html
```html
<head>
    <link rel="stylesheet" href="common.css">
</head>
<body>
    <h1 class='c1'>red</h1>
    <h2 class='c2'>height</h2>
</body>
```
## 5.3 选择器
- ID选择器（id只有一个）
```css
#c1{

}
```
```html
<div id='c1'></div>
```
- 类选择器（最多）
```css
.c2{

}
```
```html
<div class='c2'></div>
```
- 标签选择器
```css
div{

}
```
```html
<div></div>
```
- 属性选择器
```css
input[type='text']{
    border: 1px solid red;
}

.v1[xx="456"]{
    color:red;
}
```
```html
<input type='text'>会加边框
<input type='password'>

<div class='v1' xx='123'></div>
<div class='v1' xx='456'></div>会变红
``` 
- 后代选择器
```css
li{
    1
}

.yy li{
    2
}

.yy a{
    儿孙都变
}

.yy > a{
    只变儿子
}
```
```html
<ul>
    <li>1</li>
    <li>1</li>
</ul>

<div class='yy'>

    <ul>
        <li>2</li>
        <li>2</li>
    </ul>


    <a>儿子</a>
    <div>
        <a>孙子</a>
    </div>

</div>
```
- 多个选择器的覆盖问题
```css
.c1{
    color:red;
}

.c2{
    color:green;
}
```
```html
<div class='c1 c2'>c2</div>以css中后定义的为准,不论‘c1 c2’，‘c2 c1’，有冲突都以后定义的c2为准
```
```css
.c1{
    color:red !important;可更改优先级
}
```
## 5.4 使用
### 5.4.1 高度和宽度
```css
.c1{
    height:100px;
    width:50%;
}
```
```html
<div class='c1'>高宽可以改</div>
<span class='c1'>高宽不可以改</span>
```
width支持百分比  
height不支持百分比  
行内标签：默认无效  
块级标签：默认有效  
### 5.4.2 块级标签和行内标签
- 块级
- 行内
- display: inline-block
```css
.c1{
    display:inline-block;
    height:100px;
    width:100px;
}
```
```html
<span class='c1'>高宽可以改</span>
<span style='display:block'>高宽可以改</span>
<div style='display:inline'>高宽不可以改</div>
```
### 5.4.3 字体设置
```css
.c1{
    color: #00FF7F;
    font-size:50px;
    font-size:large;
    font-weight:200;加粗
    font-family:Microsoft Yahei;
}
```
### 5.4.4 文字对齐方式
```css
.c1{
    height:100px;
    width:300px;
    border:1px solid red;
    text-align:center;水平居中
    line-height:100px;只有一行时，等于height，垂直居中
}
```
### 5.5.5 浮动
```css
.c1{
    float:left;
    width:200px;
    height:100px;
    border:1px solid red;
}
```
```html
<span>左边</span>
<span style='float: right'>右边</span>

<div class='c1'></div>float后就不会占整行
```
<span>左边</span>
<span style='float: right'>右边</span>

## CSS未完待续
# 6.BootStrap
## 6.1 初识
https://getbootstrap.com/  
https://www.bootcss.com/  
是别人写好的CSS样式
- 下载BootStrap
- 使用
  - 在html中引入BootStrap
  - 编写html时，按照Bootstrap的规定来编写 + 自定义

```html
引入
<head>
<link rel="stylesheet" href="下载的bootstrap地址">
</head>

<body>
<input type="button" class="btn btn-primary" value="提交">
<input type="button" class="btn btn-success" value="提交">
<input type="button" class="btn btn-danger btn-xs" value="提交">
</body>
```
## 6.2 导航
## 6.3 栅格系统
## 6.4 container
## 6.5 面板
## 案例
## 6.6 图标
- bootstrap提供得不多
- font awesome  
https://fontawesome.com/
## 6.7 BootStrap依赖
BootStrap依赖于javaScript的类库，jQuery  
- 下载jQuery，在页面上应用jQuery
- 在页面上应用BootStrap的JavaScript类库
```html
<body>

    放在body中的下面
    <script src="static/js/jquery-3.7.0.js"></script>
    <script src="static/plugins/bootstrap-3.4.1/js/bootstrap.js"></script>
</body>
```
# 区分
- html  基本
- CSS 好看
- js 动态
  - 编程语言
  - 类库（jQuery）

# 7.JavaScript
- 一门编程语言，浏览器就是解释器
- DOM和BOM
相当于python中的内置模块：re、random、time
- jQuery
相当于pytohn中的第三方模块：requests、openpyxl

## 7.1 初识
```html
<head>
    <style>
        .menus{
            width:200px;
            border:1px solid red;
        }
        .menus .header{
            background-color:gold;
            padding:20px 10px;
        }
    </style>
</head>

<body>
    <div class='menus'>
        <div class='header' onclick='myFunc()'>点击执行myFunc（）</div>
        <div></div>
    </div>

    <script type="text/javascript">
        function myFunc(){
            alert("hello")
            confirm("true or not")
        }
    </script>
</body>
```

## 7.2 位置
一般使用位置2
```html
<head>

    <style> </style>
    <!--位置1-->
    <script src="js文件路径"></script>
    <script type='text/javascript'>
        //javascript代码
    </script>

</head>

<body>

    <!--位置2-->
    <script src="js文件路径"></script>
    <script type='text/javascript'>
        //javascript代码
    </script>
</body>
```

## 7.3 注释
- html
```html
<!-- -->
```
- css
```css
/* */
```
- js
```js
//
/* */
```

## 7.4 变量
```js
var name = '';
console.log(name);
```

## 7.5 类型
- 字符串
```js
var name = 'jack';
var name = String('jack');

var v1 = name.length;
var v2 = name[0]; var v2 = name.charAt(0);
var v3 = name.trim(); //去除空白
var v4 = name.substring(0, 2); //取ja
```

## 7.6 跑马灯
```html
<!doctype html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>

<body>
	<span id="txt">欢迎欢迎，热烈欢迎</span>
    <script type="text/javascript">
        function show(){
            var tag = document.getElementById("txt");
            var datastring = tag.innerText;
            var firstchar = datastring[0];
            var otherstring = datastring.substring(1, datastring.length);
            var newtext = otherstring + firstchar;

            tag.innerText = newtext;
        }
        
        setInterval(show, 1000);
    </script>
</body>
</html>
```

## 7.7 数组
```javascript
var a = [1, 2, 3];
var b = Array([1, 2, 3]);

a[0];
a[1] = "jack";

a.push("mary");//尾部加
a.unshift("john");//头部加

a.splice(索引, 0, 元素)
a.splice(1, 0, "anna")//在哪个位置加

a.pop()//尾部删除
a.shift()//头部删除
a.splice(索引, 1)//删除某个位置元素


//循环
for(var idx in a){
    //idx=0/1/2
    item = a[idx];
}

for(var i=0; i<a.length; i++){
    item = a[idx];
}
```
```html
<!doctype html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>

<body>
	<ul id="city">

    </ul>
    <script type="text/javascript">
        city_list = ["北京","上海","深圳"];
        for(var idx in (city_list)){
            var text = city_list[idx];

            var tag = document.createElement("li");
            tag.innerText = text;
            var parenttag = document.getElementById("city");
            parenttag.appendChild(tag);
        }
    </script>
</body>
</html>
```

## 7.8 对象
```js
info = {
    name:"jack",
    age:18
}

info.name
info.age
info['age']
info['name']

delete info['age']
```
```html
<!doctype html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>

<body>
	<table>
        <thead>
            <tr>
                <th>ID</th>
                <th>姓名</th>
                <th>年龄</th>
            </tr>
        </thead>
        <tbody id="body">
            
        </tbody>
    </table>
    <script type="text/javascript">
        var infos = [
            {ID:0, name:"jack", age:20},
            {ID:0, name:"jack", age:20},
            {ID:0, name:"jack", age:20},
            {ID:0, name:"jack", age:20}
        ]
        var body = document.getElementById("body");

        for(var idx in infos){
            info = infos[idx];
            var tr = document.createElement("tr");  

            for(var key in info){
                var value = info[key];
                var td = document.createElement("td");
                td.innerText = value;
                tr.appendChild(td);

            body.appendChild(tr);
        }
        }

    </script>
</body>
</html>
```

## 7.9 条件语句
```js
if(){}
else{}

if(){}
else if(){}
else if(){}
else{}
```

## 7.10 函数
```js
function Func(){
    
}

Func()
```

## 7.11 DOM
一个模块，可以对html中的标签进行操作
```js
var tag = document.getElementById();

tag.innerText = "";

var tag = document.createElement("div"/"span");

parent_tag.appendChild(sub_tag)嵌套
```
```html
<!doctype html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>

<body>
	<input type="button" value="点击添加" ondblclick="add()">
    <ul id="city"></ul>

    <script type="text/javascript">
        function add(){
            var newtag = document.createElement("li");
            newtag.innerText = "jack";

            var tag = document.getElementById("city");
            tag.appendChild(newtag);
        }

    </script>
</body>
</html>
```
```html
<!doctype html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>

<body>
    <input type="text" placeholder="请输入内容" id="user_input">
	<input type="button" value="点击添加" ondblclick="add()">
    <ul id="city"></ul>

    <script type="text/javascript">
        function add(){
            var texttag = document.getElementById("user_input")
            var newstring = texttag.value

            if newstring.length > 0 {
                var newtag = document.createElement("li");
                newtag.innerText = newstring;

                var tag = document.getElementById("city");
                tag.appendChild(newtag);

                texttag.value = ""
            }
            else{
                alert("none")
            }
        }

    </script>
</body>
</html>
```
## 7.12 jQuery
### 7.12.1 寻找标签（直接）
- ID选择器
```html
<body>
    <h1 id="txt">jack</h1>

    <script src="jQuery地址"></script>
    <script type="text/javascript">
        //$找，#根据id找
        $("#txt").text("改为相应内容")
    </script>
</body>
```
- 样式选择器/类选择器
```js
$(".c1")
```
- 标签选择器
```js
$("h1")
$("div")
```
- 层级选择器
```js
$(".c1 .c2 div")
```
- 多选择器
```js
$(".c1, .c2, div")
```
- 属性选择器
```html
<input type="text" name="n">
```
```js
$("input[name='n']")
```
### 7.12.2 寻找标签（间接）
```html
<div>
    <div>1</div>
    <div id="c1">2</div>
    <div>3</div>
</div>
```
```js
$("#c1").prev() //1
$("#c1").prev().prev() //
$("#c1").next() //3
$("#c1").next().next() //
$("#c1").siblings() //所有兄弟

.parent()
.parent().parent()

.children() //所有儿子
.children(".c1") //所有儿子中寻找class=c1的

.find(".c1") //去所有子孙中找
.find("div") //去所有子孙中找
```
```html
<!doctype html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <style>
        .menus{
            width:200px;
            height: 500px;
            border: 1px solid red;
        }

        .menus .header{
            background-color: gold;
            padding: 10px 5px;
            border-bottom: 1px dotted gray; /*边框*/

            cursor: pointer; /*鼠标放上变样子*/
        }

        .menus .content a{
            display:block;
            padding:5px 5px;
            border-bottom: 1px dotted gray; /*边框*/

        }

        .hide{
            display: none;
        }
    </style>
</head>

<body>
    <div class="menus">
        <div class="item">
            <div class="header" onclick="clickme(this)">北京</div>
            <div class="content hide">
                <a>1区</a>
                <a>2区</a>
            </div>

        </div>
        <div class="item">
            <div class="header" onclick="clickme(this)">上海</div>
            <div class="content hide">
                <a>1区</a>
                <a>2区</a>
            </div>

        </div>
    </div>

    <script src="../static/js/jquery-3.7.0.min.js"></script>
    <script>
        function clickme(self){
            var has_hide = $(self).next().hasClass("hide")
            if(has_hide){
                $(self).next().removeClass("hide")
            }
            else{
                $(self).next().addClass("hide")
            }
        }
    </script>
</body>
</html>
```
```html
<!doctype html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <style>
        .menus{
            width:200px;
            height: 500px;
            border: 1px solid red;
        }

        .menus .header{
            background-color: gold;
            padding: 10px 5px;
            border-bottom: 1px dotted gray; /*边框*/

            cursor: pointer; /*鼠标放上变样子*/
        }

        .menus .content a{
            display:block;
            padding:5px 5px;
            border-bottom: 1px dotted gray; /*边框*/

        }

        .hide{
            display: none;
        }
    </style>
</head>

<body>
    <div class="menus">
        <div class="item">
            <div class="header" onclick="clickme(this)">北京</div>
            <div class="content hide">
                <a>1区</a>
                <a>2区</a>
            </div>

        </div>
        <div class="item">
            <div class="header" onclick="clickme(this)">上海</div>
            <div class="content hide">
                <a>1区</a>
                <a>2区</a>
            </div>

        </div>
    </div>

    <script src="../static/js/jquery-3.7.0.min.js"></script>
    <script>
        function clickme(self){
            $(self).next().removeClass("hide")

            $(self).parent().siblings().find(".content").addClass("hide")
        }
    </script>
</body>
</html>
```
## 未完待续
# 8.MySQL
- 静态页面，永远长一个样
- 动态页面，页面可实时修改和展示
## 1.初识网站
- 默认编写的静态的效果
- 动态：需要用到web框架的功能
```html
index.html中占位符
{{data}}

{{for data in data_list}}
{{data}}
{{endfor}}
```
```python
render_template("index.html", data=" ")
render_template("index.html", data_list=" ")
```
- 什么可以存储数据
  - txt
  - excel
  - 数据库管理系统
    - MySQL（免费）
    - Oracle
    - SQLSever
## 2.安装MySQL
版本
- 8.x
- 5.x
# 8.django
## 8.1 安装
```
pip install django
```
- python310
  - python.exe
  - scripts
    - pip.exe
    - django-admin.exe（工具：创建django项目文件和文件夹）
  - Libs
    - 内置模块
    - site-packages
      - flask
      - django（源码）
## 8.2 创建项目
django项目中有默认的文件和文件夹
### 8.2.1 终端
- 打开终端
- 进入项目目录
- 执行命令创建项目
```
"../../django-admin.exe" startproject 项目名称

若scripts已加入环境变量
django-admin startproject 项目名称
```
### 8.2.2 Pycharm
- Pycharm直接创建django项目
- 比较
  - 命令行是标准的
  - Pycharm还创建了templates目录（删除）
  - settings.py中将templates中dir改为'DIRS':[]
### 8.2.3 默认项目的文件介绍
- mysite
  - manage.py （项目管理、启动项目、创建app、数据管理，不动，常用）
  - mysite
    - ```__init__.py```
    - settings.py （项目配置，常改动）
    - urls.py （url和函数的对应关系，常改动）
    - asgi.py （接收网络请求，不动）
    - wsgi.py （接收网络请求，不动）
## 8.3 创建APP
- 项目
  - app，用户管理
  - app，订单管理
  - app，后台管理
  - app，网站
  - app，API
  - ...
```python
manage.py startapp app01
```
- app01
  - \_\_init__.py
  - admin.py （不动，默认）
  - apps.py （不动，app启动类）
  - migrations
    - \_\_init__.py
  - models.py （**重要**，对数据库操作）
  - tests.py （不动，单元测试）
  - views.py （**重要**，函数）