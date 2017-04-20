#### 创建：

> ##### 函数声明
>
> ```js
> function sum (num1, num2) {
>     return num1 + num2;
> }
> ```
>
> ##### 函数表达式
>
> ```js
> var sum = function(num1, num2)(
>      return num1 + num2;   
> )
> ```
>
> ##### 构造函数
>
> ```js
> var sum = new Function("num1", "num2", "return num1 + num2");
> ```

#### 没有重载：

> ```js
> function addSomeNumber (num) {
>     return num + 100;
> }
> function addSomeNumber (num) {
>     return num + 200;
> }
> var result = addSomeNumber(100);   // 300
> ```
>
> ##### 等价于
>
> ```js
> var addSomeNumber = function(num) {
>     return num + 100;
> }
> var addSomeNumber = function(num) {
>     return num + 200;
> }
> var result = addSomeNumber(100);   // 300
> ```

#### 声明与表达式的不同：

> ##### 后声明可被正常调用：
>
> ```js
> alert(sum(num1, num2));
> function sum (num1, num2) {
>     return num1 + num2;
> }
> ```
>
> ##### 后写表达式会报错：
>
> ```js
> alert(sum(num1, num2));
> var sum = function(num1, num2) {
>     return num1 + num2;
> }
> ```

#### 作为值传递：

> ##### 作为参数：
>
> ```js
> function callSomeFunction(someFunction, someArgument){
>     return someFunction(someArgument);
> }
> function add10(num){
>     return num + 10;
> }
> var result = callSomeFunction(add10, 10);
> alert(result);   // 20
> ```
>
> ##### 作为返回值：
>
> ```js
> function compare(propertyName){
>     return function(object1, object2){
>         var value1 = object1[propertyName];
>         var value2 = object2[propertyName];
>         
>         if(value1 < value2){
>             return -1;
>         }else if(value1 > value2){
>             return 1;
>         }else{
>             return 0;
>         }
>     }
> }
>
> var  data = [{name: "Zachary", age: 28}, {name: "Nicholas", age: 29}];
>
> data.sort(compare("name"));
> alert(data[0].name);   // Nicholas
>
> data.sort(compare("age"));
> alert(data[0].name);   // Zachary
> ```

#### 函数内部属性：

> #### arguments对象的callee属性：
>
> ##### 指针类型，指向包含arguments对象的函数。
>
> > ##### 没有callee存在的问题：
> >
> > ```js
> > function factorial(num){
> >     if(num <= 1){
> >         return 1;
> >     }else{
> >         return num * factorial(num - 1);
> >     }
> > }
> > var factorial2 = factorial;
> > factorial = function(){
> >     return 0;
> > }
> > alert(factorial2(5));    // 0  factorial函数已被覆盖
> > alert(factorial(5));    // 0
> > ```
> >
> > ##### 使用callee解决：
> >
> > ```js
> > function factorial(num){
> >     if(num <= 1){
> >         return 1;
> >     }else{
> >         return num * arguments.callee(num-1);
> >     }
> > }
> > var factorial2 = factorial;
> > factorial = function(){
> >     return 0;
> > }
> > alert(factorial2(5));    // 120   可以正常递归
> > alert(factorial(5));    // 0
> > ```
>
> #### this属性：
>
> ##### 指针，应用函数的执行环境
>
> ```js
> var color = "red";
> var o = {color: "blue"};
> function sayColor(){
>     alert(this.color);
> }
> sayColor();  // red
>
> o.sayColor = sayColor();
> o.sayColor();   // blue
> ```
>
> #### caller属性：
>
> ##### 指针，指向调用当前函数的函数，全局作用域的函数返回null
>
> ```js
> function outer(){
>     inner();
> }
> function inner(){
>     alert(inner.caller);
> }
> outer();  // 此处会console出outer函数的源代码
> ```
>
> ##### 此处也可以使用arguments.callee松耦合
>
> ```js
> function outer(){
>     inner();
> }
> function inner(){
>     alert(arguments.callee.caller);
> }
> outer();  // 此处会console出outer函数的源代码
> ```

#### 属性和方法：

> ##### length属性：希望接收参数的个数
>
> > ```js
> > function sayName(name){
> >     alert(name);
> > }
> > function sum(num1, num2){
> >     return num1 + num2;
> > }
> > function sayHi(){
> >     alert("hi");
> > }
> >
> > alert(sayName.length);    // 1
> > alert(sum.length);        // 2
> > alert(sayHi.length);      // 0
> > ```
>
> ##### prototype属性：
>
> > ##### 不可枚举，不能使用for-in遍历出
>
> ##### bind\(\) :
>
> > ```js
> > var num = 1; 
> > function sum(num){
> >     return this.num;
> > }
> > function callSum(num){
> >     return sum.call(this, num);
> > }
> > alert(callSum(100));    // 1
> > ```
>
> ##### apply\(\) 和 call\(\) :
>
> > #### 用途：在指定作用域中调用函数，等同于设置函数内部的this值。
> >
> > ##### apply\(\) : 第一个参数是作用域, 第二个参数是数组或arguments对象
> >
> > > ```js
> > > var num1 = 1; 
> > > var num2 = 2;
> > > function sum(num1, num2){
> > >     return this.num1 + this.num2;
> > > }
> > > function callSum1(num1, num2){
> > >     return sum.apply(this, arguments);
> > > }
> > > function callSum2(num1, num2){
> > >     return sum.apply(this, [num1, num2]);
> > > }
> > > alert(callSum1(10, 10));    // 3
> > > alert(callSum2(10, 10));    // 3
> > > ```
> >
> > ##### call\(\) : 第一个参数是作用域，传递给函数的参数后面逐个列出
> >
> > > ```js
> > > var num1 = 1; 
> > > var num2 = 2;
> > > function sum(num1, num2){
> > >     return this.num1 + this.num2;
> > > }
> > > function callSum(num1, num2){
> > >     return sum.call(this, num1, num2);
> > > }
> > > alert(callSum(10, 10));    // 3
> > > ```

#### 



