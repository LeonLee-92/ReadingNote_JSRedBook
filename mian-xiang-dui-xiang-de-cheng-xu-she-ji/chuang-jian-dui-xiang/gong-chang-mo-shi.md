```js
function createPerson (name, age, job) {
    var o = new Object();
    o.name = name;
    o.age = age;
    o.job = job;
    o.sayName = function() {
        alert(this.name);
    };
    return o;
}
var person1 = createPerson("liyan", 18, "teacher");
var person1 = createPerson("jiangxiaoni", 36, "farmer");
```

#### 工厂模式虽然解决了创建多个相似对象的问题，

#### 但却没有解决对象识别的问题（所有对象都是Object的实例）。



