Sphinx的基本使用
============================

安装python3
----------------------------

windows直接到python官网下载安装

安装sphinx
----------------------------

windows下使用如下指令安装：

.. code-block:: shell
    :linenos:

    pip install sphinx
    #国内用户推荐使用清华源安装，使用-i指定源
    py -3 -m pip install -i https://pypi.tuna.tsinghua.edu.cn/simple sphinx


使用模板创建sphinx文档
----------------------------

本项目的sphinx已适配好支持markdown、默认的readthedoc主题等内容。

如果是要编写新的书籍，推荐直接使用本项目文档作为模版，修改conf.py文件的配置即可改变项目的名字、主题之类的内容。

文档集的根目录叫 source directory. 该目录也包含了 Sphinx 的配置文件 conf.py, 在这里你可以配置Sphinx各个方面，使Sphinx按照你的要求读取源文件并创建文档. 

Sphinx 有个脚本叫做 sphinx-quickstart ,它可以帮你建立源目录及默认配置文件 conf.py ，它通过几个简单的问题获取一些有用的配置值. 你仅需要运行

.. code-block:: shell
    :linenos:

    sphinx-quickstart


定义文档结构
----------------------------

假定你已经运行了 sphinx-quickstart . 它创建了源目录，包含 **conf.py** 及一份主文档 **index.rst** (如果你接受了默认选项).主文档 master document 的主要功能是被 转换成欢迎页, 它包含一个目录表（ “table of contents tree”或者 toctree ). Sphinx 主要功能是使用 reStructuredText, 把许多文件组织成一份结构合理的文档.

toctree 指令初始为空, 如下:

.. code-block:: rst
    :linenos:

    .. toctree::
        :maxdepth: 2

你可以在 content 的位置添加文档列表:

.. code-block:: rst
    :linenos:

    .. toctree::
        :maxdepth: 2

        intro
        tutorial
        ...


reStructuredText 导读

- toctree 是 reStructuredText的 directive （指令）, 一种用途十分广泛的块标记. 定义了参数、选项及目录.

- Arguments 直接在双冒号后面给出指令的名字. 每个指令都有不定个数的参数.

- Options 在参数后以”字段列表”的形式给出. 如 maxdepth 是 toctree 指令的选项之一.

- Content 具体内容,在选项或参数的后面，隔开一个空行. 每个指令后面都跟着不同作用的内容.

- 共同的约定是 内容与选项一般有相同的缩进 .


运行创建工具
----------------------------

现在已经添加了一些文件,下面可以创建文档了. 创建工具 sphinx-build , 使用方式

.. code-block:: shell
    :linenos:

    sphinx-build -b html sourcedir builddir

sourcedir 是源目录 source directory , builddir 则是放置生成的文档的根目录. -b 是创建工具的选项;这个例子创建HTML文件.
而且, sphinx-quickstart 脚本创建的 Makefile 和
make.bat 使操作更容易，仅需运行

.. code-block:: shell
    :linenos:

    make html

创建 HTML 在设定好的目录里. 执行 make 将不需要任何参数.
完成创建后将会在 build 目录下生成一个 html 目录.