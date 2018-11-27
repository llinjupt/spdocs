.. _my-reference-label:

基本语法
=============

指令(Directives)
-----------------
这里的指令是指 *RST* 语言定义的指示如何生成目标文件的命令定义格式。Sphinx对它进行了扩展。

指令的语法如下，它由 *".." + "Space" + "指令类型" + "::" + "Space" + "指令块"* 构成。

*RST* 语言对空格和空行的使用具有严格的定义，它们是指令的一部分，需要注意。

- "." 是指英文的句号.
- "Sapce" 是指一个空格.
- ":" 是英文的冒号.

.. code-block:: none
  :linenos:
  :lineno-start: 0

  +-------+-------------------------------+
  | ".. " | directive type "::" directive |
  +-------+ block                         |
          |                               |
          +-------------------------------+

指令块包含三部分，对于不同的指令，它们可能是强制的，也可能是可选的：

- 指令参数 (Directive arguments).
- 指令选项 (Directive options).
- 指令所作用的内容 (Directive content).

以 *image* 指令为例，它支持一个参数，且是必须的(required)。选项是可选的，不需要指令内容。

.. code-block:: none
  :linenos:
  :lineno-start: 0

  Directive Arguments: One, required (image URI).
  Directive Options: Possible.
  Directive Content: None.

*image* 指令示例：

.. code-block:: none
  :linenos:
  :lineno-start: 0
  
  .. image:: picture.jpeg
     :height: 100px
     :width: 200 px
     :scale: 50 %
     :alt: alternate text
     :align: right
     :target: www.xxx.xx

段落(Paragraphs)
-----------------
段落是文章的基本组成单位，分段不需要任何标记的帮助，空行分割不同的段落。例如：

这是第一个段落。

前边有空行，所以这里是第二个段落。

.. code-block:: none
  :linenos:
  :lineno-start: 0

  这是第一个段落。尽管进行了换行，该行依然属于第一个段落。

  前边有空行，所以这里是第二个段落。

行内标记
-----------------
- 强调，使用一个星号，显示为斜体：*emphasis* 
- 加强，使用两个星号，显示为粗体： **strong**
- 代码示例，使用两个反引号：``literal`` 
- 下标显示：H\ :sub:`2`\ O
- 上标显示：E = mc\ :sup:`2`

.. code-block:: none
  :linenos:
  :lineno-start: 0

  - 强调，使用一个星号，显示为斜体：*emphasis* 
  - 加强，使用两个星号，显示为粗体： **strong**
  - 代码示例，使用两个反引号：``literal`` 
  - 下标显示：H\ :sub:`2`\ O
  - 上标显示：E = mc\ :sup:`2`

RST 不可同时支持斜体和加粗特定，这是它的一个小缺陷。

如果文本部分包含标记所使用的标记字符，则需要加反斜杠进行转义：

转义显示：\*text\* 

.. code-block:: none
  :linenos:
  :lineno-start: 0
  
  转义显示：\*text\* 

硬换行
-------

有些编辑器支持换行显示，尽管文本还在同一行，但是编辑时可以换行显示，但是有些编辑器不支持，为何在书写时把一个长行方便的显示出来，需要硬换行。在行尾添加 “\\” 既可实现硬换行，它们被解析时，作为一行对待。

如果不使用硬换行符，而输入回车换行，那么换行符会生成一个空格。

不必说碧绿的菜畦，光滑的石井栏，高大的皂荚树，紫红的桑葚；也不必说鸣蝉在树叶里长吟，\
肥胖的黄蜂伏在菜花上，轻捷的叫天子(云雀)忽然从草间直窜向云霄里去了。单是周围的短短的泥\
墙根一带，就有无限趣味。油蛉在这里低唱，蟋蟀们在这里弹琴。翻开断砖来，有时会遇见蜈蚣；还\
有斑蝥，倘若用手指按住它的脊梁，便会啪的一声，从后窍喷出一阵烟雾。

