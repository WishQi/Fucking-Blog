# Fucking Python "import"

本篇文章参考以下两篇文章，翻译加上自己的理解：

<https://stackoverflow.com/questions/419163/what-does-if-name-main-do>

<https://realpython.com/absolute-vs-relative-python-imports/>

--------

如果大家写过`python`代码，那么你大概率使用过`import`这个关键字，它是用来进行模块管理的。当你在一开始学习python的时候，这个时候一切还没完美，这里只有一个.py文件，你可能只会用到python的内置模块，`import`显得那么的简单自然。但是，事情的发展总是不尽人意。当你最初的那个`py`文件中的功能越来越多，按照功能模块拆分到不同的文件或者文件夹中变成了一件势在必行的事情。这个时候，`import`就成了一件然人非常疑惑的事情。具体的场景会有以下几种：

1. 一个空的`__init__.py`文件究竟有何作用，为什么有了它之后，一个“文件夹”就可以被`import`了
2. 当我在执行某一个`python`脚本的时候，`import`会执行失败，但是当这个项目作为整体运行时，一切却运行良好
3. 什么时候应该使用绝对路径引用，什么时候又应该使用相对路径引用，他们之间的区别是什么

本文主要解答上面这三个疑惑。

## `module`和`package`

在`python`中，一个以`py`作为后缀的文件，就是一个`module`。在`python2`中，一个带`__init__.py`文件的文件夹就是一个`package`；而在`python3`中，一个文件夹中如果有`module`，那么这个文件夹就是一个`package`，而不要求必须有`__init__.py`文件。

在`python`中，`module`和`package`都是可以被引用的，也就是`import`关键字后可以跟`module`或者`package`。