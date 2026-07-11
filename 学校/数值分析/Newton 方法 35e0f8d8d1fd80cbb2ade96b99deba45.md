# Newton 方法

La méthode de Newton s’écrit

$$
x_{n+1}=x_n-\frac{f(x_n)}{f'(x_n)}
$$

En posant

$$
g(x)=x-\frac{f(x)}{f'(x)}
$$

on obtient

$$
x_{n+1}=g(x_n)
$$

Donc la méthode de Newton est une méthode de point fixe.

下一个知识点是第四章最后一块：**Newton 方法**，也叫**牛顿迭代法**。

它用于求非线性方程：

f(x)=0

的近似解。

---

# **第四章 3：Newton 方法**

## **1. 核心公式**

Newton 法的迭代公式是：

\boxed{x_{k+1}=x_k-\frac{f(x_k)}{f'(x_k)}}

前提是：

f'(x_k)\ne 0

也就是说，每一步都需要计算函数值和导数值。

---

## **2. 公式怎么来的？**

在 x_k 附近用切线近似函数：

f(x)\approx f(x_k)+f'(x_k)(x-x_k)

令切线等于 0：

f(x_k)+f'(x_k)(x-x_k)=0

解得：

x=x_k-\frac{f(x_k)}{f'(x_k)}

于是定义：

x_{k+1}=x_k-\frac{f(x_k)}{f'(x_k)}

所以 Newton 法本质是：

\boxed{\text{用切线的零点近似函数的零点}}

---

## **3. Newton 法和不动点法的关系**

Newton 法也可以写成不动点迭代：

x_{k+1}=g(x_k)

其中：

g(x)=x-\frac{f(x)}{f'(x)}

所以 Newton 法其实是一个特殊的不动点迭代。

---

# **4. 例题：用 Newton 法求** \sqrt{2}

要求解：

x^2-2=0

令：

f(x)=x^2-2

则：

f'(x)=2x

Newton 公式为：

x_{k+1}=x_k-\frac{x_k^2-2}{2x_k}

化简：

x_{k+1}=\frac12\left(x_k+\frac{2}{x_k}\right)

取初值：

x_0=1

第一次：

x_1=\frac12\left(1+\frac21\right)=\frac32=1.5

第二次：

x_2=\frac12\left(\frac32+\frac{2}{\frac32}\right)

=\frac12\left(\frac32+\frac43\right)=\frac12\cdot\frac{17}{6}=\frac{17}{12}\approx 1.4167

第三次：

x_3=\frac12\left(\frac{17}{12}+\frac{2}{17/12}\right)

=\frac12\left(\frac{17}{12}+\frac{24}{17}\right)=\frac12\cdot\frac{577}{204}=\frac{577}{408}\approx 1.4142

这已经非常接近：

\sqrt2\approx 1.4142

---

# **5. Newton 法收敛性**

常见结论：

如果 \alpha 是 f(x)=0 的单根，也就是：

f(\alpha)=0,\qquad f'(\alpha)\ne 0

并且初值 x_0 充分接近 \alpha，那么 Newton 法通常二阶收敛。

“二阶收敛”的意思是误差大致满足：

|e_{k+1}|\approx C|e_k|^2

其中：

e_k=x_k-\alpha

所以 Newton 法一旦靠近根，收敛非常快。

---

## **6. 考试常考内容**

Newton 法通常考这几类：

### **类型一：写出 Newton 迭代公式**

给你：

f(x)=x^3-x-1

要求写 Newton 法。

你直接写：

f'(x)=3x^2-1

所以：

x_{k+1}=x_k-\frac{x_k^3-x_k-1}{3x_k^2-1}

---

### **类型二：给初值，算几步迭代**

比如取：

x_0=1

计算：

x_1,\quad x_2

这类题注意保留分数或小数精度。

---

### **类型三：判断是否收敛或收敛阶**

常见判断：

- 若 f'(\alpha)\ne0，根是单根，Newton 法局部二阶收敛；
- 若 f'(\alpha)=0，根是重根，普通 Newton 法通常降为线性收敛。

---

# **7. Newton 法易错点**

### **易错点 1：忘记求导**

Newton 公式一定要用：

f'(x_k)

不是随便除以 x_k，也不是除以 f(x_k)。

---

### **易错点 2：把** x_k **和** x_{k+1} **混在一起**

公式是：

x_{k+1}=x_k-\frac{f(x_k)}{f'(x_k)}

右边全部用旧值 x_k。

---

### **易错点 3：初值不能随便选**

如果 x_0 选得不好，Newton 法可能不收敛，甚至出现：

f'(x_k)=0

导致下一步无法计算。

---

# **8. 模拟题**

用 Newton 法求方程

x^3-x-1=0

在初值

x_0=1

下的前两次迭代：

x_1,\quad x_2

要求：

1. 写出 Newton 迭代公式；
2. 计算 x_1；
3. 计算 x_2。

提示：

f(x)=x^3-x-1

f'(x)=3x^2-1

所以先写：

x_{k+1}=x_k-\frac{x_k^3-x_k-1}{3x_k^2-1}

然后代入 x_0=1。