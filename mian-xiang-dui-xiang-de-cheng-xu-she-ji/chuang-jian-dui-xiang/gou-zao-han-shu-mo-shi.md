```js
function Person(name, age, job) {
    this.name = name;
    this.age = age;
    this.job = job;
    this.sayName = function() {
        alert(this.name);
    }
}

var person1 = new Person("liyan", 18, "teacher");
var person2 = new Person("jiangxiaoni", 36, "farmer");
```

#### 与工厂模式的区别：

> 1. ##### 没有显式地创建对象；
> 2. ##### 直接将属性和方法赋给了this对象；
> 3. ##### 没有return语句。

#### 使用new操作符经历的四个步骤：

> 1. ##### 创建一个新对象
> 2. ##### 将构造函数的作用域赋给新对象（因此this就指向了这个新对象）
> 3. ##### 执行构造函数中的代码（为这个新对象添加属性）
> 4. ##### 返回新对象

#### 对象类型：

> #### 对象的constructor属性最初是用来标识对象类型的：

> ```js
> alert(person1.constructor == Person);    // true
> alert(person2.constructor == Person);    // true
> alert(person2.constructor == Object);    // false
> ```
>
> #### 但instanceoof操作符要更可靠一些：
>
> ```js
> alert(person1.constructor == Object);    // true
> alert(person1.constructor == Person);    // true
> alert(person2.constructor == Object);    // true
> alert(person2.constructor == Person);    // true
> ```

#### 构造函数与普通函数：

> ##### 任何函数，通过new操作符来调用，那它就是构造函数
>
> ##### 任何函数，不通过new操作符来调用，那它就是普通函数
>
> ```js
> // 构造函数
> var person = new Person("liyan", 18, "teacher");
> person.sayName();    // "liyan"
> // 普通函数
> Person("sunjian", 52, "farmer");
> window.sayName();    // "sunjian"
> // 在另一个对象的作用域中调用
> var o = new Object();
> Person.call(o, "liyan", 18, "Doctor");
> o.sayName();     // "liyan"
> ```

#### 构造函数模式存在的问题：

> ##### 主要问题：每个方法在每个实例上都要重新创建
>
> > ##### 等同于：
> >
> > > ```js
> > > function Person(name, age, job) {
> > >     this.name = name;
> > >     this.age = age;
> > >     this.job = job;
> > >     
> > >     this.sayName = new Function("alert(this.name)");
> > > }
> > > ```
>
> > ##### 优化：
> >
> > > ```js
> > > function Person(name, age, job) {
> > >     this.name = name;
> > >     this.age = age;
> > >     this.job = job;
> > >     
> > >     this.sayName = sayName;
> > > }
> > > function sayName() {
> > >     alert(this.name);
> > > }
> > > ```
> > >
> > > ##### 依旧存在问题：
> > >
> > > ##### 1.在全局定义的函数只被某个类调用，这让全局作用域名不副实
> > >
> > > ##### 2.如果对象定义很多方法，就要定义很多全局函数，封装性遭到破坏









