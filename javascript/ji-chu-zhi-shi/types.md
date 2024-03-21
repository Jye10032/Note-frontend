# 数据类型

js数据类型有6种：

number

string

boolean

object

function

undefined\


其中number、string、boolean、undefined是值类型，function和object是引用类型。

#### 判断数据类型

typeof和instanceof都是js中用来判断数据类型的方法

* typeof适用于判断数据基本类型的场景，返回结果可能是 `"undefined"`, `"boolean"`, `"number"`, `"string"`, `"object"`, `"function"`, 和 `"symbol"`
* instanceof用来判断对象（包括内置对象和自定义对象）所对应的类的场景，用于检测对象是否是特定类型的实例，返回 true / false

#### null 和 undefined

* `undefined` 表示一个声明了但未被赋值的变量，或者一个不存在的属性或索引。
* 用 `typeof` 运算符检测 `null` 变量的类型会返回 `"object"`，这是一个 JavaScript 设计上的历史错误。
* `null` 表示一个空值或不存在的对象。
