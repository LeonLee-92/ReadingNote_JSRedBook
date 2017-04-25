### Global对象：

> #### URI编码方法
>
> > ##### 用UTF-8编码替换无效字符，以便浏览器解析
> >
> > ##### encodeURI\(\) : 不会对本身属于URI的特殊字符进行编码，例如 ":" 、"/" 、"?"  和  "\#"
> >
> > ##### encodeURIComponent\(\) : 对任何非标准字符进行编码
> >
> > ```js
> > var uri = "http://www.baidu.com/123abc def.html#start"
> >
> > alert(encodeURI(uri));    // http://www.baidu.com/123abc%20def.html#start
> > alert(encodeURIComponent(uri));    // http%3A%2F%2Fwww.baidu.com%2F123abc%20def.html%23start
> > ```
>
> #### URI解码方法
>
> > ##### decodeURI\(\) : 对应encodeURI\(\)
> >
> > ##### decodeURIComponent\(\) : 对应encodeURIComponent\(\)
> >
> > ```js
> > var uri = "http%3A%2F%2Fwww.baidu.com%2F123abc%20def.html%23start";
> > alert(decodeURI(uri));            // http%3A%2F%2Fwww.baidu.com%2F123abc def.html%23start  只解出了空格
> > alert(decodeURIComponent(uri));    // http://www.baidu.com/123abc def.html#start
> > ```
>
> #### eval\(\) 方法：
>
> > ##### eval\(\)执行的代码被认为是包含该次调用的执行环境的一部分，被执行的代码具有与该执行环境相同的作用域链。
> >
> > ```js
> > var msg = "hello world";
> > eval("alert(msg)");    //hello world
> > ```
> >
> > ```js
> > eval("function sayHi() { alert('hi'); }");
> > sayHi();    // hi
> > ```
> >
> > #### 作者建议：慎用eval\(\)，防止注入
>
> #### Global对象的属性：
>
> > ![](/assets/00711.jpg)
>
> #### window对象：全局变量和函数都是window的属性
>
> > ```js
> > var color = "red";
> > function sayColor() {
> >     alert(window.color);
> > }
> > window.sayColor();    // "red"
> > ```
> >
> > ##### 另一种取得Global对象的方式：
> >
> > ```js
> > var global = function() {
> >     return this;
> > }();
> > ```

#### Math对象：保存着一些数学公式和信息

> #### Math对象的属性：
>
> | 属　　性 | 说　　明 |
> | :---: | :---: |
> | Math.E | 自然对数的底数，即常量e的值 |
> | Math.LN10 | 2的自然对数 |
> | Math.LOG2E | 以2为底e的对数 |
> | Math.LOG10E | 以10为底e的对数 |
> | Math.PI | π的值 |
> | Math. SQRT1\_2 | 1/2的平方根（即2的平方根的倒数） |
> | Math.SQRT2 | 2的平方根 |
>
> #### min\(\) 和 max\(\) 方法：
>
> > ```js
> > var max = Math.max(1, 2, 3, 10, 5);
> > var min = Math.min(1, 2, 3, 10, 5);
> >
> > alert(max);    // 10
> > alert(min);    // 1
> > ```
> >
> > 数组的操作：
> >
> > ```js
> > var values = [1, 2, 3, 4, 5, 6];
> > var max = Math.max.apply(Math, values);
> >
> > alert(max);    // 6
> > ```
>
> #### 舍入方法：
>
> > Math.ceil\(\) : 向上舍入
> >
> > Math.floor\(\) : 向下舍入
> >
> > Math.round\(\) : 四舍五入
> >
> > ```js
> > alert(Math.ceil(15.9));    // 16
> > alert(Math.ceil(15.6));    // 16
> > alert(Math.ceil(15.1));    // 16
> >
> > alert(Math.floor(15.9));    // 15
> > alert(Math.floor(15.6));    // 15
> > alert(Math.floor(15.1));    // 15
> >
> > alert(Math.round(15.9));    // 16
> > alert(Math.round(15.6));    // 16
> > alert(Math.round(15.1));    // 15
> > ```
>
> #### random\(\) 方法：
>
> > ```js
> > var num1 = Math.floor(Math.random() * 10 + 1);    // 1 ~ 10
> > var num2 = Math.floor(Math.random() * 9 +2);    // 2 ~ 10
> > ```
> >
> > ```js
> > function selectFrom(lowerValue, upperValue) {
> >     var choices = upperValue - lowerValue;
> >     return Math.floor(Math.random() * choices + lowerValue);
> > }
> >
> > var num = selectFrom(2, 10);    // 2 ~ 10的随机数
> > ```
>
> #### 其他方法：
>
> ![](/assets/00751.jpg)



