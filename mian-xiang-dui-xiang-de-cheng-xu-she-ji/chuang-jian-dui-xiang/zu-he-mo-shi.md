#### 组合使用构造函数模式和原型模式

```js
function Person(name, age, job) {
    this.name = name;
    this.age = age;
    this.job = job;
    this.friends = ["jiangxiaoni", "zhuhao"];
}
Person.prototype = {
    constructor : Person,
    sayName : function() {
        alert(this.name);
    }
}
var person1 = new Person("liyan", 18, "teacher");
var person2 = new Person("jiangxiaoni", 42, "farmer");

person1.friends.push("donglele");
alert(person1.friends);    // jiangxiaoni, zhuhao, donglele
alert(person2.friends);    //jiangxiaoni, zhuhao
alert(person1.friends === person2.friends);    // false
alert(person1.sayName === person2.sayName);    // true
```





