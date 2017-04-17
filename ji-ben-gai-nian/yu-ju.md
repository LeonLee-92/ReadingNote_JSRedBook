#### if 语句

> ```js
> if(i > 25){
>     console.log("123");
> }else{
>     console.log("456");
> }
> ```

#### do-while 语句

> ```js
> var i = 0;
> do{
>     i +=2;
> } while(i < 10);
> ```

#### while 语句

> ```js
> var i = 0;
> while(i < 10){
>     i += 2;
> }
> ```

#### for 语句

> ```js
> var count = 10;
> var i;
> for(i = 0; i < count; i++){
>     ...
> }
>
> // 无限循环的for语句
> for(;;){
>     
> }
> ```

#### for-in语句

> ```js
> for (var propName in window){
>     console.log(propName);
> }
> ```

#### label语句

> ##### 主要用于跳出多层循环
>
> ```js
>   var num = 0;
>  
>  outPoint:
>     for (var i = 0 ; i < 10 ; i++){
>          for (var j = 0 ; j < 10 ; j++){
>               if( i == 5 && j == 5 ){
>                     break outPoint;
>               }
>          num++;
>          }
>     }
>  console.log(num);   // 55
> ```

#### break 和 continue 语句

> ```js
> var num = 0;
> for (var i = 1; i < 10; i++){
>     if(i % 5 == 0){
>         break;
>     } 
>     num++;
> }
> console.log(num);   // 4
> ```
>
> ```js
> var num = 0;
> for (var i = 1; i < 10; i++) {
>     if (i % 5 == 0) {
>         continue;
>     }
>     num++;
> }
> console.log(num);    // 8
> ```
>
> ##### 结合label语句：
>
> > ```js
> > var num = 0;
> >
> > outermost:
> > for(var i = 0; i < 10; i++){
> >     for(var j = 0; j < 10; j++){
> >         if(i == 5 && j == 5) {
> >             break outermost;
> >         }
> >         num++;
> >     }
> > }
> > console.log(num);    // 55
> > ```
> >
> > ```js
> > var num = 0;
> >
> > outermost:
> > for(var i = 0; i < 10; i++){
> >     for(var j = 0; j < 10; j++){
> >         if(i == 5 && j == 5) {
> >             continue outermost;
> >         }
> >         num++;
> >     }
> > }
> > console.log(num);    // 95
> > ```

#### with 语句

> ##### 用途：简化多次编写同一个环境对象
>
> ##### 规则：
>
> \*严格模式下不允许使用
>
> ```js
> var qs = location.search.substring(1);
> var hostName = location.hostname;
> var url = location.href;
> ```
>
> ```js
> with(location){
>     var qs = search.substring(1);
>     var hostName = hostname;
>     var url = href;
> }
> ```

#### switch 语句

> ```js
> var i = 100;
> switch(i) {
>     case 25:
>     case 35:
>         console.log("25 or 35");
>         break;
>     case 45:
>         console.log("45");
>         break;        
>     default:
>         console.log("other");
> }
> // other
> ```
>
> ###### switch中可以使用任何类型：
>
> ```js
> switch("hello world") {
>     case "hello" + " world":
>         console.log("111");
>         break;
>     case "goodbye":
>         console.log("222");
>         break;
>     default:
>         console.log("other");
> }
> // 111
> ```
>
> ```js
> var num = 25;
> switch (true) {
>     case num < 0:
>         console.log("111");
>         break;
>     case num > 0:
>         console.log("222");
>         break;
>     default:
>         console.log("other");
> }
> // 222
> ```

#### 



