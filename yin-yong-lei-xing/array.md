#### \*JS中数组的每一项可以可以保存任何类型的数据。

#### 创建数组的两种方式：

> ##### new Array\(\) 方式：
>
> ```js
> var colors = new Array(3);  // 创建时写入length
> var names = new Array("liyan", "zhangsan", "lisi");  // 创建时带3个元素
> var arr = Array(5);  // 可省略 new
> ```
>
> ##### 字面量方式：
>
> ```js
> var colors = ["red", "blue", "green"];
> var names = [];  // 创建一个空数组
> var values = [1, 2,];  // 要避免这种写法，不同浏览器解析元素量不同
> ```

#### length属性：

> ##### 并不是只读的：
>
> ```js
> var colors = ["red", "blue", "green"];
> colors.length = 2;        // 移除末尾项
> alert(colors[2]);  // undefined
> ```
>
> ##### 利用length追加元素：
>
> ```js
> var colors = ["red", "blue", "green"];
> colors[colors.length] = "black";
> colors[colors.length] = "brown";
> ```

#### 检测数组：

> ##### instanceof :
>
> > ```
> > if (value instanceof Array){
> >     // DoSomething
> > }
> > ```
>
> > ##### 存在的问题：如果网页中包含多个框架，那实际上就存在两个以上不同的全局执行环境，从而存在两个以上不同版本的Array构造函数。
>
> ##### Array.isArray\(\) :
>
> ```
>
> ```





