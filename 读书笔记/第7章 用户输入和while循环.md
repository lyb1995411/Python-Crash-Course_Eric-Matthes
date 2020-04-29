#第7章 用户输入和while循环

## 7.1 函数input()的工作原理

函数`input()`让程序暂停运行，等待用户输入一些文本。获取用户输入后，Python将其存储在一个变量中，以方便使用。

<font color=red>:star:***输入的文本为字符串***</font>

```python
message = input("Tell me something, and I will repeat it back to you: ")
print(message)
```

<font color=red>:star:***函数`input()`接受一个参数：即要向用户显示的提示或说明，让用户知道该如何做。***</font>

### 7.1.2 使用`int()`来获取数值输入

请看下面的程序，它判断一个人是否满足坐过山车的身高要求：

```python
height = input("How tall are you, in inches? ")
height = int(height)

if height >= 36:
    print("\nYou're tall enough to ride!")
else:
    print("\nYou'll be able to ride when you're a little older.")
```

### 7.1.3 求模运算符

处理数值信息时，求模运算符（%）是一个很有用的工具，它将两个数相除并返回余数，求模运算符不会指出一个数是另一个数的多少倍，而只指出余数是多少。

**设计一个交互式的判断数为奇数还是偶数的程序**

```python
number = input("Enter a number, and I'll tell you if it's even or odd: ")
number = int(number)

if number % 2 == 0:
    print("\nThe number " + str(number) + " is even.")
else:
    print("\nThe number " + str(number) + " is odd.")
```

偶数都能被2整除，因此对一个数（number）和2执行求模运算的结果为零，即`number % 2 ==0`，那么这个数就是偶数；否则就是奇数。

## 7.2 while 循环简介

`for`循环用于针对集合中的每个元素都一个代码块，而`while`循环不断地运行，直到指定的条件不满足为止。

### 7.2.1 使用while 循环

你可以使用`while`循环来数数。例如，下面的while循环从1数到5：

```python
current_number = 1
while current_number <= 5:
    print(current_number)
    current_number += 1
```

- 在第1行，我们将`current_number`设置为1，从而指定从1开始数。
- 接下来的设置`while`循环为： 只要current_number 小于或等于5， 就接着运行这个循环。循环中的代码打印`current_number`的值，再使用代码`current_number += 1`将其值加1。
- 只要满足条件`current_number <= 5`，Python就接着运行这个循环。由于1小于5，因此Python打印1，并将current_number加1，使其为2。由于2小于5，因此Python打印2，并将`current_number`加1，使其为3，以此类推。
- 一旦`current_number`大于5，循环将停止，整个程序也将到此结束。

### 7.2.2 让用户选择何时退出

可使用while循环让程序在用户愿意时不断地运行，并在想退出时退出：

```python
prompt = "\nTell me something, and I will repeat it back to you:"
prompt += "\nEnter 'quit' to end the program. "
message = ""
while message != 'quit':
    message = input(prompt)
    if message != 'quit':
        print(message)
```

- 在==***#1***==处，我们定义了一条提示消息，告诉用户他有两个选择：要么输入一条消息，要么输
  入退出值（这里为'quit'）。
- 在==***#2***==处，接下来，我们创建了一个变量名为`message`的空字符串，用于存储用户输入的值。让Python首次执行while代码行时有可供检查的东西。
- 执行到代码行`message = input(prompt)`时，Python显示提示消息，并等待用户输入。不管用户输入是什么，都将存储到变量message中并打印出来
- 接下来，Python重新检查while语句中的条件。只要用户输入的不是单词`'quit'`,Python就会再次显示提示消息并等待用户输入。等到用户终于输入`'quit'`后，Python停止执行while循环，而整个程序也到此结束。

### 7.2.3 使用标志

- 当要求很多条件都满足才继续运行的程序中，可定义一个变量，用于判断整个程序是否处于活动状态。这个变量被称为标志，充当了程序的交通信号灯。

- 你可让程序在标志为`True`时继续运行，并在任何事件导致标志的值为`False`时让程序停止运行。

