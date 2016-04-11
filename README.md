## 认识CSS，为网页添加样式

**CSS全称：**Cascading Style Sheets 层叠样式表主要用于定义HTML内容在浏览器内显示的样式，如文字大小、颜色、加粗等。

实例代码：

```html
<style type="text/css">
  p{
	font-size:12px;
    color:red;
    font-weight:bold;
  }
</style>
```

```style```嵌套在```head```标签中，```style```内嵌css代码，```p```的位置代表**选择器**，表示网页内要添加样式的内容；```{ }```内表示**声明**，由**属性**和**值**组成，以冒号分割，多条声明以分号间隔。

##### 使用css代码的优势：

通过定义某个样式，可以让不同网页位置的文字有同一的字体、字号或着色等；

##### CSS的注释

css代码的注释：```/*注释内容*/```；

实例代码：

```css
/*设置段落默认格式*/
p{
  font-size:12px;
  color:red;
}
```

注：多个声明之间由分号分隔，每个声明最好独占一行，便于阅读、修改。

## CSS样式的基本知识

css代码根据插入位置的不同有三种型式：**内联式**、**嵌入式**和**外部式**。

##### 内联式css样式表

将css代码直接写在现有的html标签中。

实例代码：

```css
<p style="color:red; font-size=14px">这里是红色的文字</p>
```

注：将css代码写在**开始标签**的后面，不能写在结束标签中；css代码写在```""```中间，多条声明用```;```隔开。

##### 嵌入式css样式表

由于内联式css代码必须写在html标签内，如果有多个内容需要做同样的样式，需要在每个内容的html标签中写入相同的css代码。可以使用**嵌入式css**代码来解决这个问题，将css样式代码写在```head```标签中的```<style type="text/css">···</style>```之间。

实例代码：

```css
<style type="text/css">
	span{
  color:red;
  font-size:13px;
}
</style>
```

注：嵌入式css代码必须写在```<style>···</style>```之间，并且在```head```标签中。

##### 外部式css样式表

简称**外联式**，将css代码写在一个单独的外部文件中，以```.css```为扩展名，在```head```标签内用```<link />```标签将css样式文件链接到html文件内。

实例代码：

```css
<link href="base.css" rel="stylesheet" type="text/css" /> 
```

注：

1. css样式文件以有意义的单词命名；
2. ```rel="stylesheet" type="text/css"```为固定写法，不能修改；
3. ```link```标签一般写在```head```标签内，但是不能写在```style```标签内。

##### 优先级

```内联式 > 嵌入式 > 外部式```:

**```嵌入式 > 外部式```的前提：**嵌入式css样式的位置在外部式的后面。

```
<link href="base.css" rel="stylesheet" type="text/css" />  /*在style标签之前*/
<style type="text/css">
	span{
 	 color:red;
	}
</style>
```

总结：就近原则，css样式代码离被设置的元素越近，优先级越高。

**```内联式 > 嵌入式 > 外部式```成立的大前提：**内联式、嵌入式、外部式样式表中css样式是在**权值相同**的情况下。

## CSS选择器

##### 选择器定义

每一条css样式定义由两个部分组成，**选择器**和**样式**。

```css
选择器{
  样式;
}
```

选择器：```{ }```之前的部分，指明了```{  }```中的样式作用的对象（网页的相应标签元素）。

##### 标签选择器

指html代码中的标签，例如```body```、```h1```、```p```、```img```等。

实例代码：

```css
p{
  font-size:12px;
  line-height:1.6em;
}
```

设置```p```便签为12px字号，行间距1.6em。

##### 类选择器

实例代码：

```css
.类选择器名称{css样式代码;}
```

注：英文圆点开头；类选择器名称任意起名，不要中文。

**使用方法：**

第一步：使用合适的标签将要修饰的内容标记；

```css
<span>记忆的留念</span>
```

第二步：使用```class="类选择器名称"```为标签设置一个类；

```css
<span class="fox">记忆的留念</span>
```

第三不：设置类选择器css样式；

```css
.stress{color: red;}  /*放在style标签内，注意stress前面的英文圆点号*/
```

##### ID选择器

在很多方面 ```id选择器```类似```类选择器```，有以下区别：

1. 为标签设置```id="id名称"```而非```class="class名称"```。
2. id选择符前面的是#号，而非英文圆点号。

实例代码：

``` css
<span id="myCLass">公开课</span>
```

在```style```标签内的css代码：

```css
<style type="text/css">
	#myClass{
  color:red;
}
</style> 
```

**注：id绝对不能重复使用**

##### 类选择器与ID选择器区别

**相同点**：可以应用于任何元素；

**不同点**：

