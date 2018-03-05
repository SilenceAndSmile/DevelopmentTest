# Graph Embedding Development Guide for Python Beta v1.0
<br>
<br>
This guide was written by using Atom.<br>
The python style of this guide references PEP8 and google python style guide.<br>
<br>
Author: SilenceAndSmile<br>
Last Update Time: March 5, 2018<br>
<br>
<del>Warning: 正式发布时可能删除中文说明</del>

### Python Version: 3.6(.2) python版本: 3.6(.2)
### Encoding Format: UTF-8 编码格式：UTF-8

***
<br>

## Contents 目录
+ <strong>[1 Nameing 命名](#1)
  + [1.1 Overview 概览](#1.1)
  + [1.2 Supplementary Explanation 补充说明](#1.2)
  + [1.3 Names to Avoid 命名时应当避免](#1.3)
+ [2 Line Length 行长度](#2)
+ [3 Comments 注释](#3)
  + [3.1 Document Strings 文档字符串](#3.1)
    + [3.1.1 Modules(part) 模块(一部分)](#3.1.1)
    + [3.1.2 Functions and Methods 函数和方法](#3.1.2)
    + [3.1.3 Classes 类](#3.1.3)
  + [3.2 Block Comments 块注释](#3.2)
    + [3.2.1 Modules(other parts) 模块(其余部分)](#3.2.1)
    + [3.2.2 Complicated Operations 复杂操作](#3.2.2)
  + [3.3 Inline Comments 行注释](#3.3)
+ [4 Imports Formatting 导入格式](#4)
+ [5 Indentation 缩进](#5)
+ [6 Blank Lines 空行](#6)
+ [7 Punctuation and Whitespace 标点和空格](#7)</strong>
<br>

<h2 id='1'>1 Nameing 命名</h2>
<h3 id='1.1'>1.1 Overview 概览</h3>

| Type 类型                                | Public 公有        | Internal  内部                                                    |
| :--------------------------------------: | :----------------: | :---------------------------------------------------------------: |
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

<h3 id='1.2'>1.2 Supplementary Explanation 补充说明</h3>

+ A Python Module is a file that contains Python object definitions and Python statements. A Module accomplishes a task.Unlike to c++/Java,there is no need to limit yourself to one class per module.  一个Python Module(模块)， 是一个包含了Python对象定义和Python语句的文件。与c++/Java不同，不限制一个模块一个类。
+ "Internal" means internal to a module or protected or private within a class. ”内部(Internal)”表示仅模块内可用，或者在类内是保护或私有的。
+ To begin with a single underscore, it means protected. To begin with a double underscore, it means private. 单划线开头表示proteced，双划线开头表示private。

<h3 id='1.3'>1.3 Names to Avoid 命名时应当避免</h3>

+ Single character names except for counters or iterators. 除了计数器和迭代器外使用一个字符命名。
+ Begin with a double underscore and end. 以双划线开始和结束。
+ Use dashes(-) in any name. 使用连字符(-)。
<br>

<h2 id='2'>2 Line Length 行长度</h2>

```
Maximum line length is 80 characters.
每行最多不超过80个字符。
```
<strong>The following exceptions:_ 以下情形例外：</strong>
+ <em>Long import statements. 长的导入模块语句。
+ URLs in comments. 注释中的URL。
+ Inline comments(see in the section 3.3). 行注释(参见3.3节)。</em>
```python
Yes: # You can found this file at
     # https://github.com/SilenceAndSmile/DevelopmentTest/blob/master/DevelopmentGuide.md
```
```python
No: # You can found this file at
    # https://github.com/SilenceAndSmile/DevelopmentTest/blob/master/DevelopmentGuide.
    # md
```
Do not use backslash line continuation, just use an extra pair of parentheses. 不要使用反斜杠连接行，而应使用一组额外的括号。<br>
<em>A row over 80 characters in comment(except URLs) need be divided into multiple rows(use vertical alignment between this divided rows). See examples in the comments section. 注释中超过80个字符的行(URL除外)需要被分为多行(在这些分割开的行之间使用垂直对齐)。请参阅注释一节中的例子。</em>
```python
Yes: SpectralClustering(
         n_clusters=8, eigen_solver=None, random_state=None, n_init=10, gamma=1.0,
         affinity=’rbf’, n_neighbors=10, eigen_tol=0.0, assign_labels=’kmeans’, degree=3,
         coef0=1, kernel_params=None, n_jobs=1)
```
<br>

<h2 id='3'>3 Comments 注释</h2>

```
Uniform use of English writing Comments.
统一使用英语书写注释。
Never describe the code, just tell what you're tying to do.
永远不要描述代码，只讲你要做什么。
```
If you think comments is too abstract(not easy to understand), give an example. 如果你认为注释太抽象(不易理解)，则给出一个实例。
<h3 id='3.1'>3.1 Document Strings 文档字符串</h3>

```
This applies to Modules(part), Functions and Methods, Classes.
这适用于模块(一部分)，函数和方法，类。
```
__The document strings start and end with three quotes. A doc string is a string that is the first statement in a module, class or function.__ These strings can be extracted automatically through the \_\_doc__ member of the object and are used by pydoc. <strong>文档字符串使用三个引号来开始和结束。文档字符串是模块, 类或函数里的第一个语句。</strong>这些字符串可以通过对象的__doc__成员被自动提取, 并且被pydoc所用。
<h4 id='3.1.1'>3.1.1 Modules(part) 模块(一部分)</h4>

```
Briefly explain its purpose.
简要说明其用途。
```
```python
"""Use spectral clustering analysis for geographic network data.
"""
# other comment of module.Do not confuse it with document strings.
```

<h4 id='3.1.2'>3.1.2 Functions and Methods 函数和方法</h4>

<em>As used in this section "function" applies to methods, function, and generators. 本节下文所指的函数,包括函数, 方法, 以及生成器.</em>
```
A docstring describes the function's calling syntax and its semantics, not its implementation.
文档字符串描述函数的调用语法及其语义，而不是其实现。
```
<strong>Certain aspects of a function were documented in special sections, listed below. Each section begins with a heading line, which ends with a colon. Sections were indented 4 spaces, except for the heading. Use one blank line between different sections. 关于函数的几个方面要在下面列出的特定小节中进行描述。 每节以标题行开头，标题行以冒号结尾。 除了标题外，每节缩进四个空格。不同节之间间隔一个空行。</strong>

__Args:__
+ List each parameter by name. A description follow the name, and be separated by a colon and a space. 按名称列出每个参数。参数名后紧跟描述，(这二者)使用冒号和空格进行分割。
+ The description mention required type(s) and the meaning of the argument. The meaning of the argument was written in a new line(use 4 paces to indent, do not need to align with the first character of argument's type). 描述必须包含参数类型和参数含义。参数含义要写在新的一行(使用4个空格的悬挂缩进，不需要和参数类型的第一个字符对齐)。
+ If the argument has default value, list the default value on the type line of the argument. 如果参数具有缺省值，则应将它们在参数类型那一行列出。

__Returns: (or Yields: for generators)__
+ Describe the type and semantics of the return value. If the function only returns None, this section is not required. 描述返回值的类型和含义. 如果函数返回None, 则可略去。
+ The semantics of the return value was written in a new line(use 4 paces to indent). 返回值含义写在新的一行上(使用4个空格来缩进)。

__References(if have):__
+ Just list the main references. References have an order number. 只列出主要参考文献。参看文献应当有序号。
+ References have three little sections and use vertical alignment between different little sections. Use the comma to separate different items in the same little section. 参考文献应该具有三小节并在不同小节之间使用垂直对齐。使用逗号分隔同一小节中的不同项。
  1. The first little section list the title and time. 第一小节列出标题和时间。
  2. The second little section list the authors. 第二小节列出作者。
  3. The last little section list the internet connection. 第三小节列出网络链接。

<em>Note: A row over 80 characters in comment(except URLs) were divided into multiple rows and used vertical alignment between this divided rows). 注意：下文中超过80个字符的一句话被分割为了多行并在这些行之间使用了垂直对齐。</em>
```python
def discretize(vectors, copy=True, max_svd_restarts=30, n_iter_max=20,
               random_state=None):
    """Search for a partition matrix (clustering) which is closest to the
    eigenvector embedding.

    Args:
        vectors: array-like, shape: (n_samples, n_clusters)
            The embedding space of the samples.
        copy: boolean, optional, default: True
            Whether to copy vectors, or perform in-place normalization.
        ...

    Returns:
        labels: array of integers, shape: n_samples.
            The labels of the clusters.

    References:
        1. Multiclass spectral clustering, 2003
           Stella X. Yu, Jianbo Shi
           http://www1.icsi.berkeley.edu/~stellayu/publication/doc/2003kwayICCV.pdf
    """

    pass
```

<h4 id='3.1.3'>3.1.3 Classes 类</h4>

```
Classes must have a doc string below the class definition describing the class.
类必须在其定义下有一个用于描述该类的文档字符串.
```
If your class has public attributes or/and references, they need to be documented here in an Attributes section or/and References section following the same formatting as a function's Args section and References section. 如果你的类有公共属性(Attributes)或/和参考文献, 那么文档中要有一个属性(Attributes)节或/和参考文献节，(它们)遵守与函数的参数节和参考文献节相同的格式。
```python
class SpectralClustering(BaseEstimator, ClusterMixin):
    """Apply clustering to a projection to the normalized laplacian.
    ...

    Attributes:
        affinity_matrix_: array-like, shape (n_samples, n_samples)
            Affinity matrix used for clustering. Available only if after calling
            ``fit``.
        ...

    References:
        1. Normalized cuts and image segmentation, 2000
           Jianbo Shi, Jitendra Malik
           http://citeseer.ist.psu.edu/viewdoc/summary?doi=10.1.1.160.2324
        2. A Tutorial on Spectral Clustering, 2007
           Ulrike von Luxburg
           http://citeseerx.ist.psu.edu/viewdoc/summary?doi=10.1.1.165.9323
        ...
    """

    pass
```

<h3 id='3.2'>3.2 Block Comments 块注释</h3>

```
This applies to modules(other parts), complicated operations.
这适用于模块(其余部分)，复杂操作。
```
<h4 id='3.2.1'>3.2.1 Modules(other parts) 模块(其余部分)</h4>

```
After the document strings of modules, write Author and License section.
在文档字符串之后，写作者和许可节。
```
<em>If the module have more than one author, they need be vertically aligned. 如果模块有超过一个作者，则他们要垂直对齐。</em>
```python
"""document strings
"""
# Author: Gael Varoquaux gael.varoquaux@normalesup.org
#         Brian Cheung
#         Wei LI <kuantkid@gmail.com>
# License: BSD 3 clause

pass
```

<h4 id='3.2.2'>3.2.2 Complicated Operations 复杂操作</h4>

```
Complicated operations get a few lines of comments(align vertically) before the operations commence.
复杂操作在其实现开始之前写若干行注释(垂直对齐)。
```
```python
# Normalize the rows of the eigenvectors.  Samples should lie on the unit
# hypersphere centered at the origin.  This transforms the samples in the
# embedding space to the space of partition matrices.
vectors = vectors / np.sqrt((vectors ** 2).sum(axis=1))[:, np.newaxis]

pass
```

<h3 id='3.3'>3.3 Inline Comments 行注释</h3>

```
Inline comments are at the end of the code's line.
行注释位于代码行的末尾。
Two spaces between code and inline comments.
代码和行注释之间间隔两个空格。
```
+ The Non-obvious ones code (or you think necessary) get a inline comments. 非显而易见(或你认为有必要)的代码可以写行注释。
+ Unless necessary, Global variables and constants generally do not have inline comments. 除非必要，一般全局变量和常量不写行注释。
<em>Global variables and constants of this section means the variables and constants which were located outside any classes and functions. 此处的全局变量和常量指代位于任何类和函数之外的变量和常。</em>
  ```python
  ...
  PI = 3.141592654
  ...
  if i & (i-1) == 0:  # true if i is a power of 2
      pass
  ```
<br>

<h2 id='4'>4 Imports Formatting 导入格式</h2>

```
Imports were be on separate lines.
每个导入应该单独占一行。
Imports are put at the top of the file, after the comments of module and before module globals and constants.
导入文件位于模块注释之后，模块全局变量与全局常量之前。
```
<em>If you import more than one contents from same package/module, they can be written on the same line.  导入同一个package/module中的不同内容时可以写在同一行。</em>
+ Do not use relative names in imports and appear cyclic import. 不要在导入时使用相对命名和出现循环导入。
+ A standard import should: 一个标准导入应该：
  1. use import x for importing packages and modules. 导入包和模块时使用import x。
  2. use from x import y (as z) where x is the package prefix and y is the module name with no prefix. 使用from x import y (as z) 当x是包前缀而y是模块名(不带前缀)。
+ Imports need to be grouped with the order being most generic to least generic: 导入要按照最常用到最不常用的顺序分组：
  1. standard library imports 标准库导入
  2. third-party imports 第三方库导入
  3. application-specific imports 应用程序(本项目的package/module)导入

  Within each grouping, imports need to be sorted lexicographically, ignoring case, according to each module's full package path. 在每个分组内，要根据每个模块的完整包路径按字典序排序, 忽略大小写。<br>
  One blank line between different groups. 不同组之间间隔一行。

  ```python
  # module comments

  import warnings

  import numpy as np

  from ..base import BaseEstimator, ClusterMixin
  from ..metrics.pairwise import pairwise_kernels
  ...

  # global variables and constants of module.
  pass
  ```
<br>

<h2 id='5'>5 Indentation 缩进</h2>

```
Indent python code blocks with 4 spaces.
使用四个空格来缩进代码。
```
<strong>Never use tabs or mix tabs and spaces. 永远不要使用tab或者混合使用tab和空格(缩进时)。</strong><br>
Align wrapped elements vertically for line continuation. 行连接使用垂直对齐。
```python
x = ('This will build a very long long '
     'long long long long long long string')
```
<br>

<h2 id='6'>6 Blank Lines 空行</h2>

```
Two blank lines between top-level definitions, one blank line between method definitions.
顶级定义之间空两行, 方法定义之间空一行。
```
+ Two blank lines between top-level definitions, be they function or class definitions. 函数和类(顶级定义)的顶上空两行。
+ One blank line between method definitions and between the class line and the first method. 类的方法之间，类定义和第一个方法之间空一行。
+ One blank line between Logically independent paragraphs within the function. 函数内逻辑无关的段落之间空一行。
+ The blank line within imports can be found in section 4 (Imports Formatting). 导入部分的空行格式参见第四节(导入格式)。
+ Use single blank lines as you judge appropriate within functions or methods, but do not over-use blank lines. 在函数或方法中你认为合适的地方使用一个空行，但不要过度使用空行。

  ```python
  # module comments

  import warnings

  import scipy.sparse as sp

  from ..base import BaseEstimator, ClusterMixin, TransformerMixin
  ...


  def _k_init(X, n_clusters, x_squared_norms, random_state, n_local_trials=None):
      """function comments(document strings)
      """

      n_samples, n_features = X.shape
      centers = np.empty((n_clusters, n_features), dtype=X.dtype)

      assert x_squared_norms is not None, 'x_squared_norms None in _k_init'
      ...

      # Pick first center randomly
      center_id = random_state.randint(n_samples)
      ...

  return centers


  def _validate_center_shape(X, n_centers, centers):
      ...


  pass
  ```
<br>

<h2 id='7'>7 Punctuation and Whitespace 标点和空格</h2>

1. Do not terminate your lines with semi-colons and do not use semi-colons to put two commands on the same line. 不要在行尾使用分号，也不要用分号将两条命令放在同一行。

2. No whitespace inside parentheses, brackets or braces. No whitespace before the open paren/bracket that starts an argument list, indexing or slicing. 在所有的括号内不要有空格，在参数列表，索引或者切片的左括号前不应加空格。
    ```python
    Yes: spam(ham[1], {eggs: 2}, [])
         spam(1)
         dict['key'] = list[index]
    ```
    ```python
    No: spam(ham[1], {eggs: 2}, [])
        spam (1)
        dict ['key'] = list [index]
    ```
    ```python
    Yes: spam(1)
         dict['key'] = list[index]
    ```
    ```python
    No: spam (1)
        dict ['key'] = list [index]
    ```
    <em>Do not use parentheses in return statements or conditional statements unless using parentheses for implied line continuation. (See above.) It is however fine to use parentheses around tuples. 除非用于行连接，否则不要在返回语句或条件语句中使用括号。但可以在元组两边使用括号。</em>
    ```python
    Yes: if foo:
             bar()
         while x:
             x = bar()
         if x and y:
             bar()
         if not x:
             bar()
         return foo
         for (x, y) in dict.items(): ...
    ```
    ```python
    No:  if (x):
             bar()
         if not(x):
             bar()
         return (foo)
    ```

3. Do use (a) whitespace after(not before) a comma, semicolon, or colon except at the end of the line. 在逗号，分号或者冒号之后(不是之前)使用(一个)空格。
    ```python
    Yes: if x == 4:
             print x, y
         x, y = y, x
    ```
    ```python
    No:  if x == 4 :
             print x , y
         x , y = y , x
    ```

4. Arithmetic operators and surround binary operators (assignment, comparisons, and Booleans.) with a single space on either side. 算术操作符和二元操作符(赋值，比较和布尔)两边加一个空格。
    ```python
    Yes: x == 1
    ```
    ```python
    No:  x<1
    ```
    <em>Don't use spaces around the '=' sign when used to indicate a keyword argument or a default parameter value. ’=’用于指示关键字参数或默认参数值时, 不要在其两侧使用空格.</em>
    ```python
    Yes: def complex(real, imag=0.0): return magic(r=real, i=imag)
    ```
    ```python
    No:  def complex(real, imag = 0.0): return magic(r = real, i = imag)
    ```

5. Don't use spaces to vertically align tokens on consecutive lines, since it becomes a maintenance burden (applies to :, #, =, etc.). 不要使用空格来垂直对齐多行间标记, 因为这会成为维护的负担(适用于:, #, =等)。
    ```python
    Yes: foo = 1000  # comment
         long_name = 2  # comment that should not be aligned

         dictionary = {
             "foo": 1,
             "long_name": 2,
             }
    ```
    ```python
    No:  foo       = 1000  # comment
         long_name = 2     # comment that should not be aligned

         dictionary = {
             "foo"      : 1,
             "long_name": 2,
             }
    ```

6. Use ' as the string quote character, but it's okay to use the " on a string to avoid the need to \ escape within the string. 字符串y引号使用单引号，但是字符串内可以使用双引号以避免在字符串中使用转义字符。
    ```python
    Guide('You have reached the "died line".')
    ```
