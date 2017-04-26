```js
var person = new Object()
person.name = "abc";
person.sayName = function() {
    alert(this.name);
}
```

```js
var person = {
    name: "abc",
    sayName: function() {
        alert(this.name);       
    }
}
```

### 属性类型：

> #### 数据属性：
>
> > ##### 四个特性：
> >
> > > ##### \[\[Configurable\]\]:能否通过delete删除属性从而重新定义属性，能否修改属性的特性，能否把属性修改为访问器属性。
> > >
> > > ##### \[\[Enumerable\]\]:能否通过for-in循环返回属性。
> > >
> > > ##### \[\[Writable\]\]：表示能否修改属性的值。
> > >
> > > ##### \[\[Value\]\]：包含这个属性的数据值。这个特性的默认值为undefined。
> >
> > #### Object.defineProperty\(\)
> >
> > > ```js
> > > var person = new Object()
> > > person.name = "abc";
> > > Object.defineProperty(person, "name", {
> > >       configurable: false,
> > >       value: "def"
> > > });
> > > alert(person.name);      // "def"
> > > delete person.name;
> > > alert(person.name);      // "def"
> > > ```
> > >
> > > ```js
> > > var person = new Object()
> > > person.name = "abc";
> > > Object.defineProperty(person, "name", {
> > >       writable: false,
> > >       value: "def"
> > > });
> > > alert(person.name);      // "def"
> > > person.name = "abc";
> > > alert(person.name);      // "def"
> > > ```
> > >
> > > ##### 可以多次调用Object.defineProperty\(\)方法修改同一个属性，但是吧configurable设置为false后就不可以了
>
> #### 访问器属性：
>
> > ##### 四个特性：
> >
> > > ##### \[\[Configurable\]\]:能否通过delete删除属性从而重新定义属性，能否修改属性的特性，能否把属性修改为数据属性。
> > >
> > > ##### \[\[Enumerable\]\]:表示能否通过for-in循环返回属性。
> > >
> > > ##### \[\[Get\]\]：在读取属性时调用的函数。默认值为undefined。
> > >
> > > ##### \[\[Set\]\]：在写入属性时调用的函数。默认值为undefined。
> >
> > #### Object.definedProperty\(\)
> >
> > > ```js
> > > var book = {
> > >     _year: 2004,
> > >     edition: 1
> > > };
> > > Object.defineProperty(book, "year", {
> > >     get: function() {
> > >         return this._year;
> > >     },
> > >     set: function(newValue) {
> > >         if(newValue > 2004) {
> > >             this._year = newValue;
> > >             this.edition += newValue - 2004;
> > >         }
> > >     }
> > > });
> > > book.year = 2005;
> > > alert(book.edition);    // 2
> > > ```
>
> #### 定义多个属性：
>
> > ##### Object.defineProperties\(\):
> >
> > ```js
> > var book = {};
> > Object.defineProperties(book, {
> >       _year: {      // 数据属性
> >             value: 2004
> >       },
> >       edition: {      // 数据属性
> >             value: 1
> >       },
> >       year: {      // 访问器属性
> >             get: function() {
> >                   return this._year;
> >             },
> >             set: function() {
> >                   if(newValue > 2004) {
> >                         this._year = newValue;
> >                         this.edition += newValue - 2004;
> >                   }
> >             }
> >       }
> > });
> > ```
>
> #### 读取属性的特性：
>
> > ##### Object.getOwnPropertyDescriptor\(\):
> >
> > ```js
> > var book = {};
> > Object.defineProperties(book, {
> >       _year: {      // 数据属性
> >             value: 2004
> >       },
> >       edition: {      // 数据属性
> >             value: 1
> >       },
> >       year: {      // 访问器属性
> >             get: function() {
> >                   return this._year;
> >             },
> >             set: function() {
> >                   if(newValue > 2004) {
> >                         this._year = newValue;
> >                         this.edition += newValue - 2004;
> >                   }
> >             }
> >       }
> > });
> >
> > var descriptor = Object.getOwnPropertyDescriptor(book, "_year");
> > alert(descriptor.value);            // 2004
> > alert(descriptor.configurable);      // false
> > alert(descriptor.get);            // undefined
> >
> > descriptor = Object.getOwnPropertyDescriptor(book, "year");
> > alert(descriptor.value);            // undefined
> > alert(descriptor.enumerable);      // false
> > alert(descriptor.get);            // function
> > ```



