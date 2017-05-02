```js
function Person(name, age, job){
    this.name = name;
    this.age = age;
    this.job = job;
    if (typeof this.sayName != "function"){
        Person.prototype.sayName = function(){
            alert(this.name);
        }
    }
}

var friend = new Person("jiangxioani", 56, "farmer");
friend.sayName();
```



