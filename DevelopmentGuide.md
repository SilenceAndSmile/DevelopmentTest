# GraphEmbedding Development Guide Beta v1.0
<br />
<br />
This guide was written by using Atom.  
Warning: 正式发布时可能删除中文说明

### python version: 3.6(.2) python版本: 3.6(.2)

***
## 1.Nameing 命名
### Overview 概览
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

### Supplementary Explanation 补充说明
