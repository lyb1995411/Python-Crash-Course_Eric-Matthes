# 第5章 if语句

## 5.1 一个简单示例

下面是一个简短的示例，演示了如何使用if语句来正确地处理特殊情形。

```python
cars = ['audi', 'bmw', 'subaru', 'toyota']
for car in cars:
    if car == 'bmw':
        print(car.upper())
    else:
        print(car.title())
        
#输出结果为Audi,BMW,Subaru,Toyota  
```

这个示例中的循环首先检查当前的汽车名是否是`'bmw'`。如果是，就以全大写的方式打印它；否则就以首字母大写的方式打印：

## 5.2 条件测试

- 每条`if语句`的核心都是一个值为`True`或`False`的表达式，这种表达式被称为条件测试。

- Python根据条件测试的值为`True`还是`False`来决定是否执行if语句中的代码：
   - 列表或者字符串非空为`True`，空为`False`。
   - 如果条件测试的值为`True`，Python就执行紧跟在`if语句`后面的代码。
   - 如果为`False`，Python就忽略这些代码。

1. 检查是否相等**==（\==）==**

2. 检查是否相等时不考虑大小写==**（大小写不同的值会被视为不相等）**==

3. 检查是否不相等==**（!\=）**==

4. 比较数字==**（<，<=，>，>=）**==

5. 检查多个条件==**（and与or）**==
   - **and**：如果每个测试都通过了，整个表达式就为True；如果至少有一个测试没有通过，整个表达式就为False。
   - **or**：至少有一个条件满足，整个表达式就为True。仅当两个测试都没有通过时，表达式才为False。

6. 检查特定值是否包含在列表中==**（in与not in）**==

   ---

   执行操作前必须检查列表是否包含特定的值，要判断特定的值是否已包含在列表中，可使用关键字`in`。

   ```python
   requested_toppings = ['mushrooms', 'onions', 'pineapple']
   print('mushrooms' in requested_toppings)  #输出为True
   print('pepperoni' in requested_toppings)  #输出为False
   ```

   ---

   确定特定的值未包含在列表中，使用关键字`not in`

   ```python
   banned_users = ['andrew', 'carolina', 'david']
   user = 'marie'
   if user not in banned_users:
       print(user.title() + ", you can post a response if you wish.")
       
   #输出结果为Marie, you can post a response if you wish.
   ```

   ---

7. 布尔表达式

   随着你对编程的了解越来越深入，将遇到术语布尔表达式，它不过是条件测试的别名。与条件表达式一样，布尔表达式的结果要么为`True`，要么为`False`。

##5.3 `if `语句

 理解条件测试后，就可以开始编写if语句了

### 5.3.1 简单的`if` 语句

最简单的if语句只有一个测试和一个操作：

```python
if conditional_test:
    do something
```

- 在第1行中，`conditional_test`可为任何条件测试，而在紧跟在测试后面的缩进代码`do something`，可执行任何操作。

- 如果条件测试的结果为`True`，Python就会执行紧跟在if语句后面的代码

- 否则Python将忽略这些代码。

```python
age = 19
if age >= 18:
    print("You are old enough to vote!")
```

此代码`conditional_test=age >= 18`，`do something=print("You are old enough to vote!")`。由于`conditional_test`为`True`，则执行语句`print("You are old enough to vote!")`

:star:<font color=Red>***在`if`语句中，缩进的作用与`for`循环中相同。如果测试通过了，将执行`if`语句后面所有缩进的代码行，否则将忽略它们。***</font>

### 5.3.2 `if-else`语句

经常需要在条件测试通过了时执行一个操作，并在没有通过时执行另一个操作；在这种情况下，可使用Python提供的`if-else`语句。

```python
age = 17
if age >= 18:
    print("You are old enough to vote!")
    print("Have you registered to vote yet?")
else:
    print("Sorry, you are too young to vote.")
    print("Please register to vote as soon as you turn 18!")
    
#输出结果为Sorry, you are too young to vote.Please register to vote as soon as you turn 18!
```

