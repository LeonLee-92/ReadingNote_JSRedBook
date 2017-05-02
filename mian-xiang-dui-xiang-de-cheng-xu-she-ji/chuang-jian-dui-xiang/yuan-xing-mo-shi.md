### 理解原型

> ```js
> function Person() {
> }
>
> Person.prototype.name = "liyan";
> Person.prototype.age = 18;
> Person.prototype.job = "teacher";
> Person.prototype.sayName = function() {
>     alert(this.name);
> };
>
> var peroson1 = new Person();
> person1.sayName();    // "liyan"
> var person2 = new Person();
> person2.sayName();    // "liyan"
> alert(person1.sayName == person2.sayName);    // true
> ```
>
> ![](/assets/01181.jpg)
>
> ![](/assets/WechatIMG1.jpg)
>
> ##### 所有原型对象会自动获得constructor属性，指向prototype属性所在的函数
>
> ##### 每个函数  都有一个prototype属性，指向一个包含共享属性和方法的对象（通过构造函数创建的实例的原型对象）
>
> ##### 每个实例都有一个\_\__proto_\_\_属性，指向构造函数的原型对象
>
> ### isPropertyOf\(\) :
>
> > ```js
> > alert(Person.prototype.isPrototypeOf(person1));    // true
> > alert(Person.prototype.isPrototypeOf(person2));    // true
> > ```
>
> ### 属性访问 ：
>
> > ##### 当为对象添加属性时，会屏蔽原型中保存的同名属性。
> >
> > ##### 即使将属性设置为null，也不能解除屏蔽。但delete可以恢复对原型属性的连接
> >
> > ```js
> > function Person() {
> > }
> >
> > Person.prototype.name = "liyan";
> > Person.prototype.age = 18;
> > Person.prototype.job = "teacher";
> > Person.prototype.sayName = function() {
> >     alert(this.name);
> > };
> >
> > var peroson1 = new Person();
> > var person2 = new Person();
> >
> > person1.name = "jiangxiaoni";
> > alert(person1.name);    // jiangxiaoni  --来自实例
> > alert(person2.name);    // liyan --来自原型
> >
> > delete person1.name;
> > alert(person1.name);    // liyan --来自原型
> > ```
> >
> > #### hasOwnProperty\(\) :
> >
> > ##### 只有存在实例属性返回true

### 原型与in操作符

> ```js
> function Person() {
> }
>
> Person.prototype.name = "liyan";
> Person.prototype.age = 18;
> Person.prototype.job = "teacher";
> Person.prototype.sayName = function() {
>     alert(this.name);
> };
>
> var peroson1 = new Person();
> var person2 = new Person();
>
> alert(person1..hasOwnProperty("name"));    // false
> alert("name" in person1);    // true
>
> person1.name = "jiangxiaoni";
> alert(person1.name);    // jiangxiaoni  --来自实例
> alert(person1..hasOwnProperty("name"));    // true
> alert("name" in person1);    // true
>
> alert(person2.name);    // liyan  --来自原型
> alert(person1..hasOwnProperty("name"));    // false
> alert("name" in person1);    // true
>
> delete person1.name;
> alert(person1.name);    // liyan  --来自原型
> alert(person1..hasOwnProperty("name"));    // false
> alert("name" in person1);    // true
> ```
>
> #### 取对象所有可枚举的实例属性，可以使用Object.keys\(\)方法：
>
> ```js
> function Person() {
> }
>
> Person.prototype.name = "liyan";
> Person.prototype.age = 18;
> Person.prototype.job = "teacher";
> Person.prototype.sayName = function() {
>     alert(this.name);
> };
>
> var keys = Object.keys(Person.prototype);
> alert(keys);    // "name, age, job, sayName"
> var p1 = new Person();
> p1.name = "liyan";
> p1.age = 17;
> var p1keys = object.keys(p1);
> alert(p1keys);    // "name, age"
> ```
>
> #### 取实例属性，无论是否可枚举，可以使用Object.getOwnPropertyNames\(\)方法：
>
> ```js
> var keys = Object.getOwnPropertyNames(Person.prototype);
> alert(keys);    // "constructor, name, age, job, sayName"  --包含了不可枚举的constructor属性
> ```

### 更简单的原型语法

> ```js
> function Person() {}
> Person.prototype = {
>     name : "liyan",
>     age : 18,
>     job : "teacher",
>     sayName : function(){
>         alert(this.name);
>     }
> }
> ```
>
> ##### 此做法会导致constructor属性不再指向Person，指向新对象的constructor，即Object
>
> ##### instanceof可以返回正确的结果
>
> ```js
> var friend = new Person();
>
> alert(friend instanceof Object);    // true
> alert(friend instanceof Person);    // true
> alert(friend.constructor == Person);    // false
> alert(friend.constructor == Object);    // true
> ```
>
> #### 重设constructor属性：
>
> > ```js
> > function Person() {}
> > Person.prototype = {
> >     constructor : Person,
> >     name : "liyan",
> >     age : 18,
> >     job : "teacher",
> >     sayName : function(){
> >         alert(this.name);
> >     }
> > }
> > ```
> >
> > ##### 问题：导致constructor属性的Enumerable特性被设置为true
> >
> > #### 优化：
> >
> > > ```js
> > > function Person() {}
> > > Person.prototype = {
> > >     name : "liyan",
> > >     age : 18,
> > >     job : "teacher",
> > >     sayName : function(){
> > >         alert(this.name);
> > >     }
> > > }
> > > Object.defineProperty(Person.prototype, "constructor", {
> > >     enumerable : false,
> > >     value : Person
> > > });
> > > ```



