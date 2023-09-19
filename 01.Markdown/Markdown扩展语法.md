# 1. 表格

用`|`分隔每列，用`---`创建每列的标题

```text
| Syntax      | Description |
| ----------- | ----------- |
| Header      | Title       |
| Paragraph   | Text        |
```

```text
| Syntax      | Description | Test Text     |
| :---        |    :----:   |          ---: |
| Header      | Title       | Here's this   |
| Paragraph   | Text        | And more      |
```

| Syntax    | Description |   Test Text |
| :-------- | :---------: | ----------: |
| Header    |    Title    | Here's this |
| Paragraph |    Text     |    And more |

更改对其方式



# 2. 围栏化代码

使用三个反引号或波浪号





# 3. 脚注

哈哈哈[^1]

[^1]: My footnote（哈哈哈）.



# 4. 删除线

在要使用删除线的单词前后用两个波浪号`~~`

结果就~~像这样~~。





# 5.  任务列表

创建任务列表：`- [ ]`，选择复选框：`- [x]`

注意：方括号中要有空格或者x，先输入破折号和方括号后，再输入两者之间的空格

- [ ] 

- [x] 



# 6. 使用emoji表情

:tent:

:worried:

:joy:

:house:





# 7. 设置字体颜色

1. HTML

font（字体），顾名思义，`<font>`标签是一个设置文本文字样式的标签，可以设置文本的字体样式、字体的尺寸、字体的颜色。

`<font>`标签的使用：

```html
<!-- 在此处写注释 -->
<!-- face:规定文本的字体 -->
<font face="黑体"> 哈哈 </font>

<!-- color:规定文本的颜色 -->
<font color="red"> 红色 </font>

<!-- size:规定文本的尺寸大小 -->
<font size="5"> 
```



## 7.1 修改字体颜色：

`<font color=Blue>Test</font>`，效果为<font color=Blue>Test</font>。

或者是

`<font color="Blue">Test</font>`，效果为<font color="Blue">Test</font>。

选择[16进制](https://so.csdn.net/so/search?q=16进制&spm=1001.2101.3001.7020)颜色值，例如：

`<font color=#0000FF>Test</font>`，效果为<font color=#0000FF>Test</font>。



## 7.2 修改背景颜色

Background color

修改背景颜色，选择颜色名称，例如：

`<font style=background:red>Test</font>`

`<font style="background:red">Test</font>`

或者是

`<span style=background:red>Test</span>`

`<span style="background:red">Test</span>`

<font style=background:red>Test</font>



## 7.3 支持的颜色

**html**

| HTML        | 示例                                | HTML           | 示例                                   |
| ----------- | ----------------------------------- | -------------- | -------------------------------------- |
| Blue        | <font color=Blue>Test</font>        | Yellow         | <font color=Yellow>Test</font>         |
| Aqua        | <font color=Aqua>Test</font>        | Green          | <font color=Green>Test</font>          |
| Brown       | <font color=Brown>Test</font>       | Gold           | <font color=Gold>Test</font>           |
| Chartreuse  | <font color=Chartreuse>Test</font>  | Darkorange     | <font color=Darkorange>Test</font>     |
| Coral       | <font color=Coral>Test</font>       | DarkOrchid     | <font color=DarkOrchid>Test</font>     |
| ForestGreen | <font color=ForestGreen>Test</font> | LightSteelBlue | <font color=LightSteelBlue>Test</font> |
| Fuchsia     | <font color=Fuchsia>Test</font>     | SeaGreen       | <font color=SeaGreen>Test</font>       |
| Gainsboro   | <font color=Gainsboro>Test</font>   | SpringGreen    | <font color=SpringGreen>Test</font>    |
| Red         | <font color=Red>Test</font>         | YellowGreen    | <font color=YellowGreen>Test</font>    |



**LaTeX**

**1.使用\color**

修改字体颜色使用LaTeX公式`$\color{options}{text}$`。`options`选择颜色，`text`选择公式内容。

示例：

| **序号** | **LaTeX公式**                                                | **LaTeX示例效果**                                            |
| -------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| 1        | `$\color{Green}{y = ax^2 + bx + c}$`                         | $\color{Green}{y = ax^2 + bx + c}$                           |
| 2        | `$\color{Orange}{y} = \color{Red}{kx} + \color{Blue}{b}$`    | $\color{Orange}{y} = \color{Red}{kx} + \color{Blue}{b}$      |
| 3        | `${\color{Emerald}z^2} = {\color{Yellow}x^2} + {\color{Cyan}y^2}$` | ${\color{Emerald}z^2} = {\color{Yellow}x^2} + {\color{Cyan}y^2}$ |

**2.使用\textcolor**

修改字体颜色使用LaTeX公式`$\textcolor{options}{text}$`。`options`选择颜色，`text`选择公式内容。

示例

| **序号** | **LaTeX公式**                                                | **LaTeX示例效果**                                            |
| -------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| 1        | `$\textcolor{Green}{y = ax^2 + bx + c}$`                     | $\textcolor{Green}{y = ax^2 + bx + c}$                       |
| 2        | `$\textcolor{Orange}{y} = \textcolor{Red}{kx} + \textcolor{Blue}{b}$` | $\textcolor{Orange}{y} = \textcolor{Red}{kx} + \textcolor{Blue}{b}$ |
| 3        | `${\textcolor{Emerald}z^2} = {\textcolor{Yellow}x^2} + {\textcolor{Cyan}y^2}$` | ${\textcolor{Emerald}z^2} = {\textcolor{Yellow}x^2} + {\textcolor{Cyan}y^2}$ |



**3. 背景颜色 Background color**

修改背景颜色使用LaTeX公式`$\colorbox{options}{text}$`。`options`选择颜色，`text`选择文本内容。