1. 在一个HTML文档中，id选择器只能在文档中使用一次。类选择器可以多次使用。

     正确代码：

   ```css
     <p>三年级时，我还是一个<span class="stress">胆小如鼠</span>的小女孩，上课从来不敢回答老师提出的问题，生怕回答错了老师会批评我。就一直没有这个<span class="stress">勇气</span>来回答老师提出的问题。</p>
   ```

     错误代码：

   ```css
     <p>三年级时，我还是一个<span id="stress">胆小如鼠</span>的小女孩，上课从来不敢回答老师提出的问题，生怕回答错了老师会批评我。就一直没有这个<span id="stress">勇气</span>来回答老师提出的问题。</p>
   ```

2. 类选择器可以使用**词列表方法**为一个元素同时设置多个样式。id选择器不能使用ID词列表。

   正确代码：

   ```css
   .stress{
       color:red;
   }
   .bigsize{
       font-size:25px;
   }
   <p>到了<span class="stress bigsize">三年级</span>下学期时，我们班上了一节公开课...</p>
   ```

   作用：为“三年级”三个文字设置文本颜色为红色，并且字号为25px

   错误代码：

   ```css
   #stressid{
       color:red;
   }
   #bigsizeid{
       font-size:25px;
   }
   <p>到了<span id="stressid bigsizeid">三年级</span>下学期时，我们班上了一节公开课...</p>
   ```

   没有作用。

##### 子选择器

用于选定指定标签元素的**第一代子标签**，使用```>```符号。

```css
.food>li{border:1px solid red;}
```

使```class="food"```下的子元素```li```加入红色实线边框。

##### 包含（后代）选择器

相较于子选择器只作用于选择标签元素的第一（直接）后代，包含选择器作用于选择标签的**所有后代元素**。用**空格**取代子选择器的```>```。

```css
.first  span{color:red;}
```

总结：```>```代表自选择器，作用与元素的第一代后代；**空格**作用于元素的所有后代。

##### 通用选择器

功能最强大的选择器，使用```*```指定，作用是匹配html中**所有元素标签**。

```css
*{
  color：red；
}
```

作用：所有元素的内容颜色都改为红色。

##### 伪类选择符

伪类选择符允许给html不存在的标签（标签的某种状态）设置样式。比如html中一个标签元素的**鼠标滑过的状态**来设置字体或颜色。

```css
a:hover{color:red;}
```

注：使```a```标签中的内容在鼠标滑过的状态下，字体颜色变为红色。

```:hover```可以放在任何标签上，只是兼容性不是太好，最常用的还是```a:hover```。

##### 分组选择符

需要为html中多个标签设置同一个样式时，可以使用分组选择符```,```，在标签名之间用逗号分隔。

```css
h1,span,h2{
  color:blue;
}
```

## CSS的继承、层叠和特殊性

##### 继承

css的某些样式具有继承性，允许样式不经应用于某个特定的html标签元素，而且**应用于其后代**。

```css
p{color:red;}

<p>三年级时，我还是一个<span>胆小如鼠</span>的小女孩。</p>
```

注：颜色样式，红色不仅应用于```p```标签，还应用于```p```标签的所有元素（```span```等）。

但某些样式并不具有继承性：

```css
p{border:1px solid red;}

<p>三年级时，我还是一个<span>胆小如鼠</span>的小女孩。</p>
```

注：border样式不具有继承性。

##### 特殊性

有时会给同一个元素通过不同的方式（内联式、类选择器、id选择器等）设置了不同的属性，浏览器根据**权值**来判断使用**权值高**的css样式。

**权值的规则**：标签的权值为1；类选择符的权值为10；id选择符的权值为100。

```css
p{color:red;} /*权值为1*/
p span{color:green;} /*权值为1+1=2*/
.warning{color:white;} /*权值为10*/
p span.warning{color:purple;} /*权值为1+1+10=12*/
#footer .note p{color:yellow;} /*权值为100+10+1=111*/
```

注：继承也有权值，值很小，可以理解为**继承的权值最低**。

##### 层叠

层叠用来解决在html文件中对于同一个元素可以有多个css样式存在并且这多个css样式具有相同的权值的问题。

当有相同权值的样式存在时，根据这些css样式的前后顺序来解决，**处于最后面的css样式会被应用**（就近原则）。

```css
p{color:red;}
p{color:green;}
<p class="first">三年级时，我还是一个<span>胆小如鼠</span>的小女孩。</p>
```

注：最后文本会被设置为绿色，理解为后面的样式会覆盖前面的。按照就近原则：可以理解```内联式>嵌入式>外部式```，并且要求```link```标签放在```style```之前。

##### 重要新（！important）

在做网页时需要为某些样式**设置最高权值**，使用```!important```来解决。

```css
p{color:red!important;}
p{color:green;}
<p class="first">三年级时，我还是一个<span>胆小如鼠</span>的小女孩。</p>
```

注：```p```段落中的文字会显示为红色。```!important```要写在```;```前面。

注：当网页制作者不设置css样式时，浏览器会按照自己的一套样式来显示网页，用户也可以在浏览器中设置自己习惯的样式。这时样式优先级：```浏览器默认样式<网页制作者样式<用户自己设置的样式```，**```!important```样式优先级权值高于用户自己设置的样式。**

