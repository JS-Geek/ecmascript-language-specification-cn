# 4 Overview

本章节是ECMAScript语言的简单概述。

ECMAScript是一门面向对象的语言，它在一个宿主环境中执行计算和操作计算对象。ECMAScript并不打算被定义成一门计算性完备的语言, 而且本规范中也没有给出任何关于外部数据输入和计算结果输出的定义条款。恰恰相反，规范希望ECMAScript语言程序不仅提供规范中描述的对象和功能, 也包含一些和运行环境相关的对象。这些对象的描述和行为不属于本规范的内容，但他们可能会提供一些可以被访问的特殊属性和可以被ECMASCript程序调用的特殊方法。  

ECMAScript原本被设计成一门脚本语言，但现在已经变成了一门广泛使用的通用编程语言。**脚本语言**是用来操作，定制和自动化已有系统功能的编程语言。在这些系统中，功能已经通过用户界面提供了，而脚本语言是一种把这些功能开放给程序控制的机制。因此，已用系统被称为提供对象和功能的宿主环境，这些对象和功能实现了脚本语言的能力。**脚本语言**是用来给专业或非专业的程序员使用的。  

ECMAScript原本被设计成一门**网页脚本语言**，提供一种机制，让浏览器中的网页更加生动和作为基于网页的C/S架构的一部分执行服务器端计算。现在，ECMASCript语言用来在各种宿主环境中提供核心的脚本编程能力。因此，本文档中描述的核心语言并不限定任何一中特定的宿主环境。

ECMAScript的使用已经不仅局限于脚本编程，而且现在已经被广泛用于各种环境和系统规模下的编程工作中。ECMAScript语言的特性和功能随着它的使用范围的扩大而扩展开来。ECMASCript语言现在已经是一门功能齐全的通用编程语言了。  

ECMAScript语言的一些功能和其他语言相似，特别是C，Java<sup>TM</sup>，Self和Scheme，描述如下：

* ISO/IEC 9899:1996, Programming Languages – C
* Gosling, James, Bill Joy and Guy Steele. The Java<sup>TM</sup> Language Specification. Addison Wesley Publishing Co., 1996.* Ungar, David, and Smith, Randall B. Self: The Power of Simplicity. OOPSLA '87 Conference Proceedings, pp. 227–241, Orlando, FL, October 1987.* IEEE Standard for the Scheme Programming Language. IEEE Std 1178-1990.