- 如果`if`的条件测试通过了，就执行第一个缩进的`print`语句块

- 如果测试结果为`False`，就执行else代码块。

- 这次`age<18`，条件测试未通过，因此执行`else`代码块中的代码。

### 5.3.3 `if-elif-else` 结构

- 经常需要检查超过两个的情形，为此可使用Python提供的`if-elif-else`结构。
- Python只执行`if-elif-else`结构中的一个代码块，它依次检查每个条件测试，直到遇到通过了的条件测试。
- 测试通过后，Python将执行紧跟在它后面的代码，并跳过余下的测试。

```python
age = 12
if age < 4:
    print("Your admission cost is $0.")
elif age < 18:
    print("Your admission cost is $5.")
else:
    print("Your admission cost is $10.")
```

- `if`测试检查一个人是否不满4岁，如果是这样，Python就打印一条合适的消息，并跳
  过余下的测试。

- `elif`码行其实是另一个`if`测试，它仅在前面的测试未通过时才会运行。在这里，我们知道这个人不小于4岁，因为第一个测试未通过。如果这个人未满18岁，Python将打印相应的消息，并跳过`else`代码块。
- 如果`if`测试和`elif`测试都未通过，Python将运行`else`代码块中的代码。

### 5.3.4 使用多个`elif `代码块

可根据需要使用任意数量的`elif`代码块，语句用法类似于`if-elif-else` 。

### 5.3.5 省略else 代码块

Python并不要求`if-elif`结构后面必须有`else`代码块。在有些情况下，`else`代码块很有用而在其他一些情况下，使用一条`elif`语句来处理特定的情形更清晰。

```python
age = 12
if age < 4:
    price = 0
elif age < 18:
    price = 5
elif age < 65:
    price = 10
elif age >= 65:
    price = 5
print("Your admission cost is $" + str(price) + ".")
```

- else是一条包罗万象的语句，只要不满足任何`if`或`elif`中的条件测试，其中的代码就会执行，这可能会引入无效甚至恶意的数据。
- 如果知道最终要测试的条件，应考虑使用一个`elif`代码块来代替`else`代码块
- 这样，你就可以肯定，仅当满足相应的条件时，你的代码才会执行。

### 5.3.6 测试多个条件

检查所有的条件时，应使用一系列不包含`elif`和`else`代码块的简单`if`语句。

```python
requested_toppings = ['mushrooms', 'extra cheese']
if 'mushrooms' in requested_toppings:
    print("Adding mushrooms.")
if 'pepperoni' in requested_toppings:
    print("Adding pepperoni.")
if 'extra cheese' in requested_toppings:
    print("Adding extra cheese.")
print("\nFinished making your pizza!")
```

- 第一个`if`语句检查顾客是否点了配料蘑菇`（'mushrooms'）`，如果点了，就打印一条确认消息。

- 第二个`if`语句检查配料辣香肠`（'pepperoni'）`的代码也是一个简单的`if`语句，而不是`elif`或`else`语句，因此不管前一个测试是否通过，都将进行这个测试。
- 第三个`if`语句检查顾客是否要求多加芝士`（'extra cheese'）`，不管前两个测试的结果
  如何，都会执行这些代码，每当这个程序运行时，都会进行这三个独立的测试。

:star:<font color=Red>***总之，如果你只想执行一个代码块，就使用`if-elif-else`结构；如果要运行多个代码块，就使用一系列独立的`if`语句。***</font>

##5.4 使用if 语句处理列表

### 5.4.1 检查特殊元素

可在`for`循环中包含一条`if`语句：

