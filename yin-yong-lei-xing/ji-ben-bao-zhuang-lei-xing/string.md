> #### valueOf\(\)、toLocaleString\(\)和toString\(\)方法都放回字符串基本类型
>
> #### length属性：字符串的字符数量，双字节也算一个字符。

### 字符方法：

> ##### 方括号索引：
>
> ```js
> var stringValue = "hello world";
> alert(stringValue[1])    // "e"
> ```
>
> ##### chartAt\(\) : 索引字符
>
> ```js
> var stringValue = "hello world";
> alert(stringValue.charAt(1))    // "e"
> ```
>
> ##### charCodeAt\(\) : 索引字符对应的编码
>
> ```js
> var stringValue = "hello world";
> alert(stringValue.charCodeAt(1))    // "101"
> ```

### 字符串操作方法：

> #### concat\(\) : 拼接字符串
>
> > ```js
> > var stringValue = "hello ";
> > var result = stringValue.concat("world", "!");
> > alert(result);        // "hello world!"
> > alert(stringValue);    // "hello "
> > ```
> >
> > ##### 我们通常使用+符号来代替：
> >
> > ```
> > var stringValue = "hello ";
> > var result = stringValue + "world" + "!";
> > alert(result);    // "hello world!"
> > ```

> #### slice\(\)、substr\(\)和substring\(\)：获得子字符串方法
>
> > ##### 第一个参数： 起始位置，第二个参数：到哪里结束（可省略）
> >
> > ```js
> > var stringValue = "hello world";
> > alert(stringValue.slice(3));         // "lo world"
> > alert(stringValue.substring(3));     // "lo world"
> > alert(stringValue.substr(3));        // "lo world"
> > alert(stringValue.slice(3, 7));      // "lo w"
> > alert(stringValue.substring(3, 7));  // "lo w"
> > alert(stringValue.substr(3, 7));     // "lo worl"   第二个参数传递的是长度
> > ```
> >
> > #####  传入负值：
> >
> > > #### 注意：书中的规则有误！
> > >
> > > ##### slice\(\) : 传入的负值与length相加
> > >
> > > ##### substring\(\) : 传入的第一个负值与length相加，第二个负值转换为0
> > >
> > > ##### substr\(\) : 传入的负值统统转换为0
> > >
> > > ```js
> > > var stringValue = "hello world";
> > > alert(stringValue.slice(-3));        // "rld"
> > > alert(stringValue.substr(-3));       // "rld"
> > > alert(stringValue.substring(-3));    // "hello world"
> > > alert(stringValue.slice(3, -4));     // "lo w"
> > > alert(stringValue.substr(3, -4));    // ""
> > > alert(stringValue.substring(3, -4)); // "hel"
> > > ```

### 字符串位置方法：

> #### indexOf\(\) 和 lastIndexOf\(\) 
>
> ```js
> var stringValue = "hello world";
> alert(stringValue.indexOf("o"));     // 4
> alert(stringValue.lastIndexOf("o")); // 7
> ```
>
> #### 第二个参数：从指定位置开始查找
>
> ```js
> var stringValue = "hello world";
> alert(stringValue.indexOf("o", 6));     // 7
> alert(stringValue.lastIndexOf("o", 6)); // 4
> ```
>
> #### 例子：
>
> ![](/assets/00405.jpg)

### 创建副本：

> #### trim\(\) 方法：会删除前置和后缀的所有空格
>
> ```js
> var stringValue = "  hello world  ";
> var trimedStr = stringValue.trim();
> alert(stringValue);    // "  hello world  "
> alert(stringStr);      // "hello world"
> ```

### 字符串大小写转换：

> toLowerCase\(\) 和 toUpperCase\(\)















