

  __by RingJohn__

  

[学习链接](https://blog.csdn.net/qq_40818172/article/details/126260661)：参考-CSDN卷不动的小白

![markdown|500](https://img-blog.csdnimg.cn/84b60bcc127844ddacf39a6d9175af0c.png)

  

## 1. 初级用法


### 1.1 标题

***

```html

# 一级标题示例

## 二级标题示例

### 三级标题示例

#### 四级标题示例

##### 五级标题示例

###### 六级标题示例

```

效果如下：

# 一级标题示例

## 二级标题示例

### 三级标题示例

#### 四级标题示例

##### 五级标题示例

###### 六级标题示例

  

***

### 1.2 字体

|代码|效果|

|:-:|:-:|

|\*这是斜体\*|*这是斜体*|

|\_这是斜体\_|_这是斜体_|

|\*\*这是粗体\*\*|**这是粗体**|

|\_\_这是粗体\_\_|__这是粗体__|

|\*\*\*这是粗斜体\*\*\*|***这是粗斜体***|

|\_\_\_这是斜体\_\_\_|___这是粗斜体___|

  

### 1.3 换行

显示文字时使用\<br\/\>换行,如下:

  

***

显示文字时使用<br/>换行

  

***

  

### 1.4 引用

  

\> 引用记号，在引用内容的最前面使用

示例：

```html

> 引用1

>> 引用2

>>> 引用3

```

  

***

> 引用1

>> 引用2

>>> 引用3

  

***

  

### 1.5 链接

#### 方法一

\[链接名称](链接地址)

例如

  

***

```html

[github](https://github.com/)

```

效果如下

[github](https://github.com/)

  

***

### 方法二

\<url>

例如

  

***

```html

<https://github.com/>

```

效果如下

<https://github.com/>

  

***

  

### 1.6 插入图片

```html

![图片描述，可为空但不可无](图片地址)

```

  

***

```html

![百度百科中github标识](https://bkimg.cdn.bcebos.com/pic/e824b899a9014c086e0641f5a33115087bf40

ad15e02?x-bce-process=image/watermark,image_d2F0ZXIvYmFpa2UxODA=,g_7,xp_5,yp_5)

```

  

效果如下：

  

![百度百科中github标识|500](https://bkimg.cdn.bcebos.com/pic/e824b899a9014c086e0641f5a33115087bf40ad15e02?x-bce-process=image/watermark,image_d2F0ZXIvYmFpa2UxODA=,g_7,xp_5,yp_5)

  

***

### 1.7 列表

#### 1.7.1 不含序号的列表：使用*、+、-，再加一个空格作为列表的标记

例如：

  

***

```html

* 列表 1

+ 列表 2

- 列表 3

```

  

效果如下：

* 列表 1

+ 列表 2

- 列表 3

  

***

### 1.7.2 含序号的列表：使用数字并加上.号，再加一个空格作为列表的标记

例如：

  

***

```html

1. 列表 1

2. 列表 2

3. 列表 3

```

效果如下：

1. 列表 1

2. 列表 2

3. 列表 3

***

  

### tips:

可通过使用Tab键实现列表的层级关系。

  

### 1.8 分割线

通过三个\-或三个\*产生分割线。注意，必须与正文部分隔一行

  

### 1.9 删除线

在需要划去的文字前后添加两个~号

  

***

```html

~~要删除的文字~~

```

效果如下：

~~要删除的文字~~

  

***

### 1.10 下划线

添加下划线的格式为`<u>text</u>`

  

***

```html

<u>为文本添加下划线</u>

```

效果如下：

<u>为文本添加下划线</u>

  

***

### 1.11 代码和代码块

#### 1.11.1 在正文内容中添加一行代码

使用反引号`包裹在代码两侧

  

***

```java

在文中插入一行代码`system.out.println("Hello World!");`已完成

```

效果如下：

  

在文中插入一行代码`system.out.println("Hello World!");`已完成

  

***

#### 1.11.2 插入代码块

在代码块前后用`` ``` ``包裹代码块，并在首端的`` ``` ``后著明语言类型

例如建立Java代码块

  

***

  

`` ```java ``

```html

public static int add(int a, int b)

{

  system.out.println(a + b);

  return a + b;

}

```

`` ``` ``

  

效果如下：

```java

public static int add(int a, int b)

{

  system.out.println(a + b);

  return a + b;

}

```

^code

  

***

### 1.12 表格 ^table

表格使用|来分割不同的单元格，使用-来分隔表头和其他行

* `:-` 将表头及单元格内容左对齐

* `-:` 将表头及单元格内容右对齐

* `:-:` 将表头及单元格内容居中

例如：

  

***

```html

|Name|Age|Birthday|

|:-|-:|:-:|

|ZhangSan|21|6.2|

|Tommy|5|7.4|

|Watt|45|12.4|

```

效果如下：

|Name|Age|Birthday|

|:-|-:|:-:|

|ZhangSan|21|6.2|

|Tommy|5|7.4|

|Watt|45|12.4|

  

***

### 1.13 脚注

论文中脚注，可以通过如下方式实现：

  

***

```html

使用 Markdown[^1]可以效率的书写文档, 直接转换成 HTML[^2], 你可以使用 Typora[^T] 编辑器进行书写。

[^1]:Markdown是一种纯文本标记语言

[^2]:HyperText Markup Language 超文本标记语言

[^T]:NEW WAY TO READ & WRITE MARKDOWN.

```

效果如下：

  

使用 Markdown[^1]可以效率的书写文档, 直接转换成 HTML[^2], 你可以使用 Typora[^T] 编辑器进行书写。

[^1]:Markdown是一种纯文本标记语言

[^2]:HyperText Markup Language 超文本标记语言

[^T]:NEW WAY TO READ & WRITE MARKDOWN.

  

>注意：脚注自动被搬运到最后面，请到文章末尾查看，并且脚注后方的链接可以直接跳转回到加注的地方。

  

***

### 1.14 转义

\\, \*, \-, \+, \. 等符号可以通过`\`进行转义；

`` ` ``则需要使用` `` `进行包裹达到转义的效果。

  

## 2 高阶用法

可参考[菜鸟教程](https://www.runoob.com/markdown/md-advance.html)学习更详细内容

  

### 2.1 制作待办事项

* `- [ ]` 表示未完成

* `- [x]` 表示已完成

例如：

  

***

```html

- [ ] 事务1

- [x] 事务

```

效果如下：

  

- [ ] 事务1

- [x] 事务

  

***

>注意：`-`与`[ ]`或`[x]`之间有空格，若未完成事项。方括号之间也需要加空格。

### 2.2 使用LaTeX插入公式

使用`$$`包裹公式两端即可

例如：

***

```latex

$$ R = \frac{U}{I} $$

```

效果如下：

  

$$ R = \frac{U}{I} $$

***

### 2.3 绘制流程图

***

```html

\```flow

st=>start: 开始

op=>operation: 点亮第i盏灯

cond=>condition: i<10?

sub=>subroutine: i+1

e=>end: 结束

  

st->op->cond

cond(yes)->sub(left)->op

cond(no)->e

\```

```

>注意：上面代码中`\`为转义符，实际代码中不需要`\`

  

效果如下：

  

```flow

st=>start: 开始

op=>operation: 点亮第i盏灯

cond=>condition: i<10?

sub=>subroutine: i+1

e=>end: 结束

  

st->op->cond

cond(yes)->sub(left)->op

cond(no)->e

```

  

### 2.4 HTML 语法

#### 2.4.1 通过原生HTML语句创建纵跨两行的列表

***

```html

<table>

    <tr>

        <th rowspan="2">值班人员</th>

        <th>星期一</th>

        <th>星期二</th>

        <th>星期三</th>

    </tr>

    <tr>

        <td>李强</td>

        <td>张明</td>

        <td>王平</td>

    </tr>

</table>

```

效果如下

<table>

    <tr>

        <th rowspan="2">值班人员</th>

        <th>星期一</th>

        <th>星期二</th>

        <th>星期三</th>

    </tr>

    <tr>

        <td>李强</td>

        <td>张明</td>

        <td>王平</td>

    </tr>

</table>

  

***

#### 2.4.2 改变字体格式

***

```html

<font face="宋体" color=#0000ff size=9>改变文字格式</font>

```

效果如下：

<font face="宋体" color=#0000ff size=9>改变文字格式</font>

  

***

  

## 3 VSC编辑MarkDown所需插件一览

* Markdown All in operation

* Markdown PDF

* Markdown TOC

* Markdown Preview Enhanced

* vscode-pdf