- 在`while`语句中就只需检查一个条件—标志的当前值是否为`True`，并将所有测试（是否发生了应将标志设置为`False`的事件）都放在其他地方，从而让程序变得更为整洁。

```python
prompt = "\nTell me something, and I will repeat it back to you:"
prompt += "\nEnter 'quit' to end the program. "
active = True
while active:
    message = input(prompt)
    if message == 'quit':
        active = False
    else:
        print(message)
```

- 我们将变量`active`设置成了`True`，让程序最初处于活动状态。这样做简化了`while`语句，因为不需要在其中做任何比较—相关的逻辑由程序的其他部分处理。只要变量active为`True`，循环就将继续运行。
- 在`while`循环中，我们在用户输入后使用一条`if`语句来检查变量`message`的值。如果用户输入的是`'quit'`，我们就将变量`active`设置为`False`，这将导致while循环不再继续执行。
- 如果用户输入的不是`'quit'`，我们就将输入作为一条消息打印出来。

<font color=red>:star:***这个程序的输出与前一个示例相同。在前一个示例中，我们将条件测试直接放在了`while`语句中，而在这个程序中，我们使用了一个标志来指出程序是否处于活动状态，这样如果要添加测试（如`elif语句`）以检查是否发生了其他导致`active`变为`False`的事件，将很容易。***</font>

### 7.2.4 使用break 退出循环

要立即退出`while`循环，不再运行循环中余下的代码，也不管条件测试的结果如何，可使用`break`语句。`break`语句用于控制程序流程，可使用它来控制哪些代码行将执行，哪些代码行不执行，从而让程序按你的要求执行你要执行的代码。

```python
prompt = "\nPlease enter the name of a city you have visited:"
prompt += "\n(Enter 'quit' when you are finished.) "
while True:
    city = input(prompt)
    if city == 'quit':
        break
    else:
        print("I'd love to go to " + city.title() + "!")
```

以`while True:`打头的循环将不断运行，直到遇到`break`语句。这个程序中的循环不断输入用户到过的城市的名字，直到他输入`'quit'`为止。用户输入`'quit'`后，将执行`break`语句，导致Python退出循环。

### 7.2.5 在循环中使用continue

要返回到循环开头，并根据条件测试结果决定是否继续执行循环，可使用`continue`语句，它不像`break`语句那样不再执行余下的代码并退出整个循环。

**例如，来看一个从1数到10，但只打印其中偶数的循环：**

```python
current_number = 0
while current_number < 10:
    current_number += 1
    if current_number % 2 != 0:
        continue

    print(current_number)
```

- 我们首先将`current_number`设置成了0，由于它小于10，Python进入while循环。

- 进入循环后，我们以步长1的方式往上数，因此`current_number`为1。接下来，`if`语句检查`current_number`与2的求模运算结果。如果结果为0（意味着`current_number`可被2整除），就执行`continue`语句，让Python忽略余下的代码，并返回到循环的开头。

- 如果当前的数字不能被2整除，就执行循环中余下的代码，Python将这个数字打印出来：

### 7.2.6 避免无限循环

每个`while`循环都必须有停止运行的途径，这样才不会没完没了地执行下去。

```python
# 这个循环将没完没了地运行！
x = 1
while x <= 5:
    print(x)
```

<font color=red>:star:***要避免编写无限循环，务必对每个while循环进行测试，确保它按预期那样结束。***</font>

## 7.3 使用while 循环来处理列表和字典

`for`循环是一种遍历列表的有效方式，但在`for`循环中不应修改列表，否则将导致Python难以跟踪其中的元素。要在遍历列表的同时对其进行修改，可使用`while`循环。通过将`while`循环同列表和字典结合起来使用，可收集、存储并组织大量输入，供以后查看和显示。

### 7.3.1 在列表之间移动元素

假设有一个列表，其中包含新注册但还未验证的网站用户；验证这些用户后，如何将他们移到另一个已验证用户列表中呢？一种办法是使用一个while循环，在验证用户的同时将其从未验证用户列表中提取出来，再将其加入到另一个已验证用户列表中。代码可能类似于下面这样：