```python
requested_toppings = ['mushrooms', 'green peppers', 'extra cheese']
for requested_topping in requested_toppings:
    if requested_topping == 'green peppers':
        print("Sorry, we are out of green peppers right now.")
    else:
        print("Adding " + requested_topping + ".")
        print("\nFinished making your pizza!")
        
# 输出结果为
# Adding mushrooms.
# Sorry, we are out of green peppers right now.
# Adding extra cheese.

# Finished making your pizza!
```

这里在比萨中添加每种配料前都进行检查。`if`处的代码检查顾客点的是否是青椒，如果是，就显示一条消息，指出不能点青椒的原因，`else`处的代码确保其他配料都将添加到比萨中。

### 5.4.2 确定列表不是空的

到目前为止，对于处理的每个列表都做了一个简单的假设，即假设它们都至少包含一个元素。我们马上就要让用户来提供存储在列表中的信息，因此不能再假设循环运行时列表不是空的。

```python
requested_toppings = []
if requested_toppings:
    for requested_topping in requested_toppings:
        print("Adding " + requested_topping + ".")
        print("\nFinished making your pizza!")
else:
    print("Are you sure you want a plain pizza?")
```

- 在这里，这个列表为空，因此输出如下——询问顾客是否确实要点普通比萨
- 如果这个列表不为空，将显示在比萨中添加的各种配料的输出。

***批注：***在这里，我们首先创建了一个空列表，其中不包含任何配料。在`if`处我们进行了简单检查，而不是直接执行`for`循环。在`if`语句中将列表名用在条件表达式中时，Python将在列表至少包含一个元素时返回`True`，并在列表为空时返回`False`。如果`requested_toppings`不为空，就运行与前一个示例相同的`for`循环；否则，就打印一条消息，询问顾客是否确实要点不加任何配料的普通比萨。

### 5.4.3 使用多个列表

来看看在制作比萨前如何拒绝怪异的配料要求。下面的示例定义了两个列表，其中第一个列表包含比萨店供应的配料，而第二个列表包含顾客点的配料。这次对于`requested_toppings`中的每个元素，都检查它是否是比萨店供应的配料，再决定是否在比萨中添加它：

```python
available_toppings = ['mushrooms', 'olives', 'green peppers', 'pepperoni', 'pineapple', 'extra cheese']  #1
requested_toppings = ['mushrooms', 'french fries', 'extra cheese'] #2
for requested_topping in requested_toppings:
    if requested_topping in available_toppings:
        print("Adding " + requested_topping + ".")
    else:
        print("Sorry, we don't have " + requested_topping + ".")

print("\nFinished making your pizza!")
```

- 在**==#1==**处，我们定义了一个列表，其中包含比萨店供应的配料。请注意，如果比萨店供应的配料是固定的，也可使用一个元组来存储它们。
- 在**==#2==**处，我们又创建了一个列表，其中包含顾客点的配料，请注意那个不同寻常的配料—`'french fries'`。

- 在`for`语句处，我们遍历顾客点的配料列表。在这个循环中，对于顾客点的每种配料，我们都检查它是否包含在供应的配料列表中（见`if语句`）
- 如果答案是肯定的，就将其加入到比萨中，否则将运行`else`代码块，打印一条消息，告诉顾客不供应这种配料。

## 5.5 设置`if `语句的格式

- 在条件测试的格式设置方面，PEP 8提供的唯一建议是，在诸如`==`、`>=`和`<=`等比较运算符两边各添加一个空格，例如，`if age < 4:`要比`if age<4:`好。

- 这样的空格不会影响Python对代码的解读，而只是让代码阅读起来更容易。

## 5.6 小结

- 编写结果要么为`Ture`要么为`False`的条件测试。
- 编写简单的`if`语句、`if-else`语句和`if-elif-else`结构，在程序中，你使用了这些结构来测试特定的条件，以确定这些条件是否满足。
- 利用高效的`for`循环的同时，以不同于其他元素的方式对特定的列表元素进行处理。
- Python就代码格式方面提出的建议，这可确保即便你编写的程序越来越复杂，其代码依然易于阅读和理解。
  