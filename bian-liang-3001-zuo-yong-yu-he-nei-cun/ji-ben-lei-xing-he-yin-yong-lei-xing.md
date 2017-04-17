#### 基本类型：Undefined、Null、Boolean、Number 和 String

#### 引用类型：Object

> #### Tip：
>
> 在 JavaScript 中 String 不是引用类型。

#### 动态的属性：

> ```js
> var person = new Object();
> person.name = "liyan";
> alert(person.name);  // liyan
> ```
>
> ##### 注意：给基本类型添加属性，并不会报错

> ```
> var name = "liyan";
> name.age = 27;
> alert(name.age);  // undefined
> ```



