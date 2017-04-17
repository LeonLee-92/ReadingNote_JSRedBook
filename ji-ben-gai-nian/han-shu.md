#### 函数

> ##### arguments 对象
>
> ```js
> function howManyArgs() {
>     alert(arguments.length);
> }
> howManyArgs("string", 45);    // 2
> howManyArgs();                // 0
> howManyArgs(45);              // 1
> ```
>
> ##### arguments对象中的值和对应参数的值会双向同步（书中有误）
>
> ```js
> function doAdd(num1, num2) {
>     arguments[1] = 10;
>     console.log(num2);  // 同步为10
> }
> doAdd(1,2);
> ```
>
> ```js
> function doAdd(num1, num2) {
>     num2 = 10;
>     console.log(arguments[1]);  // 同步为10
> }
> doAdd(1,2);
> ```
>
> 没有传递的参数会自动赋予undefined
>
> ```js
> function doAdd(num1, num2) {
>     console.log(num2);          // 没传递的参数，undefined
>     console.log(arguments[1]);  // 没传递的参数，undefined
> }
> doAdd(1);
> ```
>
> #### ECMAScript没有重载
>
> ##### 如果在ECMAScript中定义了两个名字相同的函数，则该名字只属于后定义的函数。
>
> ```js
> function addNum(num){
>     return num + 100;
> }
> function addNum(num){
>     return num + 200;
> }
> console.log(addNum(100));  // 300
> ```
>
> ##### Tip:
>
> ##### 通过检查传入函数中参数的类型和数量并作出不同的反应，可以模仿方法的重载。



