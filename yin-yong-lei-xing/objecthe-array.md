#### 创建Object实例的两种方式：

> ##### new Object方式：
>
> ```js
> var person = new Object();
> person.name = "liyan";
> person.age = 18;
> ```
>
> ##### 字面量方式：
>
> ```js
> var person = {
>     name: "liyan",
>     age: 18    // 最后一个属性后面不加逗号
> }
> ```

#### 对象字面量也是向函数传递大量可选参数的首选方式：

> ```js
> function displayInfo(args){
>     var output = "";
>     if(typeof args.name == "string"){
>         output += "Name: " + args.name + "\n";
>     }
>     if(typeof args.age == "number"){
>         output += "Age: " + args.age + "\n";
>     }
>     alert(output);
> }
> displayInfo({
>    name: "liyan",
>    age: 18 
> });
> displayInfo({
>    name: "liyan",
> });
> ```

#### 还可以使用方括号访问属性：

> ```js
> alert(person.name); 
> // 等同于
> alert(person["name"]); 
> ```
>
> ```js
> var propertyName = "first name"; //点语法无法访问的属性
> person[propertyName] = "liyan";  //通过方括号访问
> ```