```python
# 首先，创建一个待验证用户列表
# 和一个用于存储已验证用户的空列表

unconfirmed_users = ['alice', 'brian', 'candace']
confirmed_users = [] 
# 验证每个用户，直到没有未验证用户为止
# 将每个经过验证的列表都移到已验证用户列表中
while unconfirmed_users:  #未验证用户列表为空后结束循环
    current_user = unconfirmed_users.pop()
    print("Verifying user: " + current_user.title())
    confirmed_users.append(current_user)

# 显示所有已验证的用户
    print("\nThe following users have been confirmed:")
    for confirmed_user in confirmed_users:
        print(confirmed_user.title())
```

- 我们首先创建了一个未验证用户列表，其中包含用户`Alice`、`Brian`和`Candace`，还创建了一个空列表，用于存储已验证的用户。
- `while`循环将不断地运行，直到列表`unconfirmed_users`变成空的。在这个循环中，函数`.pop()`以每次一个的方式从列表`unconfirmed_users`末尾删除未验证的用户。
- 由于`Candace`位于列表`unconfirmed_users`末尾，因此其名字将首先被删除、存储到变量`current_user`中并加入到列表`confirmed_users`中，接下来是`Brian`，然后是`Alice`。

### 7.3.2 删除包含特定值的所有列表元素

在第3章中，我们使用函数`.remove()`来删除列表中的特定值，这之所以可行，是因为要删除的值在列表中只出现了一次。下面删除列表中所有包含特定值的元素。

```python
pets = ['dog', 'cat', 'dog', 'goldfish', 'cat', 'rabbit', 'cat']
print(pets)
while 'cat' in pets:
    pets.remove('cat')
print(pets)
```

- 进入while循环，因为它发现`'cat'`在列表中至少出现了一次。
- 进入这个循环后，Python删除第一个`'cat'`并返回到while代码行，然后发现`'cat'`还包含在列表中，因此再次进入循环。
- 它不断删除`'cat'`，直到这个值不再包含在列表中，然后退出循环并再次打印列表。

#### 7.3.3 使用用户输入来填充字典

可使用while循环提示用户输入任意数量的信息。下面来创建一个调查程序，其中的循环每次执行时都提示输入被调查者的名字和回答。我们将收集的数据存储在一个字典中，以便将回答同被调查者关联起来：

```python
responses = {}
# 设置一个标志，指出调查是否继续
polling_active = True
while polling_active:
    # 提示输入被调查者的名字和回答
    name = input("\nWhat is your name? ")
    response = input("Which mountain would you like to climb someday? ")

    # 将答卷存储在字典中
    responses[name] = response

    # 看看是否还有人要参与调查
    repeat = input("Would you like to let another person respond? (yes/ no) ")
    if repeat == 'no':
        polling_active = False

    # 调查结束，显示结果
    print("\n--- Poll Results ---")
    
for name, response in responses.items():
    print(name + " would like to climb " + response + ".")
```

- 这个程序首先定义了一个空字典`（responses）`，并设置了一个标志`（polling_active）`，用于指出调查是否继续。只要`polling_active`为`True`，Python就运行while循环中的代码。
- 在这个循环中，提示用户输入其用户名及其喜欢爬哪座山，将这些信息存储在字典`responses`中。
- 然后询问用户调查是否继续，如果用户输入`yes`，程序将再次进入`while`循环；如果用户输入`no`，标志`polling_active`将被设置为`False`，而`while`循环将就此结束，最后一个代码块显示调查结果。

## 7.4 小结

- 如何在程序中使用`input()`来让用户提供信息。

- 如何处理文本和数字输入，以及如何使用`while`循环让程序按用户的要求不断地运行。

- 多种控制`while`循环流程的方式：设置活动标志、使用`break`语句以及使用`continue`语句。

- 如何使用`while`循环在列表之间移动元素，以及如何从列表中删除所有包含特定值的元素。

- 如何结合使用`while`循环和字典。

  