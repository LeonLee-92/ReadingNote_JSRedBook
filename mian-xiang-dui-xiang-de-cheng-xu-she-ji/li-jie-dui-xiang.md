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
> > ##### \[\[Configurable\]\]:能否通过delete删除属性从而重新定义属性，能否修改属性的特性，能否把属性修改为访问器属性。
> >
> > ##### \[\[Enumerable\]\]:能否通过for-in循环返回属性。
> >
> > ##### \[\[Writable\]\]：表示能否修改属性的值。
> >
> > ##### \[\[Value\]\]：包含这个属性的数据值。这个特性的默认值为undefined。
>
> #### Object.defineProperty\(\)
>
> > ```js
> > var person = new Object()
> > person.name = "abc";
> > Object.defineProperty(person, "name", {
> >       writable: false,
> >       value: "def"
> > });
> > alert(person.name);      // "def"
> > delete person.name;
> > alert(person.name);      // "def"
> > ```



