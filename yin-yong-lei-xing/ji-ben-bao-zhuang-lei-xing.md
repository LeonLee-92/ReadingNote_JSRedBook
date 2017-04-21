### 基本概念：

> ### ECMAScript提供了3个特殊的引用类型：Boolean、Number和String
>
> ---
>
> ####  底层的操作，以String举例：
>
> > ```js
> > // 创建一个基本类型的字符串
> > var s1 = "some text";
> >
> > // 创建一个String实例
> > // 调用substring()函数
> > // 销毁String实例
> > var s2 = s1.substring(2);
> > ```
>
> #### 引用类型和基本包装类型的区别在于生命周期：
>
> > ###### 引用类型：声明周期绑定与作用域
> >
> > ###### 基本包装类型：声明周期只在于一行代码
> >
> > ```js
> > var s1 = "some text";
> > s1.color = "red";
> > alert(s1.color);    // undefined
> > ```
>
> #### new Object\(\)可以自动转换：
>
> > ```js
> > var obj = new Object("some text");
> > alert(obj instanceof String);    //true
> > ```
>
> #### 注意：
>
> > ##### 1. typeof对基本包装类型返回object ，
> >
> > ##### 2. 基本包装类型转Boolean都是true
> >
> > ##### 3. 区分转型函数和构造函数
> >
> > ```js
> > var value = "25";
> > var number = Number(value);    // 转型函数
> > alert(typeof number);    // number
> >
> > var obj = new Number(value);    // 构造函数
> > alert(typeof obj);        // object
> > ```



