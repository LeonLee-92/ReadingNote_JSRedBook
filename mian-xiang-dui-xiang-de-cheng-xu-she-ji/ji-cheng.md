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
> > #### 父类的实例属性会继承为子类的原型属性
> >
> > ```js
> > function ParentType() {
> >     this.colors = ["red", "blue", "green"];
> > }
> > ```



