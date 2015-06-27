# 4.3 Terms and definitions
本文档采用了一下术语和定义：

## 4.3.1 type 类型
规范[条款6](../6_ecmascript_data_types_and_values/index.html)定义数据值的集合。

## 4.3.2 primitive value 简单值
规范[条款6](../6_ecmascript_data_types_and_values/index.html)定义的类型**Undefined**，**Null**，**Boolean**，**Number**，**Symbol**，或**String**的成员

> NOTE 一个简单值直接表示语言实现最底层的数据

## 4.3.3 object 对象
类型**Object**的成员

> NOTE 一个对象是属性的集合，有一个唯一的prototype对象。prototype对象可以是null值。

## 4.3.4 constructor 构造器
创建和初始化对象的函数对象

> NOTE 构造器的*prototype*属性是一个prototype对象，用来实现继承和共享属性。

## 4.3.5 prototype 原型对象
为其他对象提供共享属性的对象 

> NOTE 当一个构造器创建一个对象时，该对象有隐式引用指向构造器的**prototype**属性，用来解析属性引用。构造器的**prototype**属相可以通过程序表达式`constructor.prototype`来引用，添加到对象的prototype上的属性，通过继承，会被所有共享同一个prototype的对象共享。另外，一个新的对象可以通过使用内建函数**Object.create**，显式指定prototype来创建。

## 4.3.6 ordinary object 普通对象
所有对象都支持的必需的内部方法和默认行为一致的对象

## 4.3.7 exotic object 奇异对象
一个或多个所有对象都支持的必需的内部方法和默认行为不一致的对象

## 4.3.8 standard object 标准对象
由本规范定义语义的对象

## 4.3.9 build-in object 内建对象
由ECMAScript实现来指定和提供的对象

> 标准内建对象是在本规范中定义的。一个ECMAScript实现可以指定和提供其他种类的内建对象。一个内建构造器即是一个内建对象，也是一个构造器。

## 4.3.10 undefined value 未定义值
一个简单值，用来表示一个变量还没有被赋值时的值

## 4.3.11 Undefined type 未定义类型
一个类型，它的唯一值是**undefined**

## 4.3.12 null value null值
一个简单值，用来表示对象的值是“无（absence）”

## 4.3.13 Null type Null类型
一个类型，它的唯一值是**null**

## 4.3.14 Boolean value 布尔值
Boolean类型的成员

> NOTE 只有两个布尔值：**true**和**false**

## 4.3.15 Boolean type 布尔类型
由简单值**true**和**false**组成的类型

## 4.3.16 Boolean object 布尔对象
Object类型的成员，是标准内置**Boolean**构造器的实例

> 一个布尔对象通过使用**Boolean**构造器在**new**表达式中创建，提供一个布尔值作为参数。产生的对象有一个内部存储空间（slot），它的值是布尔值。一个布尔对象可以强制转换成一个布尔值。

## 4.3.17 string value 字符串值
表示有限的有序16位无符号整数序列的简单值

> NOTE 一个字符串值是String类型的成员，序列中的每个整数值常常表示为一个16位的UTF-8文本单元。但是，除了要求必须是16位无符号整数外，ECMAScript没有规定任何限制和要求在这些值上。

## 4.3.18 String type 字符串类型
所有字符串值的集合

## 4.3.19 String object 字符串对象
Object类型的成员，是标准内置**String**构造器的实例

> NOTE 一个字符串对象通过使用**String**构造器在**new**表达式中创建，提供一个字符串值作为参数。产生的对象有一个内部存储空间（slot），它的值是字符串值。一个字符串对象可以通过把**String**构造器当成函数来调用，强制转换成字符串值。

## 4.3.20 number value 数字值
表示一个双精度64位二进制格式的IEEE 754-2008值

> NOTE 一个数字值是Number类型的成员，是一个数字的直接表示。

## 4.3.21 number type 数字类型
所有数字值，及特殊值“非数字值（NaN）”，正无限（positive infinity）和负无限（negative infinity）的集合

## 4.3.22 Number object 数字对象
Object类型的成员，是标准内置**Number**构造器的实例

> NOTE 一个数字对象通过使用**Number**构造器在**new**表达式中创建，提供一个数字值作为参数。产生的对象有一个内部存储空间（slot），它的值是数字值。一个数字对象可以通过把**Number**构造器当成函数来调用，强制转换成数字值。

## 4.3.23 Infinity 无限
表示正无限的数字值

## 4.3.24 NaN 非数字值
表示IEEE 754-2008 “Not-a-Number”值的数字值

## 4.3.25 symbol value 符号值
表示一个唯一的，非字符串的Object属性主键（key）的简单值

## 4.3.26 Symbol type 符号类型
所有符号值的集合

## 4.3.27 Symbol object 符号对象
Object类型的成员，是标准内置**Symbol**构造器的实例

## 4.3.28 function 函数
Object类型的成员，可以作为一个子程序被调用

> NOTE 除了属性外，一个函数包含了可运行的代码和决定其被调用时行为的状态。一个函数的代码可以用，也可以不用ECMAScript编写。

## 4.3.29 build-in fucntion 内建函数
内建对象是函数的时，称之为内建函数

> NOTE 内建函数的例子包括**`parseInt`**和**`Math.exp`**。一个ECMAScript语言实现可以提供本规范没有描述的，依赖语言实现的内建函数

## 4.3.30 property 属性
对象中把主键（key，可以是String值或Symbol值）和值关联起来的部分

> NOTE 取决于属性的形式，属性值可以直接地表现为一个的数据值（简单值，对象或函数对象），或间接地表现为一对访问器（accessor）函数。

## 4.3.31 method 方法
作为属性值的函数

> NOTE 当一个函数作为一个对象的方法被调用时，该对象作为该函数的**`this`**值传入。

## 4.3.32 build-in method 内建方法
方法是内建函数时，称之为内建方法

> NOTE 本规范定义了标准内建方法，而一个ECMAScript实现可以定义和提供其他的内建方法。

## 4.3.33 attribute 特性
特性是用来定义属性一些特征的内部值

## 4.3.34 own property 自有属性
对象直接包含的属性称为自有属性

## 4.3.35 inherited property 继承属性
对象的属性不是自有属性，而是对象的prototype上的属性，称之为继承属性