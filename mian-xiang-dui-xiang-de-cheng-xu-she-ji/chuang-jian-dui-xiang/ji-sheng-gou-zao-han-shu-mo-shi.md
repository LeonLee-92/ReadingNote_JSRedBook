#### 类似于工厂模式和构造函数模式的结合：

```js
function Person(name, age, job){
    var o = new Object();
    o.name = name;
    o.age = age;
    o.job = job;
    o.sayName = function() {
        alert(this.name);
    }
    return o;
}
var friend = new Person("liyan", 17, "teacher");
friend.sayName();    // liyan
```

#### 使用场景：

> ##### 创建一个特殊的数组，添加一个额外的方法
>
> ```js
> function SpecialArray() {
>     var values = new Array();
>     values.push.apply(values, arguments);
>     values.toPipedString = function() {
>         return this.join("|");
>     };
>     return values;
> }
> var colors = new SpecialArray("red", "blue", "green");
> alert(colors.toPipedString());    // "red|blue|green"
> ```



