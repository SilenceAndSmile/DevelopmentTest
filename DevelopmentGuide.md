# Graph Embedding Development Guide Beta v1.0
<br>
<br>
This guide was written by using Atom.<br>
Warning: 正式发布时可能删除中文说明

### python version: 3.6(.2) python版本: 3.6(.2)

***

## 1 Nameing 命名
### 1.1 Overview 概览
| Type 类型                                | Public 公有        | Internal  内部                                                    |
| ---------------------------------------- | ------------------ | ----------------------------------------------------------------- |
| Modules 模块/文件                        | lower_with_under   | _lower_with_under                                                 |
| Classes 类                               | CapWords           | _CapWords                                                         |
| Exceptions 表达式                        | CapWords           |                                                                   |
| Functions 函数                           | lower_with_under() | _lower_with_under()                                               |
| Global/Class Constants 全局/类常量       | CAPS_WITH_UNDER    | CAPS_WITH_UNDER                                                   |
| Global/Class Variables 全局/类变量       | lower_with_under   | _lower_with_under                                                 |
| Instance Variables 实例变量              | lower_with_under   | _lower_with_under (protected) or __lower_with_under (private)     |
| Method Names 方法名称                    | lower_with_under() | _lower_with_under() (protected) or __lower_with_under() (private) |
| Function/Method Parameters 函数/方法参数 | lower_with_under   | lower_with_under                                                  |
| Local Variables 局部变量                 | lower_with_under   |                                                                   |

### 1.2 Supplementary Explanation 补充说明
+ A Python Module is a file that contains Python object definitions and Python statements. A Module accomplishes a task.Unlike to c++/Java,there is no need to limit yourself to one class per module.  一个Python Module(模块)， 是一个包含了Python对象定义和Python语句的文件。与c++/Java不同，不限制一个模块一个类。
+ "Internal" means internal to a module or protected or private within a class. ”内部(Internal)”表示仅模块内可用，或者在类内是保护或私有的。
+ To begin with a single underscore, it means protected. To begin with a double underscore, it means private. 单划线开头表示proteced，双划线开头表示private。

### 1.3 Names to Avoid 命名时应当避免
+ Single character names except for counters or iterators. 除了计数器和迭代器外使用一个字符命名。
+ Begin with a double underscore and end. 以双划线开始和结束。
+ Use dashes(-) in any name. 使用连字符(-)。

## 2 Line Length 行长度
##### Maximum line length is 80 characters. 每行最多不超过80个字符。
<strong>The following exceptions:_ 以下情形例外：</strong>
+ _Long import statements._
+ _URLs in comments._
```python
Yes: #You can found this file at
     #https://github.com/SilenceAndSmile/DevelopmentTest/blob/master/DevelopmentGuide.md
```
```python
No: #You can found this file at
    #https://github.com/SilenceAndSmile/DevelopmentTest/blob/master/DevelopmentGuide
    #.md
```

Do not use backslash line continuation, just use an extra pair of parentheses. 不要使用反斜杠连接行，而应使用一组额外的括号。

## 3 Comments 注释
##### Uniform use of English writing Comments. 统一使用英语书写注释。
### 3.1 Module(part), Class and Function 模块(一部分)，类和函数
##### For these, write comments using document strings. 对于这些，使用文档字符串书写注释。
__The document strings start and end with three quotes. A doc string is a string that is the first statement in a module, class or function.__ These strings can be extracted automatically through the \_\_doc__ member of the object and are used by pydoc. <strong>文档字符串使用三个引号来开始和结束。文档字符串是模块, 类或函数里的第一个语句。</strong>这些字符串可以通过对象的__doc__成员被自动提取, 并且被pydoc所用。
#### 3.1.1 Module(part) 模块(一部分)
##### Briefly explain its purpose. 简要说明其用途。
```python
"""Use spectral clustering analysis for geographic network data.
"""
# other comment of module.Do not confuse it with document strings.
```


## 4 Imports Formatting 导入格式
##### Imports should be on separate lines.Imports are always put at the top of the file, just after the doc strings of module and before module globals and constants. 每个导入应该单独占一行。导入文件位于模块的文档字符串和模块全局变量与全局常量之前。
