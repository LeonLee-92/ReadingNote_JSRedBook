#### 分类

> ##### 基本类型：Undefined、Null、Boolean、Number 和 String
>
> ##### 引用类型：Object
>
> #### Tip：
>
> 在 JavaScript 中 String 不是引用类型。

#### 动态的属性：

> ```js
> var person = new Object();
> person.name = "liyan";
> alert(person.name);  // "liyan"
> ```
>
> ##### 注意：给基本类型添加属性，并不会报错
>
> ```js
> var name = "liyan";
> name.age = 27;
> alert(name.age);  // undefined
> ```

#### 变量赋值：

> ```js
> var num1 = 5;
> var num2 = num1;
> ```
>
> ![](/assets/00192.jpg)
>
> ```js
> var obj1 = new Object();
> var obj2 = obj1;
> obj1.name = "liyan";
> alert(obj2.name);  // "liyan"
> ```
>
> ![](/assets/00319.jpg)

#### 传递参数：

> ##### 基本类型：
>
> ```js
> function addTen(num) {
>     num += 10;
>     return num;
> }
> var count = 20;
> var result = addTen(count);
> alert(count);   // 20 互不影响
> alert(result);  // 30
> ```
>
> 引用类型：
>
> ```js
> function setName(obj) {
>     obj.name = "liyan";
> }
> var person = new Object();
> setName(person);
> alert(person.name);  // "liyan"
> ```
>
> ```js
> function setName(obj) {
>     obj.name = "liyan";
>     obj = new Object();   // 改变了局部变量的引用，该对象会在函数执行完毕后立即销毁
>     obj.name = "zhangsan";
> }
> var person = new Object();
> setName(person);
> alert(person.name);  // "liyan"
> ```

#### 检测类型：

> ##### typeof\(\)：检测基本类型（Undefined、Null、Boolean、Number 和 String）和Object
>
> ##### instanceof：检测Object类型

#### 执行环境及作用域：

> ![](/assets/00343.jpg)

> ![](/assets/00347.jpg)





