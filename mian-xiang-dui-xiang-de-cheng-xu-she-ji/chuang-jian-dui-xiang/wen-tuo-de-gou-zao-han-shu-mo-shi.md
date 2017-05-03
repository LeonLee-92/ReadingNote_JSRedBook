#### 重点在安全性：

```js
function Person(name, age, job){

    var o = new Object();
    o.sayName = function() {
        alert(name);
    };
    return o;
}
var friend = Person("liyan", 18, "teacher");
friend.sayName();    // liyan
```



