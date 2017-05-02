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



