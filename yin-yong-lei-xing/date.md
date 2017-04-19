#### 创建Date对象：

> ##### new Date\(\) :
>
> ```js
> var now = new Date();           // 当前时间
> var someDate = new Date(1000);  // 可传入从1970年1月1日起经过的毫秒数
> alert(now);       // Wed Apr 19 2017 11:18:44 GMT+0800 (CST)
> alert(someDate);  // Thu Jan 01 1970 08:00:01 GMT+0800 (CST)
> ```
>
> ##### Date.parse\(\) :
>
> ```js
> var someDate = new Date(Date.parse("3453542"));  // 传入无效字符串，Date.parse将返回NaN
> alert(someDate);    // Invalid Date
> someDate = new Date(Date.parse("May 25, 2016"));
> alert(someDate);  // Wed May 25 2016 00:00:00 GMT+0800 (CST)
> // 直接传入new Date()中，底层会自动调用Date.parse
> someDate = new Date("May 25, 2016");
> alert(someDate);  // Wed May 25 2016 00:00:00 GMT+0800 (CST)
> ```
>
> ##### Date.UTC\(\) :
>
> ##### 依次传入年月日分秒，年月必传
>
> ##### 特别注意：月份从零开始
>
> ```js
> var someDate = new Date(Date.UTC(2000, 0));  //2000年1月
> alert(someDate);   // Sat Jan 01 2000 08:00:00 GMT+0800 (CST)
> someDate = new Date(Date.UTC(2005, 4, 5, 17, 55, 55));  //2005年5月5日 17:55:55
> alert(someDate);   // Fri May 06 2005 01:55:55 GMT+0800 (CST)
> // 直接传入new Date()中，底层会自动调用Date.UTC
> someDate = new Date(2005, 4, 5, 17, 55, 55);  //2005年5月5日 17:55:55
> alert(someDate);   // Fri May 06 2005 01:55:55 GMT+0800 (CST)
> ```
>
> ##### Date.now\(\) :返回毫秒数
>
> ```js
> var start = Date.now();
> for(var i=100;i--;i>0) {
>     console.log(123123);
> }
> var stop = Date.now();
> alert(stop);   // 1492574024681
> alert(start);  // 1492574024672
> alert(stop - start);   // 11 用时11毫秒
> ```

##### 继承的方法：

> ##### toString\(\) :
>
> ```js
> var time = new Date();
> alert(time.toString());   // Wed Apr 19 2017 13:27:14 GMT+0800 (CST) 
> ```
>
> ##### toLocaleString\(\) :
>
> ```js
> var time = new Date();
> alert(time.toLocaleString());  // 2017/4/19 下午1:26:51
> ```
>
> ##### valueOf\(\) :
>
> ```js
> var date1 = new Date(2007, 0, 1);
> var date2 = new Date(2007, 1, 1);
> alert(date1 < date2);  // true
> alert(date1 > date2);  // false
> ```

##### 格式化方法：

>



