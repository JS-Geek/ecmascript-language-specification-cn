# 4.2 ECMAScript Overview

接下来是ECMAScript非正式的概述，并没有阐述语言的所有组成。该概述并非标准的组成部分。  

ECMAScript是基于对象的：基本的语言和宿主功能由对象提供，而一个ECMAScript程序是由一组相互通信的对象组成。在ECMAScript中，一个对象是0或多个**属性（properties）**的集合，这些属性具有一些**特性（attributes）**，这些特性决定每个属性如何被使用。例如，当一个属性的Writable特性为false食，ECMAScript代码任何试图设置该属性为一个不同的值的操作都将失败。属性可以是存储其他对象，**简单类型值（primitive values）**和**函数（functions）**的容器。简单类型值是以下内建类型之一的成员：**Undefined**，**Null**，**Boolean**，**Number**，**String**和**Symbol**。对象则是内建类型**Object**的成员；而函数则是一个可以调用的对象。当一个函数作为对象的属性时，被称为**方法（Method）**。  

ECMAScript定义了一系列的内建对象。这些内建对象包括全局（global）对象；还有构成语言运行语义基础的对象，包括**Object**，**Function**，**Boolean**，**Symbol**和各种**Error**对象；还有用来表达和操作数字值的对象，包括**Math**，**Number**，和**Date**；还有文本处理的对象**String**和**RegExp**；用来存储索引集合的对象**Array**，和用来存储九种不同的数字类型的限定类型数组（Typed Array）;基于键（key）的集合有**Map**和**Set**对象；支持结构化数据的对象有**JSON**，**ArrayBuffer**，和**DataView**；支持控制抽象的对象有generator函数和**Promise**对象；以及两种反射对象**Proxy**和**Reflect**。  

ECMAScript也定义了一组内建的**运算符（operators）**。ECMAScript运算符包括各种一元运算符，乘性运算符，加性运算符，按位移动运算符，关系运算符，等性运算符，位运算符，位逻辑运算符，赋值运算符和逗号运算符。  

大型ECMAScript程序由**模块（modules）**组成，模块把程序分隔成多个包含语句和声明的代码序列。每个模块显式地识别其他模块提供给它使用声明，以及它提供给其他模块使用的声明。  

ECMAScript语法有意地模仿Java语法。而它的语法使其成为一门易于使用的脚本语言。例如，变量不需要声明类型，类型也不要声明属性。而在文法上，定义的函数也不需要在调用它之前声明。  

## 4.2.1 Object

虽然ECMAScript提供了class定义的语法，但从根本上说，它的对象不像C++，Smalltalk或Java是基于class的。对象可以使用多种方法创建，包括通过字面量表示法创建，和通过**构造器（constructors）**创建。构造器创建对象，然后运行初始化代码来给赋初始值给对象的属性。每个构造器都是一个函数，它有一个属性叫“**prototype**”，用来实现**基于原型的继承（prototype-based inheritance）**和**共享属性（shared properties）**。在**new**表达式中，使用构造器来创建对象；例如，`new Data(2009, 11)`创建一个新的Date对象。如果不使用**new**来调用构造器，则返回的结果取决于构造器。例如，代码`Date()`会产生一个表示当前日期和时间的字符串而不是Date对象。  

每个通过构造器创建的对象，都有一个隐式引用（被称为对象的prototype）指向构造器的“**prototype**”属性。而且，一个prototype也可能有一个非空（non-null）的隐式引用指向它的prototype，以此类推。这被称为原型链（*prototype chain*）。当引用一个对象上的某个命名属性时，引用将指向原型链上第一个包含该名称属性的对象的对应属性。换句话说，首先，检查对象上是否有同名的属性，如果对象包含同名属性，则引用指向属性；如果对象不包含同名属性，接着检查对象的prototype；以此类推。  
  
￼￼
![Object/Prototype Relationships](res/4_2_figure_1.png)  
**Figure 1 - Object/Prototype Relationships**  

在基于类的面向对象语言中，通常，状态（state）由实例保存，方法由类保存，仅继承数据结构和行为。在ECMAScript中，状态和方法都由对象保存，数据结构、行为和状态都可以继承。  

所有prototype相同的对象自身都不包含某个属性，而它们的prototype包含这个属性时，该属性和属性值会在这些对象间共享。Figure 1图解了这个特性：  

CFi是一个构造器（也是一个对象）。五个对象通过**new**表达式创建：cf1，cf2，cf3，cf4，和cf5。这五个对象都包含名称为q1和q2的属性。虚线表示隐式的prototype关系；例如，cf3的prototype是CF<sub>p</sub>。构造器CF自身有两个属性，名称为P1和P2，这两个属性对CF<sub>p</sub>，cf1，cf2，cf3，cf4或cf5都不可见。CF<sub>p</sub>的属性CFP1被cf1，cf2，cf3，cf4和cf5共享（但CF不会共享），而且所有在CP<sub>p</sub>的隐式原型链上找到的名称不为q1，q2或CFP1属性也会被共享。注意，CF和CF<sub>p</sub>之间没有隐式原型链。  

和绝大多数基于class的对象语言不同，属性可以通过赋值被动态地加到对象上。这意味，构造器不需要命名或赋值给被构造出来对象的所有或某些属性。在以上示意图中，可以通过赋值给CF<sub>p</sub>的属性为cf1，cf2，cf3，cf4和cf5一个共享属性。  

虽然ECMAScript对象本身不是基于class的，但很容易基于一个通用的构造函数，原型对象和方法模式来定义一个类class的抽象。ECMAScript内建的对象本身遵从一个类class的模式。从ECMAScript 2015开始，ECMAScript语言包含了class定义语法，允许程序员遵从和内建对象一样的类class抽象模式来简洁地定义对象。

## 4.2.2 The Strict Variant of ECMAScript

ECMAScript语言意识到有可能一些用户希望限制使用一些语言特性。这些用户可能是基于安全原因这么做，希望避免使用一些他们认为易于犯错的特性，得到增强的错误检查，或是一些其他的原因。为了支持上述场景，ECMAScript定义一个语言的严格变体。语言的严格变体排除了一些标准ECMAScript语言定义的语法和语义特性，并且修改了一个特性的语义。严格变体也定义了附加的错误情况，会通过抛出错误异常的方式来报告这些错误，而这些错误情况在语言非严格模式下并不认为是错误。  

ECMAScript的严格变体通常被称为语言的*严格模式（strict mode）*。严格模式的选择和ECMAScript严格模式语法和语义显式地在独立的ECMAScript代码文本单元的层次中指定。因为严格模式是在语法上的代码文本单元层次中选择的，所以严格模式仅仅把具有局部作用的限制强加在这个代码文本单元。严格模式不会限制或修改需要在多个代码文本单元保持操作一致的ECMAScript语义。一个完整的ECMAScript程序必须包含严格模式和非严格模式的代码文本单元。因此，当在严格模式代码单元中定义的代码被真正运行的时候，严格模式才会生效。  

为了遵守本规范，一个ECMAScript语言实现必须包括完整的不受限制的ECMAScript语言和本规范定义的严格变体。另外，一个语言实现必须支持在一个复合的程序中结合使用不受限的和严格模式的代码文本单元。