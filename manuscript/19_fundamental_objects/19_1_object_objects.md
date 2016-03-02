# 19.1 Object Objects

## 19.1.1 The Object Constructor

Object的构造器是内部对象%Object%，它是全局对象的**Object**属性的初始值。当作为构造器调用时，它会创建一个全新的普通对象。当**Object**作为一个函数而非构造器调用时，它会执行一个类型转换。  

**Object**构造器被设计成可以被子类化。它可以作为类定义的**extends**从句的值使用。

### 19.1.1.1 Object([ value ])
当**Object**函数和可选的参数*value*一起被调用时，以下步骤依次执行：  

1. 如果NewTarget既不是**undefined**也不是一个有作用的function时，返回 [OrdinaryCreateFromConstructor]()(NewTarget, **"%ObjectPrototype%"**)
2. 如果*value*是**null**，**undefined**或未提供，返回 [ObjectCreate]()(%ObjectPrototype%)
3. 