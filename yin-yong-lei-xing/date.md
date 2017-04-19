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

#### 继承的方法：

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

#### 格式化方法：

> ##### toDateString\(\) :
>
> ```
> alert((new Date()).toDateString());   // Wed Apr 19 2017
> ```
>
> ##### toTimeString\(\) ：
>
> ```
> alert((new Date()).toTimeString());   // 13:45:23 GMT+0800 (CST)
> ```
>
> ##### toLocaleDateString\(\) ：
>
> ```
> alert((new Date()).toLocaleDateString());   // 2017/4/19
> ```
>
> ##### toLocaleTimeString\(\) ：
>
> ```
> alert((new Date()).toLocaleTimeString());   // 下午1:46:42
> ```
>
> ##### toUTCString\(\) ：
>
> ```
> alert((new Date()).toUTCString());   // Wed, 19 Apr 2017 05:47:26 GMT
> ```

#### 其他方法：

> ##### getTime\(\)    返回表示日期的毫秒数；与valueOf\(\)方法返回的值相同
>
> ##### setTime\(毫秒\)    以毫秒数设置日期，会改变整个日期
>
> ##### getFullYear\(\)    取得4位数的年份（如2007而非仅07）
>
> ##### getUTCFullYear\(\)    返回UTC日期的4位数年份
>
> ##### setFullYear\(年\)    设置日期的年份。传入的年份值必须是4位数字（如2007而非仅07）
>
> ##### setUTCFullYear\(年\)    设置UTC日期的年份。传入的年份值必须是4位数字（如2007而非仅07）
>
> ##### getMonth\(\)    返回日期中的月份，其中0表示一月，11表示十二月
>
> ##### getUTCMonth\(\)    返回UTC日期中的月份，其中0表示一月，11表示十二月
>
> ##### setMonth（月）    设置日期的月份。传入的月份值必须大于0，超过11则增加年份
>
> ##### setUTCMonth（月）    设置UTC日期的月份。传入的月份值必须大于0，超过11则增加年份
>
> ##### getDate\(\)    返回日期月份中的天数（1到31）
>
> ##### getUTCDate\(\)    返回UTC日期月份中的天数（1到31）
>
> ##### setDate（日）    设置日期月份中的天数。如果传入的值超过了该月中应有的天数，则增加月份
>
> ##### setUTCDate（日）    设置UTC日期月份中的天数。如果传入的值超过了该月中应有的天数，则增加月份
>
> ##### getDay\(\)    返回日期中星期的星期几（其中0表示星期日，6表示星期六）
>
> ##### getUTCDay\(\)    返回UTC日期中星期的星期几（其中0表示星期日，6表示星期六）
>
> ##### getHours\(\)    返回日期中的小时数（0到23）
>
> ##### getUTCHours\(\)    返回UTC日期中的小时数（0到23）
>
> ##### setHours（时）    设置日期中的小时数。传入的值超过了23则增加月份中的天数
>
> ##### setUTCHours（时）    设置UTC日期中的小时数。传入的值超过了23则增加月份中的天数
>
> ##### getMinutes\(\)    返回日期中的分钟数（0到59）
>
> ##### getUTCMinutes\(\)    返回UTC日期中的分钟数（0到59）
>
> ##### setMinutes（分）    设置日期中的分钟数。传入的值超过59则增加小时数
>
> ##### setUTCMinutes（分）    设置UTC日期中的分钟数。传入的值超过59则增加小时数
>
> ##### getSeconds\(\)    返回日期中的秒数（0到59）
>
> ##### getUTCSeconds\(\)    返回UTC日期中的秒数（0到59）
>
> ##### setSeconds（秒）    设置日期中的秒数。传入的值超过了59会增加分钟数
>
> ##### setUTCSeconds（秒）    设置UTC日期中的秒数。传入的值超过了59会增加分钟数
>
> ##### getMilliseconds\(\)    返回日期中的毫秒数
>
> ##### getUTCMilliseconds\(\)    返回UTC日期中的毫秒数
>
> ##### setMilliseconds（毫秒）    设置日期中的毫秒数
>
> ##### setUTCMilliseconds（毫秒）    设置UTC日期中的毫秒数
>
> ##### getTimezoneOffset\(\)    返回本地时间与UTC时间相差的分钟数。例如，美国东部标准时间返回300。
>
> ##### 在某地进入夏令时的情况下，这个值会有所变化



