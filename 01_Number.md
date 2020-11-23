## Number

### 1.isNaN

对象调用isNaN方法，会先调用对象的valueOf方法，然后确定返回值是否可以转换成数字值，如果不能在基于返回值调用toString()方法，再测试返回值。

### 2.数值转换

有3个函数可以把非数值转换成数值：`Number()`、`parseInt()`和`parseFloat()`。

> `Number()`可用于任何数据类型。`parseInt`和`parseFloat`专门用于把字符串转换成数值。

#### `2.1 Number()`转型函数的转换规则：

- `Boolean`类型：`true`转换成1；`false`转换成0。
- Number类型：转换前后相同。
- String类型：

> - 如果字符串中只包含数字（包括前面带正负号的情况），则将其转换成十进制数值。（前导0会被忽略）。
> - 如果字符串中为浮点格式，转换成对应浮点数值。（前导0被忽略）
> - 如果字符串中包含有效十六进制格式，如“0xf”，则转换成对应大小的十进制数值。
> - 如果空字符串，则转换成0。
> - 如果字符串中包含除上述格式之外的字符，则结果为NaN。

- null转换成0。
- `undefined`返回`NaN`。
- `Object`类型：先调用对象的`valueOf`方法，然后再依照上面规则转换。如果转换结果为`NaN`，则再调用`toString()`方法，然后再按照上面String类型转换规则转换。

#### `2.2 parseInt(string[,radix])`解析字符串，以指定基数解析返回十进制整数。radix 2-36之间的整数。第一个参数如果不是字符串会自动转换成字符串

参数radix省略:

- 转换字符串时会忽略字符串前面的空格，直到找到第一个非空字符。
  例如：`parseInt("  111"); // 111`

- 如果找到的第一个字符如果不是数字或者正负号就返回`NaN`。
  例如：`parseInt("s11"); // NaN`

  ​			`parseInt("-11"); //-11`

  ​			`parseInt("+123"); // 123`

- 如果找到的第一个字符串为数字或正负号，则继续解析下一个字符直到遇见非数字字符时停止。
  例如：`parseInt("12ss"); // 11`

  ​			`parseInt("12.1234"); // 12` 因为`.`字符非数字，所以`.`及后面的数字并不会取到。

- 处理数值 :

  "0x"解析为十六进制。"010"ES5要求解析为十进制结果为10，ES3解析成八进制结果为8，所以要指定radix参数是必要的。

指定radix参数：

- radix为0、undefined或未指定，他们的行为是一样的。
- 指定的radix如果不在2-36返回NaN。
- 如果参数radix为16，那么`parseInt("AF",16); // 175`。也就是可以省略"0x"。

> 注：为了兼容性，最好全部指定radix参数。

#### `2.3 parseFloat(string)`

`parseFloat`与`parseInt`类似。`parseFloat`第一个有效字符是`数字`或者第`点`或者`正负号`。

没有`.`会解析成解析成整数。`parseFloat(11); // 11` `parseFloat("11."); // 11`。

parseFloat会解析科学计数的值。`parseFloat("12e2"); //1200` 

#### String

###### toString([radix])方法，返回相应值的字符串表现

- null和undefined没有toString方法。

- 如果调用toString是数值，可以指定一个参数，以指定进制的形式返回字符串。

```javascript
var a = 10;
a.toString(2); // "1010"
a.toString(8); // "12"
a.toString(16); // "a" 
```

###### String()转换函数

转换规则：

- 如果有toString方法直接调用进行转换。
- null转换成“null”
- undefined转换成“undefined”

> 要将某个值转换为字符串，可以直接使用加号操作符。+""对应值加空串

#### Object

创建对象：

- 字面量方式
- new Object() ,没有参数可以省略括号，（new Object;） 但是不推荐。
- Objectl类型是所有实例的基础，Object实例具有一下属性方法：
  - constructor构造函数。
  - hasOwnProperty(propertyName)判断实例本身是含有某个属性。
  - propertyIsEnumerable(propertyName)判断属性是否可枚举。
  - isPrototypeOf(obj)判断传入对象是否是实例的原型。
  - toLocaleString
  - toString
  - valueOf

###### 递增递减

前置会等表达式求值之前递增递减。后置会在表达式求值之后递增递减。

对于任何类型的值都可以进行递增或递减操作，

递增递减前，会将值转换成number同转换函数Number()。