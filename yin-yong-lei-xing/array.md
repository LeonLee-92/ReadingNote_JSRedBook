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
> > ```js
> > if (value instanceof Array){
> >     // DoSomething
> > }
> > ```
> >
> > ##### 存在的问题：如果网页中包含多个框架，那实际上就存在两个以上不同的全局执行环境，从而存在两个以上不同版本的Array构造函数。
>
> ##### Array.isArray\(\) :
>
> ```js
> if (Array.isArray(value)){
>     // DoSomething
> }
> ```

#### 转换方法：

> ##### toString\(\) 和 valueOf\(\) :
>
> > 调用数组元素每项的toString\(\)方法，以逗号分隔拼接字符串
> >
> > ```js
> > var colors = ["red", "blue", "green"];
> > alert(colors.toString());  // "red,blue,green"
> > alert(colors.valueOf());   // "red,blue,green"
> > alert(colors);  // 底层调用了 colors.toString()
> > ```
>
> ##### toLocaleString\(\) :
>
> > 调用数组元素每项的toString\(\)方法，以逗号分隔拼接字符串。通常和toString\(\)方法返回相同
> >
> > ```js
> > var person1 = {
> >     toLocaleString: function() {
> >         return "123";
> >     },
> >     toString: function() {
> >         return "456";    
> >     }
> > }
> > var person2 = {
> >     toLocaleString: function() {
> >         return "abc";
> >     },
> >     toString: function() {
> >         return "def";    
> >     }
> > }
> > var people = [person1, person2];
> > alert(people);                   // "456,def"
> > alert(people.toString());        // "456,def"
> > alert(people.toLocaleString());  // "123,abc"
> > ```
>
> ##### join\(\) :
>
> > ```js
> > var colors = ["red", "blue", "green"];
> > alert(colors.join(','));  // "red,blue,green"
> > alert(colors.join('||'));  // "red||blue||green"
> > ```
> >
> > ##### 当不传参或传入undefined时，使用逗号分隔
> >
> > ##### 当数组元素为null或undefined的时候，该值在join、toString、toLocaleString、valueOf返回空字符串
> >
> > ```js
> > var arr = ["a",null,"b"];
> > alert(arr.toString());   // "a,,b"
> > ```

#### 栈方法：（LIFO，后进先出）

> ##### 用push\(\) 和 pop\(\)可以实现类似栈的行为。

#### 队列方法：（FIFO，先进先出）

> ##### 用push\(\) 和 shift\(\)可以实现类似队列的行为。
>
> ##### 用unshift\(\) 和 pop\(\)可以实现类似反方向队列的行为。

#### 排序方法：

> ##### reverse\(\) :
>
> ```js
> var values = [1,2,3,4,5];
> alert(values.reverse());  // "5,4,3,2,1"
> ```
>
> ##### sort\(\) :
>
> > 默认依toString\(\)返回的字符串进行比较：
> >
> > ```js
> > var values = [0,1.5,10,15];
> > alert(values.sort());  // "0,1.5,10,15"
> > ```
> >
> > 可传比较函数：
> >
> > ```js
> > function compare(value1, value2) {
> >     return value2 - value1;
> > }
> > var values = [0,1,15,10,5];
> > alert(values.sort(compare));  // "15,10,5,1,0"
> > ```

#### 操作方法：

> ##### concat\(\) :
>
> ```js
> var colors = ["red", "green", "blue"];
> var colors2 = colors.concat("yellow", ["black", "brown"]);
>
> alert(colors);  // "red,green,blue"
> alert(colors2); // "red,green,blue,yellow,black,brown"
> ```
>
> ##### slice\(\) :
>
> > ```js
> > var colors = ["red","green","blue","yellow","purple"];
> > var colors2 = colors.slice(1);    // ["green", "blue", "yellow", "purple"]
> > var colors3 = colors.slice(1,3);  // ["green", "blue"]
> > ```
> >
> > slice\(\) 参数为负数时，顺序倒数
> >
> > ```js
> > var colors = ["red","green","blue","yellow","purple"];
> > var colors2 = colors.slice(-3, -1);    // ["blue", "yellow"]
> > ```
>
> ##### splice\(\) :
>
> ```js
> var colors = ["red","green","blue"];
> var removed = colors.splice(0, 1);  // 删除指定项，并返回
> alert(colors);   // green,blue
> alert(removed);  // red
> ```

#### 位置方法：

> ##### indexOf\(\) :正序查找
>
> ```js
> var numbers = [1,2,3,4,5,4,3,2,1];
> alert(numbers.indexOf(4));  // 3
> ```
>
> ##### lastIndexOf\(\) : 倒序查找
>
> ```js
> var numbers = [1,2,3,4,5,4,3,2,1];
> alert(numbers.lastIndexOf(4));  // 5
> ```
>
> ##### 第二个参数，表示从哪里开始查找：
>
> ```js
> var numbers = [1,2,3,4,5,4,3,2,1];
> alert(numbers.lastIndexOf(4, 4));  // 5
> alert(numbers.lastIndexOf(4, 4));  // 3
> ```
>
> ##### 两个方法判断的是全等（===）：
>
> ```js
> var person = {name: "liyan"};
> var people1 = [{name: "liyan"}];
> var people2 = [person];
>
> alert(people1.indexOf(person));  // -1  不全等
> alert(people2.indexOf(person));  // 0  全等成立
> ```

#### 迭代方法：

> ##### forEach\(\) :依次执行，没有返回值
>
> ##### every\(\) :每一项都返回true，则返回true
>
> ##### some\(\) :任一项返回true，则返回true
>
> ##### filter\(\) :返回会返回true的项组成的数组
>
> ##### map\(\) :返回每项执行函数返回结果组成的数组
>
> ```js
> var numbers = [1,2,3,4,5,4,3,2,1];
> var everyResult = numbers.every(function(item, index, array){
>     return (item > 2);
> });
> alert(everyResult);  // false
>
> var someResult = numbers.some(function(item, index, array){
>     return (item > 2);
> });
> alert(someResult);   // true
>
> var filterResult = numbers.filter(function(item, index, array){
>     return (item > 2);
> });
> alert(filterResult); // [3,4,5,4,3]
>
> var mapResult = numbers.map(function(item, index, array){
>     return (item * 2);
> });
> alert(mapResult);    // [2,4,6,8,10,8,6,4,2]
> ```

#### 缩小方法：

> ##### reduce\(\) :正序累计执行函数
>
> ##### reduceRight\(\) :倒序累计执行函数
>
> ```js
> var values = [1,2,3,4,5];
> var sum = values.reduce(function(prev,cur){ 
>     return prev + cur
> }); 
> alert(sum);  // 15
> ```
>
> ##### 第二个参数为，第一次执行前设置的基数：
>
> ```js
> var values = [1,2,3,4,5];
> var sum = values.reduce(function(prev,cur){ 
>     return prev + cur
> }, 100); 
> alert(sum);  // 115
> ```



