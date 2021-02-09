<h1>Python入门(上)</h1>
1. [简介](#简介)

2. [变量、运算符与数据类型](#变量、运算符与数据类型)<br>
   [1. 注释](#1.-注释)<br>
   [2. 运算符](#2.-运算符)<br>
   [3. 变量和赋值](#3.-变量和赋值)<br>
   [4. 数据类型与转换](#4.-数据类型与转换)<br>
   [5. print()函数](#5.-print()-函数)<br>

3. [位运算](#位运算)<br>
   [1. 原码、反码和补码](#1.-原码、反码和补码)<br>
   [2. 按位运算](#2.-按位运算)<br>
   [3. 利用位运算实现快速计算](#3.-利用位运算实现快速计算)<br>
   [4. 利用位运算实现整数集合](#4.-利用位运算实现整数集合)<br>
   
4. [条件语句](#条件语句)<br>
   [1. if 语句](#1.-if-语句)<br>
   [2. if - else 语句](#2.-if---else-语句)<br>
   [3. if - elif - else 语句](#3.-if---elif---else-语句)<br>
   [4. assert 关键词](#4.-assert-关键词)<br>
   
5. [循环语句](#循环语句)<br>
   [1. while 循环](#1.-while-循环)<br>
   [2. while - else 循环](#2.-while---else-循环)<br>
   [3. for 循环](#3.-for-循环)<br>
   [4. for - else 循环](#4.-for---else-循环)<br>
   [5. range() 函数](#5.-range()-函数)<br>
   [6. enumerate()函数](#6.-enumerate()函数)<br>
   [7. break 语句](#7.-break-语句)<br>
   [8. continue 语句](#8.-continue-语句)<br>
   [9. pass 语句](#9.-pass-语句)<br>
   [10. 推导式](#10.-推导式)<br>
   
6. [异常处理](#异常处理)<br>
   [1. Python 标准异常总结](#1.-Python-标准异常总结)<br>
   [2. Python 标准警告总结](#2.-Python标准警告总结)<br>
   [3. try - except 语句](#3.-try---except-语句)<br>
   [4. try - except - finally 语句](#4.-try---except---finally-语句)<br>
   [5. try - except - else 语句](#5.-try---except---else-语句)<br>
   [6. raise语句](#6.-raise语句)<br>



由于比较基础，没有什么特别好记下的，随手记几个吧

1. **while - else**

```python
while 布尔表达式:
    代码块
else:
    代码块
```

当`while`循环正常执行完的情况下，执行`else`输出，如果`while`循环中执行了跳出循环的语句，比如 `break`，将不执行`else`代码块的内容。    

**2.异常处理**

# 异常处理

异常就是运行期检测到的错误。计算机语言针对可能出现的错误定义了异常类型，某种错误引发对应的异常时，异常处理程序将被启动，从而恢复程序的正常运行。

## 1. Python 标准异常总结

- BaseException：所有异常的 **基类**
- Exception：常规异常的 **基类**
- StandardError：所有的内建标准异常的基类
- ArithmeticError：所有数值计算异常的基类
- FloatingPointError：浮点计算异常
- <u>OverflowError</u>：数值运算超出最大限制
- <u>ZeroDivisionError</u>：除数为零
- <u>AssertionError</u>：断言语句（assert）失败
- <u>AttributeError</u>：尝试访问未知的对象属性
- EOFError：没有内建输入，到达EOF标记
- EnvironmentError：操作系统异常的基类
- IOError：输入/输出操作失败
- <u>OSError</u>：操作系统产生的异常（例如打开一个不存在的文件）
- WindowsError：系统调用失败
- <u>ImportError</u>：导入模块失败的时候
- KeyboardInterrupt：用户中断执行
- LookupError：无效数据查询的基类
- <u>IndexError</u>：索引超出序列的范围
- <u>KeyError</u>：字典中查找一个不存在的关键字
- <u>MemoryError</u>：内存溢出（可通过删除对象释放内存）
- <u>NameError</u>：尝试访问一个不存在的变量
- UnboundLocalError：访问未初始化的本地变量
- ReferenceError：弱引用试图访问已经垃圾回收了的对象
- RuntimeError：一般的运行时异常
- NotImplementedError：尚未实现的方法
- <u>SyntaxError</u>：语法错误导致的异常
- IndentationError：缩进错误导致的异常
- TabError：Tab和空格混用
- SystemError：一般的解释器系统异常
- <u>TypeError</u>：不同类型间的无效操作
- <u>ValueError</u>：传入无效的参数
- UnicodeError：Unicode相关的异常
- UnicodeDecodeError：Unicode解码时的异常
- UnicodeEncodeError：Unicode编码错误导致的异常
- UnicodeTranslateError：Unicode转换错误导致的异常

异常体系内部有层次关系，Python异常体系中的部分关系如下所示：


![](https://img-blog.csdnimg.cn/20200710131404548.png)



---
## 2. Python标准警告总结

- Warning：警告的基类
- DeprecationWarning：关于被弃用的特征的警告
- FutureWarning：关于构造将来语义会有改变的警告
- UserWarning：用户代码生成的警告
- PendingDeprecationWarning：关于特性将会被废弃的警告
- RuntimeWarning：可疑的运行时行为(runtime behavior)的警告
- SyntaxWarning：可疑语法的警告
- ImportWarning：用于在导入模块过程中触发的警告
- UnicodeWarning：与Unicode相关的警告
- BytesWarning：与字节或字节码相关的警告
- ResourceWarning：与资源使用相关的警告

## 3. try - except 语句

```python
try:
    检测范围
except Exception[as reason]:
    出现异常后的处理代码
```

try 语句按照如下方式工作：

- 首先，执行`try`子句（在关键字`try`和关键字`except`之间的语句）
- 如果没有异常发生，忽略`except`子句，`try`子句执行后结束。
- 如果在执行`try`子句的过程中发生了异常，那么`try`子句余下的部分将被忽略。如果异常的类型和`except`之后的名称相符，那么对应的`except`子句将被执行。最后执行`try - except`语句之后的代码。
- 如果一个异常没有与任何的`except`匹配，那么这个异常将会传递给上层的`try`中。
demo
```python
try:
    f = open('test.txt')
    print(f.read())
    f.close()
except OSError:
    print('打开文件出错')
```

## 4. try - except - finally 语句

try:     检测范围 except Exception[as reason]:     出现异常后的处理代码 finally:     无论如何都会被执行的代码

不管`try`子句里面有没有发生异常，`finally`子句都会执行。

【例子】如果一个异常在`try`子句里被抛出，而又没有任何的`except`把它截住，那么这个异常会在`finally`子句执行后被抛出。

------

## 5. try - except - else 语句

如果在`try`子句执行时没有发生异常，Python将执行`else`语句后的语句。

```python
try:
    检测范围
except:
    出现异常后的处理代码
else:
    如果没有异常执行这块代码
```

使用`except`而不带任何异常类型，这不是一个很好的方式，我们不能通过该程序识别出具体的异常信息，因为它捕获所有的异常。

try:     检测范围 except(Exception1[, Exception2[,...ExceptionN]]]):    发生以上多个异常中的一个，执行这块代码 else:     如果没有异常执行这块代码