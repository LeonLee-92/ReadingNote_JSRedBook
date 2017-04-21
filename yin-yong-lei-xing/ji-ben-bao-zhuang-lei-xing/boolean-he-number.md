## Boolean：

> ### Boolean的方法：
>
> > ##### valueof\(\) 返回基本类型值true或false
> >
> > ##### toString\(\) 返回字符串"true"或"false"
>
> ### Boolean对象 和 基本类型Boolean值的区别：
>
> > #### 在关系表达式中：
> >
> > ```js
> > var falseObject = new Boolean(false);
> > var result = falseObject && true;  // 基本包装类型转boolean基本类型永远返回true
> > alert(result);    // true
> >
> > var falseValue = false;
> > result = falseValue && true;
> > alert(result);    // false
> > ```
> >
> > #### typeof\(\)
> >
> > ```js
> > var falseObject = new Boolean(false);
> > var falseValue = false;
> > alert(typeof falseObject);    //object
> > alert(typeof falseValue);    //boolean
> > ```
> >
> > #### instanceof\(\)
> >
> > ```js
> > var falseObject = new Boolean(false);
> > var falseValue = false;
> > alert(falseObject instanceof Boolean);    //true
> > alert(falseValue instanceof Boolean);    //false
> > ```
>
> ### 作者建议：永远不要使用Boolean对象

## Number：

> ### Number的方法：
>
> > #### 继承方法：
> >
> > > ##### valueOf\(\) 返回基本类型数值
> > >
> > > ##### toString\(\) 返回基本数值对应的字符串，可传递进制参数
> >
> > #### 转字符串方法：
> >
> > > toFixed\(\) ：四舍五入，可以表现0到20位小数
> > >
> > > ```js
> > > var num = 10.005;
> > > alert(num.toFixed(2));    // "10.01"
> > > ```
> > >
> > > toExponential\(\) ：转为e表示法，传入小数位数
> > >
> > > ```js
> > > var num = 10;
> > > alert(num.to/exponential(1));    // "1.0e+1"
> > > ```
> > >
> > > toPrecision\(\)：转为最合适的格式，传入所有数字位数（不包括指数部分）
> > >
> > > ```js
> > > var num = 99;
> > > alert(num.toPrecision(1));    // "1e+2"
> > > alert(num.toPrecision(2));    // "99"
> > > alert(num.toPrecision(3));    // "99.0"
> > > ```
> >
> > #### 与基本类型的不同：
> >
> > > ```js
> > > var numberOjbect = new Number(10)；
> > > var numberValue = 10;
> > > alert(typeof numberObject);    // "object"
> > > alert(typeof numberValue);    // "number"
> > > alert(numberObject instanceof Number);    // true
> > > alert(numberValue instanceof Number);    // false
> > > ```





