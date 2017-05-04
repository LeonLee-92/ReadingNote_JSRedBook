### 原型链

> ```js
> function ParentType() {
>     this.property = true;
> }
> function SonType() {
>     this.sonProperty = false;
> }
> SonType.prototype = new ParentType();    // 继承
>
> ParentType.prototype.getParentValue = function() {
>     return this.property;
> };
>
> SonType.prototype.getSonValue = function() {
>     return this.sonProperty;
> }
>
> var instance = new SonType();
> alert(instance.getParentValue());    // true
> ```
>
> #### 继承关系
>
> > ![](/assets/00032.jpg)
>
> #### 判断原型和实例的关系
>
> > #### 通过 instanceof
> >
> > ```js
> > alert(instance instanceof Object);    // true
> > alert(instance instanceof ParentType);    // true
> > alert(instance instanceof SonType);    // true
> > ```
> >
> > #### 通过 isPrototypeOf\(\)
> >
> > ```js
> > alert(Object.protorype.isPrototypeOf(instance));    // true
> > alert(ParentType.protorype.isPrototypeOf(instance));    // true
> > alert(SonType.protorype.isPrototypeOf(instance));    // true
> > ```
>
> #### 谨慎定义方法
>
> > #### 添加方法一定要在替换原型之后
> >
> > > ![](/assets/00040.jpg)
> >
> > #### 不要使用字面量创建原型方法
> >
> > > ![](/assets/00044.jpg)
>
> #### 原型链存在的问题
>
> > #### 1.父类的实例属性会继承为子类的原型属性
> >
> > > ```js
> > > function ParentType() {
> > >     this.colors = ["red", "blue", "green"];
> > > }
> > > function SonType() {
> > >     
> > > }
> > > SonType.prototype = new ParentType();
> > >
> > > var instance1 = new SonType();
> > > instance1.colors.push("black");
> > > alert(instance1.colors);        // red,blue,green,black
> > >
> > > var instance2 = new SonType();
> > > alert(instance2.colors);        // 与instance1引用了同一个对象
> > > ```
> >
> > #### 2.创建子类实例时，无法向父类构造函数传参

### 借用构造函数

> ```js
> function ParentType() {
>     this.colors = ["red", "blue", "green"];
> }
> function SonType() {
>     ParentType.call(this);    // 继承
> }
> var instance1 = new SonType();
> instance1.colors.push("black");
> alert(instance1.colors);    // red,blue,green,black
> var instance2 = new SonType();
> alert(instance2.colors);    // red,blue,green
> ```
>
> #### 像父类构造函数传参
>
> ```js
> function ParentType(name) {
>     this.name = name;
> }
> function SonType(name, age) {
>     ParentType.call(this,name);
>     this.age = age;
> }
> var instance = new SonType("liyan", 18);
> alert(instance.name);
> alert(instance.age);
> ```
>
> #### 借用构造函数存在的问题
>
> ##### 1.父类原型中定义的方法子类不可见。
>
> ##### 2.方法都在构造函数中定义，函数无法复用。

### 组合继承

> 融合了原型链和构造函数的优点，是JS中最常用的继承模式
>
> ```js
> function ParentType(name){
>     this.name = name;
>     this.colors = ["red", "blue", "green"];
> }
> ParentType.prototype.sayName = function() {
>     alert(this.name);
> };    
> function SonType(name, age){
>     ParentType.call(this, name);
>     this.age = age;
> }
> SonType.prototype = new ParentType();
> SonType.prototype.sayAge = function() {
>     alert(this.age);
> }
>
> var instance1 = new SonType("liyan", 18);
> instance1.colors.push("balck");
> alert(instance1.colors);    // red,blue,green,black
> alert(instance1.sayName());    // liyan
> alert(instance1.sayAge());    // 18
>
> var instance1 = new SonType("jiangxiaoni", 39);
> alert(instance1.colors);    // red,blue,green
> alert(instance1.sayName());    // jiangxiaoni
> alert(instance1.sayAge());    // 39
> ```

### 原型式继承

> #### 重要：这种模式引用类型的属性会始终共享

> ```js
> function object(o){
>     function F(){}
>     F.prototype = o;
>     return new F();
> }
> var person = {
>     name: "liyan",
>     colors: ["red", "blue", "green"]
> }
> var anotherPerson = object(person);
> anotherPerson.name = "jiangxiaoni";
> anotherPerson.colors.push("orange");
>
> var yetAnotherPerson = object(person);
> yetAnotherPerson.name = "zhouyuan";
> yetAnotherPerson.colors.push("black");
>
> alert(person.colors);    // red,blue,green,orange,black
> ```
>
> #### 使用Object.create\(\)方法
>
> > ![](/assets/00193.jpg)
> >
> > #### 第二个参数与Object.defineProperties\(\)方法格式相同
> >
> > > ```js
> > > var person = {
> > >     name: "liyan",
> > >     colors: ["red", "blue", "green"]
> > > };
> > > var anotherPerson = Object.create(person, {
> > >     name: {
> > >         value: "jiangxiaoni"
> > >     }
> > > });
> > > alert(anotherPerson.name);    // jiangxiaoni
> > > ```

### 寄生式继承

> ```js
> function object(o){
>     function F(){}
>     F.prototype = o;
>     return new F();
> }
> function createAnother(original) {
>     var clone = object(original);
>     clone.sayHi = function() {
>         alert("hi");
>     }
>     return  clone;
> }
> var person = {
>     name: "liyan",
>     colors: ["red", "blue", "green"]
> }
> var anotherPerson = createAnother(person);
> anoterPerson.sayHi();    // hi
> ```
>
> #### 此模式函数不能复用

### 寄生组合式继承

> #### 实现继承的最有效方法

> ```js
> // 继承父类原型
> function inheritPrototype(son, parent) {
>     var protyotype = object(parent.prototype);    // 创建父类的原型副本
>     prototype.constructor = son;        // 更改副本的构造函数
>     son.prototype = prototype;        // 将副本复制给子类原型
> }
> function ParentType(name) {
>     this.name = name;
>     this.colors = ["red", "blue", "green"];
> }
> ParentType.prototype.sayName = function() {
>     alert(this.name);
> }
>
> function SonType(name, age) {
>     ParentType.call(this, name);
>     this.age = age;
> }
> inheritPrototype(SonType, ParentType);
> SonType.prototype.sayAge = function() {
>     alert(this.age);
> }
> ```





