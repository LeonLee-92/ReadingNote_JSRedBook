### 数据类型：

> ##### 基本数据类型：Undefined、Null、Boolean、Number和String。
>
> ##### 复杂数据类型：Object

### typeof操作符：

> ##### 负责检测数值类型
>
> ##### 返回："undefined"、"boolean"、"number"、"string"、"object"和"function"。

#### 注意：

> ##### typeof\(null\);
>
> --&gt; object
>
> ##### typeof\(new RegExp\("^\d+$"\)\);
>
> --&gt; object

#### 

### Undefined类型：

> ##### 字面值undefined的主要目的是用于比较
>
> ##### var message;    ==&gt;   var message = undefined;

#### 注意：

```js
var message;
alert(message);
alert(age);  // 报错
```

```js
var message;
alert(typeof(message));
alert(typeof(age));   //  undefined
```

### 

### Null类型：

##### 如果定义的变量准备在将来用于保存对象，那么最好将该变量初始化为null

> ##### 注意：
>
> undefined是派生自null的
>
> ##### alert\(null == undefined\);   --&gt;  true

### 

### Boolean类型:

##### true和false，所有类型的值都有与这两个Boolean值等价的值

> ##### Boolean\(\)函数:
>
> ###### false:  ""  \|  0  \|  NaN   \|  null   \|   undefined
>
> ###### true: 其他所有

### 

### Number类型:

> ##### 八进制：前缀0
>
> ##### 十六进制： 前缀0x

##### 注意：

* 严格模式下，八进制无效。
* 八进制超出数值，按十进制解析：

```js
var num1 = 070;  // 56
var num2 = 079;  // 79
var num3 = 08;   // 8
```

#### 浮点数值：

> ##### 某些情况会解析为整数：
>
> > ```js
> > var floatNum1 = 1.;    // 解析为整数 1
> > var floatNum2 = 10.0;  // 解析为整数 10
> > ```

##### 由于JS的浮点计算，会有精度问题，比如0.1+0.2不等于0.3，所以永远不要测试某个特定的浮点数值

#### 数值范围 和 infinety存储位置：

![](/assets/86048BBD-2F6B-43A4-A548-8503CD443A22.png)

##### ![](/assets/0D4B12C3-22C2-4D33-8758-D66B5BD84AAC.png)

#### 

#### NaN:

##### 用于表示一个本来要返回数值的操作数未返回数值的情况

##### 注意：

> ##### 1.任何涉及NaN的操作（例如NaN/10）都会返回NaN
>
> ```js
> alert(NaN/10);   //NaN
> ```
>
> ##### 2.NaN与任何值都不相等，包括NaN本身。
>
> ```js
> alert(NaN == NaN)； //false
> ```

##### isNaN\(\)

##### ![](/assets/00629.jpg)

##### 注意：

> ##### isNaN\(\)也适用于对象：
>
> 1.首先调用对象的valueOf\(\)方法
>
> 2.基于valueOf\(\)的返回值调用toString\(\)方法

#### 数值转换:

##### Number\(\)

##### 用于任何数据类型，规则如下：

> □　Boolean，转换为1和0。
>
> □　数字值，直接返回。
>
> □　null，返回0。
>
> □　undefined，返回NaN。
>
> □　字符串：
>
> > * 只包含数字（可带符号），转换为十进制数值（前导0将被忽略）
> > * 包含有效的浮点格式，如"1.1"，转换为对应的浮点数值（前导0将被忽略）
> > * 包含有效的十六进制格式，例如"Oxf"，转换为相同大小的十进制整数值；
> > * 空字符串，则将其转换为0；
> > * 其他，转换为NaN。
>
> □　对象：
>
> > * 调用valueOf\(\)方法，然后依照前面的规则转换返回的值。
> > * 如果结果是NaN，调用对象的toString\(\)方法，然后再次依照前面的规则转换返回的字符串值。

##### parseInt\(\)

##### 用于提取字符串中的整数

![](/assets/222.png)

![](/assets/333.png)

##### parseFloat\(\)

##### 用于提取字符串中的浮点数

![](/assets/00653.jpg)

### String类型

#### 性质：JS中字符串是不可变的

![](/assets/00662.jpg)

#### 转换为字符串：

* ###### toString\(\)

> > ![](/assets/555.png)

* ###### String\(\)

> > ![](/assets/String__.png)

* ###### String\(n\)与n+""结果相同

### Object类型：

##### new Object\(\) 具有下列属性和方法:

> * ###### **Constructor**：保存着用于创建当前对象的函数\(构造函数\)。
>
> > > ###### ![](/assets/constructor.png)
>
> * ###### **hasOwnProperty\("xxx"\)**：检查属性在当前对象实例中（而不是在原型中）是否存在。
>
> > > ###### ![](/assets/1212.png)
>
> * ###### **isPrototypeOf\(object\)**：用于检查传入的对象是否是另一个对象的原型。
>
> > > ###### ![](/assets/isproperty.png)
>
> * ###### **propertyIsEnumerable\("xxx"\)**：用于检查给定的属性是否能够使用for-in语句来枚举。
>
> > ###### \*\*通常继承**的属性不是可枚举的，而用户定义的属性总是可枚举的**
> >
> > > ###### ![](/assets/456.png)
>
> * ###### **toLocaleString\(\)**: 返回对象的字符串表示，该字符串与执行环境的地区对应。
>
> > > ###### ![](/assets/0789.png)
> > >
> > > ###### ![](/assets/7seuf87i.png)
>
> * ###### **toString\(\)**：返回对象的字符串表示。
>
> > ###### \*\*不适用于null和undefined
>
> * ###### **valueOf\(\)**：返回对象的字符串、数值或布尔值表示。通常与toString\(\)方法的返回值相同。
>
> > > ###### JS许多内置对象都重写了该函数
> > >
> > > ###### ![](/assets/ejrtgoj.png)
> >
> > ```js
> > // Array：返回数组对象本身
> > var array = ["abc", true, 12, -5];
> > console.log( array.valueOf() === array );     // true
> >
> > // Date：当前时间距1970年1月1日午夜的毫秒数
> > var date = new Date();
> > console.log( date.valueOf() );                 // 1491890449150
> >
> > // Number：返回数字值
> > var num =  15.26540;
> > console.log( num.valueOf() );                 // 15.2654
> >     
> > // 布尔：返回布尔值
> > var bool = true;
> > console.log( bool.valueOf() === bool );         // true
> > // new一个Boolean对象
> > var newBool = new Boolean(true);
> > // valueOf()返回的是true，两者的值相等
> > console.log( newBool.valueOf() == newBool );     // true
> > // 但是不全等，前者是boolean类型，后者是object类型
> > console.log( newBool.valueOf() === newBool );     // false
> >
> > // Function：返回函数本身
> > function foo(){ 
> > }
> > console.log( foo.valueOf() === foo );             // true
> > var foo2 =  new Function("x", "y", "return x + y;");
> > console.log( foo2.valueOf() === foo2 );         // true
> >
> > // Object：返回对象本身
> > var obj = {name: "张三", age: 18};
> > console.log( obj.valueOf() === obj );         // true
> >
> > // String：返回字符串值
> > var str = "http://www.baidu.com";
> > console.log( str.valueOf() === str );         // true
> > // new一个字符串对象
> > var str2 = new String("http://www.365mini.com");
> > // 但不全等，前者为string类型，后者为object类型
> > console.log( str2.valueOf() === str2 );         // false
> > ```



