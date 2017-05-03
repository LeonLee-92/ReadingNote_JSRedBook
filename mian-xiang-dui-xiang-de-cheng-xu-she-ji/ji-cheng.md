### 原型链

> ```js
> function ParentType() {
>     this.property = true;
> }
> ParentType.prototype.getParentValue = function() {
>     return this.property;
> };
>
>
> function SonType() {
>     this.sonProperty = false;
> }
> SonType.prototype = new ParentType();    // 继承
>
>
>
> SonType.prototype.getSonValue = function() {
>     return this.sonProperty;
> }
>
> var instance = new SonType();
> alert(instance.getParentValue()); 
> ```



