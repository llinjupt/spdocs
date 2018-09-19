进阶应用
==========

表格
----------
Sphinx支持两种表格形式：简单表格和对于格子表格。

=====  =====  =======
A      B      A and B
=====  =====  =======
False  False  False
True   False  False
=====  =====  =======

简单表格容易书写，但是有限制：表格必须是两行以及以上，而且第一列不能包含多行。

.. code-block:: none
  :linenos:
  :lineno-start: 0
  
  =====  =====  =======
  A      B      A and B
  =====  =====  =======
  False  False  False
  True   False  False
  =====  =====  =======

网格表格要复杂，可以表示更具弹性的内容：

+------------------------+------------+----------+----------+   
| Header row, column 1   | Header 2   | Header 3 | Header 4 |   
| (header rows optional) |            |          |          |   
+========================+============+==========+==========+   
| body row 1, column 1   | column 2   | column 3 | column 4 |   
+------------------------+------------+----------+----------+   
| body row 2             | Cells may span columns.          |   
+------------------------+------------+---------------------+   
| body row 3             | Cells may  | - Table cells       |   
+------------------------+ span rows. | - contain           |   
| body row 4             |            | - body elements.    |   
+------------------------+------------+---------------------+

.. code-block:: c                                               
    :linenos:
    :lineno-start: 0
    
    +------------------------+------------+----------+----------+   
    | Header row, column 1   | Header 2   | Header 3 | Header 4 |   
    | (header rows optional) |            |          |          |   
    +========================+============+==========+==========+   
    | body row 1, column 1   | column 2   | column 3 | column 4 |   
    +------------------------+------------+----------+----------+   
    | body row 2             | Cells may span columns.          |   
    +------------------------+------------+---------------------+   
    | body row 3             | Cells may  | - Table cells       |   
    +------------------------+ span rows. | - contain           |   
    | body row 4             |            | - body elements.    |   
    +------------------------+------------+---------------------+

引用代码
----------
在文档中列出代码是开发人员经常用到的一个功能。在reST文档中列出代码有三种方式：

行内代码用使用两个反引号，例如 ``code``。

.. code-block:: none                                             
    :linenos:
    :lineno-start: 0
    
    行内代码用 ``code``

简单代码块：在代码块的上一个段落后面加2个冒号，空一行后开始代码块，代码块要缩进：

下面是源码 ::
                                                    
    void foo()                                                  
    {                                                           
        int i;                                                  
                                                                
        for(i=0; i<10; i++)                                     
            printf("i: %d\n", a);                               
    }                                                           

.. code-block:: none                                             
    :linenos:
    :lineno-start: 0
    
    下面是源码 ::
                                                        
        void foo()                                                  
        {                                                           
            int i;                                                  
                                                                    
            for(i=0; i<10; i++)                                     
                printf("i: %d\n", a);                               
        }

复杂代码块 使用code-block指导语句，还可以选择列出行号和高亮重点行等                                            
                                                                
.. code-block:: c                                               
    :linenos:                                                   
    :emphasize-lines: 3,6                                       
                                                                
    void foo()                                                  
    {                                                                                            
      int i;                                                  
                                                              
      for(i=0; i<10; i++)                                     
       printf("i: %d\n", a);                               
    }

.. code-block:: none                                             
    :linenos:
    :lineno-start: 0
    
    .. code-block:: c                                               
      :linenos:                                                   
      :emphasize-lines: 3,6                                       
                                                                
      void foo()                                                  
      {                                                                                            
        int i;                                                  
                                                                
        for(i=0; i<10; i++)                                     
         printf("i: %d\n", a);                               
      }

图片和主题
----------
如果需要围绕图片展开一个主题，那么使用 *figure* 命令是一个很好的选择。
可以方便的为图片加入简洁的文字说明，和详细的图片故事。

.. figure:: _static/namakualan.jpg
  :scale: 80 %
  :align: left
  :alt: Scene of Namaqualand

  美丽的纳马夸兰

  纳马夸兰是最著名的赏花圣地。在春天到来时，这个半沙漠地区忽然魔术般地变成花的海洋，方圆几十公里内全都是番杏科的植物盛开着紫红、金黄、粉红、橘红色的花朵，视野里只有色彩，整个世界中好像只有花存在。

.. code-block:: none
  :linenos:
  :lineno-start: 0
  
  .. figure:: _static/namakualan.jpg
    :scale: 80%
    :align: left
    :alt: Scene of Namaqualand
    
    美丽的纳马夸兰
  
    纳马夸兰是最著名的赏花圣地。在春天到来时,这个半沙漠地区忽然魔术般地变成花的海洋，
    方圆几十公里内全都是番杏科的植物盛开着紫红、金黄、粉红、橘红色的花朵，视野里只有
    色彩，整个世界中好像只有花存在。  

figure指令不支持图片自动编号。Sphinx没有提供该功能，需要自己扩展。

借用Linux内核中的扩展
----------------------
Linux内核中的Documentation部分对Sphinx进项了扩展，提供了更多好用的标签，借用Linux内核来生成自己的文档，效果非常好，它特别针对源码注释生成文档进行了优化。

详细资料参考 `Linux内核中Sphnix的应用 <https://www.kernel.org/doc/html/latest/doc-guide/index.html>`_ 。

在readthedocs中显示
--------------------

https://readthedocs.org 是一个第三方免费的文档托管网站，不仅如此，它可以直接从github等源码服务器上拉取项目，并自动生成html文件方便浏览和外部引用。

有一点要注意：如果文档中含有中文，那么在高级设置中取消生成pdf，否则可能编译不过。

附录
======

参考网站
--------
- Sphinx的中文文档：https://zh-sphinx-doc.readthedocs.io/en/latest/contents.html
- reST: http://docutils.sourceforge.net/rst.html
- Sphinx对reST的扩展： http://www.sphinx-doc.org/en/master/usage/restructuredtext/index.html
- Linux内核中Sphnix的应用：https://www.kernel.org/doc/html/latest/doc-guide/index.html
- readthedocs：https://docs.readthedocs.io/en/latest/