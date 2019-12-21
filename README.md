
.. image:: https://img.shields.io/travis/shedskin/shedskin.svg
    :target: https://travis-ci.org/shedskin/shedskin
.. image:: http://img.shields.io/badge/benchmarked%20by-asv-green.svg?style=flat
    :target: http://shedskin.github.io/benchmarks

Shed Skin
=========



实际上告诉你的那个人听的可能是PyPy里的RPython可以被译（Translate）成C，这的确是可行的，而且也是目前唯一可用的Backend。曾经也使用过LLVM作为Backend（Frequently Asked Questions）但似乎没成功过。
注：RPython不是Python，只是一个子集。

[RPython的GenC源码：https://bitbucket.org/pypy/pypy/src/default/rpython/translator/c/](RPython的GenC源码：https://bitbucket.org/pypy/pypy/src/default/rpython/translator/c/
)

关于把Python译成C的问题，当然理论上是可行的，但是真要把一门动态解析的语言翻译成一门静态编译的语言，难度颇大。

类似的项目有:

[Py2C](https://github.com/Ewenwan/Py2C)

[shedskin]()

[Cython](https://github.com/cython/cython)



## 优化Python程序执行效率的工具？

### Psyco:

是一个PVM的增强工具，这个工具收集并使用信息，在程序运行时，可以将部分程序的字节码转换成底层的真正的二进制机器代码，从而实现更快的执行速度。在理想的情况下，一些通过Pysco优化的Python代码的执行速度可以像编译好的C代码一样快。所有Pysco往往被看做是一个即时编译器(JIT)。

### Shedskin C++转换器:

Shedskin是一个引擎系统，它尝试将Python代码变为C++代码，然后使用机器中的C++编译器将得到的C++代码编译为机器代码。


Shed Skin is an experimental compiler, that can translate pure, but implicitly statically typed Python (2.4-2.6) programs into optimized C++. It can generate stand-alone programs or extension modules that can be imported and used in larger Python programs.

Besides the typing restriction, programs cannot freely use the Python standard library (although about 25 common modules, such as random and re, are currently supported). Also, not all Python features, such as nested functions and variable numbers of arguments, are supported (see the `documentation <https://shedskin.readthedocs.io/>`_ for details).

For a set of `75 non-trivial programs <https://github.com/shedskin/shedskin/releases/download/v0.9.4/shedskin-examples-0.9.4.tgz>`_ (at over 25,000 lines in total (sloccount)), measurements show a typical speedup of 2-200 times over CPython.

The following people have contributed to Shed Skin development so far:

  Hakan Ardo, Brian Blais, Paul Boddie, François Boutines, Djamel Cherif, James Coughlan, Mark Dewing, Mark Dufour, Artem Egorkine, Michael Elkins, Moataz Elmasry, Enzo Erbano, Ernesto Ferro, Salvatore Ferro, FFAO, Victor Garcia, Luis M. Gonzales, Fahrzin Hemmati, Karel Heyse, Kousuke, Denis de Leeuw Duarte, Van Lindberg, David Marek, Douglas McNeil, Andy Miller, Jeff Miller, Danny Milosavljevic, Joaquin Abian Monux, John Nagle, Harri Pasanen, Brent Pedersen, Joris van Rantwijk, Pierre-Marie de Rodat, Jérémie Roquet, Mike Schrick, SirNotAppearingInThisTutorial, Thomas Spura, Joerg Stippa, Dave Tweed, Jaroslaw Tworek, Tony Veijalainen, Pavel Vinogradov, Jason Ye, Liu Zhenhai, Joris van Zwieten

Installation
------------

::

  sudo python setup.py install
  shedskin test.py
  make
  ./test

Documentation
-------------

See: https://shedskin.readthedocs.io/