.. code-block:: none
  :linenos:
  :lineno-start: 0

  不必说碧绿的菜畦，光滑的石井栏，高大的皂荚树，紫红的桑葚；也不必说鸣蝉在树叶里长吟，\
  肥胖的黄蜂伏在菜花上，轻捷的叫天子(云雀)忽然从草间直窜向云霄里去了。单是周围的短短的泥\
  墙根一带，就有无限趣味。油蛉在这里低唱，蟋蟀们在这里弹琴。翻开断砖来，有时会遇见蜈蚣；还\
  有斑蝥，倘若用手指按住它的脊梁，便会啪的一声，从后窍喷出一阵烟雾。


居中显示
-------------
.. centered:: LICENSE AGREEMENT

.. code-block:: none
  :linenos:
  :lineno-start: 0
  
  .. centered:: LICENSE AGREEMENT

列表
-----------------------

无序列表(Bullet lists)
~~~~~~~~~~~~~~~~~~~~~~
以"*", "+", "-", "•", "‣",或"⁃"加空格开头，具有相同缩进的行作为列表处理。通常使用"-"。

- 列表表项1
- 列表表项2
- 列表表项3

.. code-block:: none
  :linenos:
  :lineno-start: 0
  
  - 列表表项1
  - 列表表项2
  - 列表表项3

列表可以通过缩进进行嵌套，注意子项前必须留有空行：

- 列表表项1

  - 子表项1
  - 子表项2

.. code-block:: none
  :linenos:
  :lineno-start: 0

  - 列表表项1

    - 子表项1
    - 子表项2  

枚举列表(Enumerated lists)
~~~~~~~~~~~~~~~~~~~~~~~~~~
枚举列表可以给表项进行编序，有下几种序号格式：

- 阿拉伯数字：1，2，3，...
- 大写字母：A，B，C，...
- 小写字母：a，b，c，...
- 大写罗马数字：I, II, III, IV, ...
- 小写罗马数字：i, ii, iii, iv, ...

a. 列表表项1
b. 列表表项2

.. code-block:: none
  :linenos:
  :lineno-start: 0

  a. 列表表项1
  b. 列表表项2

可以使用"#"号实现自动编序。

a. 列表表项1
#. 列表表项2

.. code-block:: none
  :linenos:
  :lineno-start: 0

  a. 列表表项1
  #. 列表表项2

自动编序支持以下几种格式的前缀:

- 普通前缀: "1.", "A.", "a.", "I.", "i."
- 带小括号的前缀: "(1)", "(A)", "(a)", "(I)", "(i)"
- 带右括号的前缀: "1)", "A)", "a)", "I)", "i)"

列表项多列显示
~~~~~~~~~~~~~~~~~~~~~~
多列显示，只支持无序表(Bullet Lists)。

.. hlist::
  :columns: 2
  
  - 列表表项1
  - 列表表项2
  - 列表表项3
  - 列表表项4
   
.. code-block:: none
  :linenos:
  :lineno-start: 0
  
  .. hlist::
    :columns: 2
    - 列表表项1
    - 列表表项2
    - 列表表项3
    - 列表表项4

链接
----------
超链接
~~~~~~~~~~~
嵌入外部超链接则无需任何标记，例如：

使用 `百度 <http://www.baidu.com/>`_ 可以访问百度主页，注意空格。
这是另一种方式，来显示超链接 `百度`_ 。第二种方式一次定义可多处引用。

.. _a 百度: http://www.baidu.com/
  
.. code-block:: none
  :linenos:
  :lineno-start: 0

  使用 `百度 <http://www.baidu.com/>`_ 可以访问百度主页。注意空格。
  这是另一种方式，来显示超链接 `百度`_ 。第二种方式一次定义可多处引用。
  
  .. _a 百度: http://www.baidu.com/

内部链接
~~~~~~~~~~
内部链接，由sphnix提供的 `:ref:` 定义引用标签，标签必须位于章节之前。然后在其他地方引用。

内部链接 :ref:`my-reference-label`.

.. code-block:: none
  :linenos:
  :lineno-start: 0

  .. _my-reference-label:
  内部链接 :ref:`my-reference-label`.

脚注和引用
----------------

