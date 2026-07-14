 ## Choosing Names
- 1.Names typically don't matter for correctness but they matter a lot for composition  
  名字通常对程序的正确性没有影响，但是它们对代码的组合与构建（可读性与复用性）至关重要。
- 2.Names should convey the meaning or purpose of the values to which they are bound.  
  名字应该传达它们所绑定的值的含义或目的。
- 3.The type of value bound to the name is best documented in a function's docstring.  
  绑定到该名称的值的类型，最好在函数的文档字符串（docstring）中进行记录。
- 4.Function names typically convey their effect (print), their behavior (triple), or the value returned (abs).  
  函数名通常传达它们的作用（如 print 打印）、它们的行为（如 triple 三倍）或返回的值（如 abs 绝对值）。
## Which values deverse a name
### 1. 重复的复合表达式 (Repeated Compound Expressions)
**核心原则**：当代码中多次出现相同的复杂计算时，应该用一个有意义的变量名将其提取出来。这不仅提高了代码的可读性，还能避免重复计算。

* **优化前 (Before):**
  ```python
  if sqrt(square(a) + square(b)) > 1:
      x = x + sqrt(square(a) + square(b))
  ```

* **优化后 (After):**
  *(通过引入变量 `hypotenuse`（直角三角形的斜边）提取重复的复合表达式)*
  ```python
  hypotenuse = sqrt(square(a) + square(b))
  if hypotenuse > 1:
      x = x + hypotenuse
  ```

---

### 2. 复杂表达式的具意部分 (Meaningful Parts of Complex Expressions)
**核心原则**：对于长且复杂的数学公式或逻辑表达式，把其中代表特定数学或业务含义的部分拆解为独立变量，能让代码的数学意图更加清晰。

* **优化前 (Before):**
  ```python
  x = (-b + sqrt(square(b) - 4 * a * c)) / (2 * a)
  ```

* **优化后 (After):**
  *(将一元二次方程求根公式中关键的根式部分命名为 `discriminant`（判别式部分）)*
  ```python
  discriminant = sqrt(square(b) - 4 * a * c)
  x = (-b + discriminant) / (2 * a)
  ```

---

### 3. 更多命名技巧 (More Naming Tips)

#### 📌 技巧 A：如果能起到代码文档化的作用，名字可以长一些
好的变量名自带解释功能，优先于“简写变量名 + 行内注释”的糟糕组合。

* **推荐写法 (Preferable):**
  ```python
  average_age = average(age, students)
  ```
* **不推荐写法 (Avoid):**
  ```python
  # Compute average age of students
  aa = avg(a, st)
  ```

#### 📌 技巧 B：如果代表的是通用数学量或常规概念，名字可以短一些
当变量表示计数、常规数学坐标、任意函数或数学运算参数时，使用行业惯用的单字母命名更简洁清晰：
* `n, k, i` — 通常表示 **整数** (*Usually integers*)，例如循环计数器或索引
* `x, y, z` — 通常表示 **实数** (*Usually real numbers*)，例如三维空间坐标
* `f, g, h` — 通常表示 **函数** (*Usually functions*)

---