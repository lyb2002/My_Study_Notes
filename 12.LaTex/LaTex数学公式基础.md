# Latex基础



## 1. 上下标

**下标**使用 `_`

 x_1 表示  $x_1$

**上标**使用 `^{}`

x^{2}  表示 $x^{2}$



## 2. 分式

1. 写成分式形式使用 `\frac{分子}{分母}`

    在行内显示：  \frac{a+b+c}{2} 表示 $\frac{a+b+c}{2}$

    在行间显示：

$$
\frac{a+b+c}{2}
$$

可以看到这种方式表示分式时，在行内或者分式中嵌套分式时分式会被压缩，影响视觉效果。如果不想分式被压缩，可以使用下面的方法。

2. 将 `\frac{分子}{分母}` 改为 `\dfrac{分子}{分母}` 即可。

    需要引入`amsmath`包

    $\dfrac{a+b+c}{2} $ 不压缩形式

3. 若想实现相反效果，即在行间显示压缩的分式，改为 `\tfrac `即可。

    $\tfrac{a+b+c}{2}$压缩形式



## 3. 积分、求和、微分

求和号：`\sum^{上限}_{起始}`    $\sum^n_{i=1}$

求连乘：`\prod_{i=1}^{n}`   	$\prod_{i=1}^{n}$

积分号：`\int^{上限}_{下限}`   $\int^{10}_{1}$

微分号：`\mathrm{d}`   $\mathrm{\int^{}x^2dx}$





## 4. 希腊字母表

| $\alpha$ | $\rho$ | $\beta$ | $\delta$ | $\Delta$ | $\nabla$ | $\pi$ | $\sigma$ | $\epsilon$ | $\varepsilon$ |
| -------- | ------ | ------- | -------- | -------- | -------- | ----- | -------- | ---------- | ------------- |
| \alpha   | \rho   | \beta   | \delta   | \Delta   | \nabla   | \pi   | \sigma   | \epsilon   | \varepsilon   |

| $\sin{x}$ | $\cos{x}$ | $\tan{x}$ | $\sqrt{x}$ | $\in$ | $\notin$ |
| --------- | --------- | --------- | ---------- | ----- | -------- |
| \sin{x}   | \cos{x}   | \tan{x}   | \sqrt{x}   | \in   | \notin   |

| $\lambda$ | $\gamma$ | $\theta$ | $\eta$ | $\mu$ | $\tau$ | $\varphi$ | $\partial$ |
| --------- | -------- | -------- | ------ | ----- | ------ | --------- | ---------- |
| \lambda   | \gamma   | \theta   | \eta   | \mu   | \tau   | \varphi   | \partial   |



## 箭头

| $\leftarrow$        | $\rightarrow$      | $\uparrow$     | $\leftrightarrow$ | $\searrow$     | $\swarrow$     |
| ------------------- | ------------------ | -------------- | ----------------- | -------------- | -------------- |
| \leftarrow(或\gets) | \rightarrow(或\to) | \up(down)arrow | \leftrightarrow   | \s(n)e(w)arrow | \s(n)e(w)arrow |

| $\Leftarrow$ | $\Rightarrow$ | $\Uparrow$ | $\Downarrow$ | $\Leftrightarrow$ | $$   |
| ------------ | ------------- | ---------- | ------------ | ----------------- | ---- |
| \Leftarrow   | \Rightarrow   | \Uparrow   | \Downarrow   | \Leftrightarrow   |      |



## 5. 空格

一个空格：`\quad`

两个空格：`\qquad`



## 6. 乘法

`\times`: 乘号



## 7. 约等于

`\approx`



## 8. 矩阵

引入`amsmath`宏包

```latex
\begin{equation*}
A=\begin{bmatrix}
1&2&3\\
4&5&6
\end{bmatrix}
\end{equation*}
```

`matrix`:  无括号

`bmatrix`:	中括号

`pmatrix`:	小括号

`Bmatrix`:	大括号

`vmatrix`:	竖线

`Vmatrix`:	双竖线



## 9. 省略号

`\dots`:	横向

`\vdots`:	纵向

`\ddots`:	斜向



## 10.左侧括号

```text
\begin{cases} 选项1\\ 选项2 \\ \cdots \\ 选项n \end{cases} 
```



## 11.比较运算符

| $\leq$ | `leq`或`le` | Less than or Equal to：小于或者等于     |
| ------ | ----------- | --------------------------------------- |
| $\geq$ | `geq`或`ge` | Greater than or Equal to : 大于或者等于 |
| $\neq$ | `\neq`      |                                         |



## 12. 给公式加上编号

`\tag{1.1}`



## 13. 存在、任意、非

| $\exists$ | `\exists` |
| --------- | --------- |
| $\forall$ | `\forall` |
| $\neg$    | `\neg`    |



## 14. 因为所以

| $\because$   | \because<br/> |
| ------------ | ------------- |
| $\therefore$ | \therefore    |



## 15. **符号上打尖角帽子**

（1）如果是在正文中，例如用\^{Z}即可；

（2）如果是在公式中，例如用\hat{Z}即可。



## 16. 下标在正下方

如果在段内想使上下标位于正上下方的话，我们可以使用 **\limit**  命令。`$\sum \limits_a^b$`显示如下

$\sum \limits_a^b$

给普通符号——非数学运算符加正下方的下标     ` \mathop`
但是对与普通的符号——非数学运算符，我们想让其上下标位于其正上下方应该怎么办呢。有人可能会想还是用   \limits  命令。如 `$x \limits_a^b$`，其实这样会报错，编译无法通过。因为  \limits  命令只能跟在数学运算符后边（如\max，\sum等）。

**对于普通符号，我们可以用 \mathop 命令使得普通的符号表现的跟数学运算符一样。**

如$\mathop{x} \limits_a^b$的显示如下



## 17. 公式对齐

```latex
\begin{aligned}
&(1)\quad若P(x|w_j)P(w_j)=\mathop{\max}_{i\in1,2,\cdots,m}P(x|w_i)P(w_i)，则x\in w_j \\
&(2)\quad若L(x)=\frac{P(x|w_j)}{P(x|w_i)}>\frac{P(w_i)}{P(w_j)}，i=1,2,\cdots,m,i\neq j,则x\in w_j\\
&(3)\quad若\ln L(x)=\ln P(x|w_j)-\ln P(x|w_i)>\ln \frac{P(w_i)}{P(w_j)}，i=1,2,\cdots,m,i\neq j,则x\in w_j
\end{aligned}
```