## CSS格式化排版

##### 文字排版--字体

利用css可以为网页中的文字设置字体、颜色、字号等样式属性。

```css
body{font-family:"宋体";}
```

注：网页中的文字设置为宋体。不要设置不常用字体，如果电脑中没有安装设置的字体，浏览器显示默认的字体。现在的网页一般设置为微软雅黑```body{font-family:"Microsoft Yahei"}```，用英文的兼容性好一点。

##### 字号、颜色

使用```font-size```和```color```来设置字体的颜色和自号。

```css
body{
  font-size:20px;
  color:blue;
}
```

注意在```body``中，将自号设置为20个像素，颜色设置为蓝色。

##### 粗体

```font-weight```来指定字体的宽度。

```css
p span{font-weight:bold;}
```

使用```font-weight```来实现粗体，不要```h```标签和```strong```来实现粗体。

##### 斜体	

```font-style:italic;```来实现斜体。

```css
p a{font-style:italic;}

<p>三年级时，我还是一个<a>胆小如鼠</a>的小女孩。</p>
```

##### 下划线

为文字设置下划线，可以在视觉上强调文字。

```css
p a{text-decoration:underline;}

<p>三年级时，我还是一个<a>胆小如鼠</a>的小女孩。</p>
```

注：使用```text-decoration:underline;``` 实现。

##### 删除线

在网页中实现删除线，```text-decoration:line-through```。

```css
 .oldPrice{text-decoration:line-through;}
```

在```oldPrice```的文本中添加删除线。

##### 缩进

中文文字习惯在段前空两个字符的空白，采用```p{text-indent:2em}```实现。

```css
p{text-indent:2em;}
<p>1922年的春天，一个想要成名名叫尼克卡拉威（托比?马奎尔Tobey Maguire 饰）的作家，离开了美国中西部，来到了纽约。那是一个道德感渐失，爵士乐流行，走私为王，股票飞涨的时代。为了追寻他的美国梦，他搬入纽约附近一海湾居住。</p>
```

注：2em指文字大小的两倍。

##### 行间距（行高）

行高属性：```line-height```

```css
p{line-height:1.5em;}
<p>菲茨杰拉德，二十世纪美国文学巨擘之一，兼具作家和编剧双重身份。他以诗人的敏感和戏剧家的想象为"爵士乐时代"吟唱华丽挽歌，其诗人和梦想家的气质亦为那个奢靡年代的不二注解。</p>
```

注：行高为文字大小的1.5倍。

##### 中文字间距、字母间距

使用```letter-spacing```实现网页排版中的文字间隔或者字母间隔。

```css
h1{
    letter-spacing:50px;
}
...
<h1>了不起的盖茨比</h1>
```

注：在文本为英文是，设置英文字母间距。

**单词间距：**```word-spacing```

```css
h1{
    word-spacing:50px;
}
...
<h1>welcome to imooc!</h1>
```

##### 对齐

为块元素中的文本、图片设置居中样式，使用```text-align:center```实现。

```css
h1{
    text-align:center;
}
<h1>了不起的盖茨比</h1>
```

注：居左left，居右right。

## CSS盒模型

##### 元素分类

在css中，html中的标签元素大体被分为三种不同的类型：**块状元素、内联元素（行内元素）、内联块状元素**。

常用的**块状元素**：

```<div>、<p>、<h1>···<h6>、<ol>、<ul>、<dl>、<address>、<blockquote>、<form>```

**内联元素**：

```<a>、<span>、<br>、<i>、<em>、<strong>、<label>、<q>、<var>、<cite>、<code>```

**内联块状元素**：

```<img>、<input>```

##### 块级元素

在html中，```<div>、<p>、<h1>···<h6>、<ol>、<ul>、<dl>、<address>、<blockquote>、<form>```为块级元素（block），可以将内联元素转换为块级元素。

```css
a{dispaly:block;}
```

注：将内联元素```<a>```转换为块状元素。

块状元素的特点：

1. 每个块级元素都从新的一行开始，并且其后的元素另起一行；
2. 元素的高度、宽度、行高以及顶和底边距都可以设置；
3. 元素宽度在不设置情况下，是它本身父容器的100%（和父元素宽度一致），除非设定一个宽度。

##### 内联元素

在html中，```<a>、<span>、<br>、<i>、<em>、<strong>、<label>、<q>、<var>、<cite>、<code>```就是内联元素（inline），块状元素可以转换为内联元素。

```css
div{
  display:inline;
}
```

内联元素特点：

1. 和其他元素在同一行上；
2. 元素的高度、宽度及顶部、底部边距不可设置；
3. 元素的宽度就是它所包含文字或图片的宽度，不可改变。

##### 内联块状元素

同时具备内联元素与块状元素的特点，```<img>、<input>```是内联块状元素（inline-block）。

```css
p{display:inline-block;}
```

inline-block特点：

1. 和其他元素在同一行上；
2. 元素的高度、宽度、顶部和底部边距都可以设置。