脚注(Footnotes)
~~~~~~~~~~~~~~~~~~~~
[#]_ 参考脚注1, [#]_ 参考脚注2，[3]_ 参考脚注3，可以直接填入数字，也可以使用"#"自动为脚注编序。

.. [#] 这是脚注1.
.. [#] 这是脚注2.
.. [3] 这是脚注3.

.. code-block:: none
  :linenos:
  :lineno-start: 0

  [#]_ 参考脚注1, [#]_ 参考脚注2.

  .. [#] 这是脚注1.
  .. [#] 这是脚注2.
  .. [3] 这是脚注3.  

引用(Citations)
~~~~~~~~~~~~~~~~~
与脚注类似，可以全局使用，只需直接使用引用的名字：

引用参考的内容通常放在页面结尾处，比如 [One]_，[Two]_

.. [One] 参考引用一
.. [Two] 参考引用二

.. code-block:: none
  :linenos:
  :lineno-start: 0

  引用参考的内容通常放在页面结尾处，比如 [One]_，[Two]_

  .. [One] 参考引用一
  .. [Two] 参考引用二

引用图片
~~~~~~~~~~~
可以引用本地图片，也可以指定图片的URL。

.. image:: _static/test.png
  :alt: test png image
  
.. code-block:: none
  :linenos:
  :lineno-start: 0

  .. image:: _static/test.png
  
图片也可以指向超链接：

.. image:: _static/test.png
  :target: http://www.baidu.com
  
.. code-block:: none
  :linenos:
  :lineno-start: 0

  .. image:: _static/test.png
    :target: http://www.baidu.com
    
image 指令不能定义标题。如果需要请使用 figure 指令。 

注释(Comments)
--------------
以 ``..`` 加空格开始的行以及相同缩进的行均认为是注释：

.. 这句话是注释
..
  相同缩进的注释的第一句.
  
  此句也是注释.

.. code-block:: none
  :linenos:
  :lineno-start: 0

  .. 这句话是注释
  ..
    相同缩进的注释的第一句.
  
    此句也是注释.

提示(Admonitions)
----------------------------
用一段话进行提示，告警等。支持的提示类型有：

.. hlist::
  :columns: 3
  
  - attention
  - caution
  - danger
  - error
  - hint
  - important
  - note
  - tip
  - warning

.. note::
  这里书写提示信息。

.. warning::
  这里书写警告信息。  

.. admonition:: 自定义

   自定义消息提示。

.. code-block:: none
  :linenos:
  :lineno-start: 0

  .. note::
    这里书写提示信息。
  
  .. warning::
    这里书写警告信息。  
  
  .. admonition:: 自定义

    自定义消息提示。

术语表(Glossary)
----------------
术语可以有多个名称，对应一条解释。

.. glossary::

   术语
      这里是对术语的解释说明。

   DNA
   脱氧核糖核酸
      脱氧核糖核酸又称去氧核糖核酸，是一种生物大分子，可组成遗传指令，引导生物发育与生命机能运作。

.. code-block:: none
  :linenos:
  :lineno-start: 0

  .. glossary::
  
     术语
        这里是对术语的解释说明。
  
     DNA
     脱氧核糖核酸
        脱氧核糖核酸又称去氧核糖核酸，是一种生物大分子，可组成遗传指令，
        引导生物发育与生命机能运作。


参见(Reference)
----------------
参见信息应该是类似术语表中定义列表的格式。

.. seealso::

  条目A
    对条目A的信息说明。

.. code-block:: none
  :linenos:
  :lineno-start: 0
  
  .. seealso::

    条目A
      对条目A的信息说明。


代用(Substitutions)
-------------------
代用类似 C 语言中的宏定义，可以对代用符号进行全局替换。

这里的代用符号 |name| 将被替换为中文名称。

这里的代用符号 |caution| 将被替换为图片。

.. |name| replace:: 名称
.. |caution| image:: _static/warning.png

.. code-block:: none
  :linenos:
  :lineno-start: 0

  这里的代用符号 |name| 将被替换为中文名称。
  
  这里的代用符号 |caution| 将被替换为图片。
  
  .. |name| replace:: 名称
  .. |caution| image:: _static/warning.png
