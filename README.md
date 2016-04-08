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















