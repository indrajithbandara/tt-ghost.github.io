---
title: 前端入门一小时
---

说明：本教程适用于对前端知识零基础同学，使对前端有一些概念性的认识。如有不解或不正确地方，欢迎拍砖。

## 前半小时
### 与其他职位关系
前端工程师(Front-End-Enginer，简称FE)的上游通常是PM和UI，下游通常是后端RD

### 前端语言
前端语言：HTML + CSS + JS；首先看一个简单的<code>Hello World!</code>，将以下代码复制到<code>index.html</code>的文件中，然后打开就可以看到了。
```html
<!doctype html>
<html>
  <head>
    <title>Hello World!</title>
  </head>
  <body>
    <h1>Hello World!</h1>
  </body>
</html>
```

*这是一个仅仅由html显示的<code>Hello World!</code>。*
#### 代码说明
+ 第一行是文档类型申明。这里指定的是<code>html5</code>文档类型。
+ 接下来是由**成对**的标签组成的html，当然html也有非闭合的标签，对于非闭合标签一般会在<code>></code>前添加一个斜线<code>/</code>，虽然很多浏览器能够解析这种不带反斜线的非闭合标签，至少在编码风格一致上也推荐加上反斜线。如：
  + <code><br /></code>：换行符
  + <code><input type="text" /></code>：输入框 等
  
+ 一个标准html文件应该由文档类型申明，然后由<code>html</code>包裹的<code>head</code>、<code>body</code>标签。
  + <code>head</code>标签：
    + 标签内容不会在浏览器中直接显示；通常有一个<code>title</code>：文档名称，会显示在浏览器当前tab上；
    + <code>style</code>、<code>link</code> 标签通常也会放在 <code>head</code>中，分别对应**内联样式**和**外部样式**
    + 另外还有一些<code>meta</code>标签，用于描述文档的一些属性，如<code><meta charset="utf-8" /></code>知名文档编码类型
  + <code>body</code>
    + <code>body</code>内的内容将显示在浏览器中
    + 另外经常会把一些JS文件放在<code></body></code>之前，是这样引入**<scrpt src="js/main.js"></scrpt>** 
    
+ html注释
  + 以 **<!--** 开始，以**-->**结束的标签，可以跨行，但不能嵌套

*添加样式(style或link)和脚本(script)后的html*，如下：
```html
<!doctype html>
<html>
  <head>
    <meta charset="utf-8">
    <title>Hello World!</title>
    <link rel="stylesheet" type="text/css" src="./css/main.css" />
    <style>
      .red{
        color:red;
      }
    </style>
  </head>
  <body>
    <h1 class="red">Hello World!</h1>
    <button id="butotn">点击我</button>
    <!-- 我是一段注释 -->
    <!--
      <h1 class="red">!</h1>
    -->
    <script src="./lib.js"></script>
    <script>
      var btn = document.getElementById("button");
      btn.addEventListener("click", function(){
        alert("你点击了按钮");
      });
    </script>
  </body>
</html>
```

<code>main.css</code>文件如下
```css
*{
  margin: 0;
  padding: 0
}
h1{
  font-size: 20px;
}
```

<code>lib.js</code>文件如下：
```javascript
(function(w, undefined){
  var Lib = {
    this.version ＝ "0.0.1"
  }

  Lib.prototype = (function(){
    var proto = {
      trim: funciton(str){
        return str.repleace(/(^\s*)|(\s*$)/g, '');
      }
    }
    return proto;
  })();

  w.Lib = new Lib();
})(window);
```

+ 样式使页面根据UI效果图定位、设置等。其中可以通过<code>style</code> 添加页面内样式，也可以通过<code>link</code>引入外部 <code>css</code> 文件，通过 <code>style</code>好处是可以少发一个css文件的请求，缺点是不能被缓存，不易维护，每次打开这个<code>index.html</code>
+ 脚本跟上面讲的类似。脚本实现的核心功能是添加页面内外的交互，让页面真正动起来。

## 后小时

### CSS

#### 盒子模型
html标签元素根据显示特性可以分为三种类型：行内元素、块元素、行内块元素
+ 行内元素：span\a\i\em\b\strong\img\canvas
+ 块元素：html\body\div\h1~h6\p\table\ul\ol\li\header\footer\hgroup...
+ 行内块元素：

##### 标准盒子模型

|──────────────────────────────────── top ──────────────|
|          |─────────────────────────────────────────|  |
|          |          |───────────────────────────|  |  |
|left      |          |                           |  |  |
|          |          |           |─────────────| |  |  | right
|<-margin->|<-border->|<-padding->|<--content-->| |  |  |
|          |          |           └─────────────  |  |  |
|          |          └───────────────────────────   |  |
|          └──────────────────────────────────────────  |
└─────────────────────────────────── bottom ────────────

#### 书写规范

+ 颜色设置
```css
/* 通常颜色使用16进制表示，也可以使用rgb、rgba等表示，如下表示白色文字，纯黑且50%半透明背景，边框颜色为不透明深灰色*/
body{
  color:#fff;
  background-color:rgba(0,0,0,.5);
  border-color:rgb(100,100,100);
}
/* 常见颜色可以直接使用英文单词，如red,green,blue,white,black,yellow,gray等 */
form{color:black}
```

+ padding/margin/border及简写
```css
/* 为0时，可以省去单位 */
/* 
h1{
  padding-left:0;
  padding-right:0;
  padding-bottom:0;
  padding-left:0;
}
 */
h1{padding:0}
/* 最后一个属性可以去掉分号，书写时推荐保留 */
h2{margin:5px; padding:0px}
h3{
  padding:10px 5px;
}
/* 等价于 */
/* 
h3{
  padding-top:10px;
  padding-right:5px;
  padding-bottom:10px;
  padding-left:5px;
}
 */
}
h4{
  padding:10px 5px 8px;
}
/* 设置的顺序为上右下左，同理margin和border属性，等价于 */
/*
h4{
  padding-top:10px 5px 8px;
  padding-right:5px;
  padding-bottom:8px;
  padding-left:5px;
}
 */
h5{
  border:1px solid #f00;
}

```

+ 常见符合属性
padding\margin\border\background\font\overflow
  + 其中padding\margin\border

#### 注释
```css
/* css注释，可多行 */
```

#### 选择器
important(!important)、id(#content)、类(.title)、标签(h1)、属性([type="text"])、后代(div a)、子(div>a)等


#### CSS属性
根据是否对相邻元素产生影响可以分为以下两种：
+ 只影响自身
常见属性有：<code>background</code>、<code>color</code>
+ 影响响铃元素

#### 单位
px\%\em\rem\

#### 常见布局




