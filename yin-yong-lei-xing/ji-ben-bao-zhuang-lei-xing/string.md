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
>
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
> > ##### 传入负值：
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

> #### toLowerCase\(\) 和 toUpperCase\(\)
>
> ```js
> var stringValue = "hello world";
> alert(stringValue.toUpperCase());    // "HELLO WORLD"
> alert(stringValue.toLowerCase());    // "hello world"
> ```
>
> #### toLocaleLowerCase\(\) 和 toLocaleUpperCase\(\)
>
> ##### 少数语言会为Unicode大小写转换应用特殊的规则，此方法可保证转换正确
>
> ```js
> var stringValue = "hello world";
> alert(stringValue.toLocaleUpperCase());    // "HELLO WORLD"
> alert(stringValue.toLocaleLowerCase());    // "hello world"
> ```

### 字符串模式匹配：

> #### match\(\) :
>
> > ##### 和调用RegExp的exec\(\)本质相同传入字符串或RegExp对象
> >
> > ```js
> > var text = "cat, bat, sat, fat";
> > var pattern = /.at/;
> >
> > var matches = text.match(pattern); // 等同于 pattern.exec(text)
> > alert(matches.index);        // 0
> > alert(matches.input);        // "cat, bat, sat, fat"
> > alert(pattern[0]);           // "cat"
> > alert(pattern.lastIndex);    // 书中有误，数组中无此元素
> > ```
>
> #### search\(\) :
>
> > ##### 传入字符串或RegExp对象，返回索引
> >
> > ```js
> > var text = "cat, bat, sat, fat";
> > var pattern = /.at/;
> > alert(text.search(pattern));    // 0
> > pattern = /at/;
> > alert(text.search(pattern));    // 1
> > ```
>
> #### replace\(\) :
>
> > ##### 第一个参数是字符串或RegExp对象，第二个是要用来替换的字符串或一个函数
> >
> > ##### 如果第一个参数是字符串，只会替代第一个匹配对象
> >
> > ##### 想要替换所有子字符串，第一个参数需传入RegExp对象，且要指定g标志
> >
> > ```js
> > var text = "cat, bat, sat, fat";
> > var result = text.replace("at", "ond");
> > alert(result);    // "cond, bat, sat, fat"
> >
> > var result = text.replace("/at/g", "ond");
> > alert(result);    // "cond, bond, sond, fond"
> > ```
> >
> > ##### 第二个参数如果是字符串，可以使用一些特殊的字符：
> >
> > | 字符序列 | 替换文本 |
> > | :---: | :--- |
> > | $$ | $ |
> > | $& | 匹配整个模式的子字符串。与RegExp.lastMatch的值相同 |
> > | $' |  匹配的子字符串之前的子字符串。与RegExp.leftContext的值相同 |
> > | $、 |  匹配的子字符串之后的子字符串。与RegExp.rightContext的值相同 |
> > | $n |  匹配第n捕获组的子字符串，其中n等于0~9。例如，$1是匹配第一个捕获组的子字符串，$2是匹配第二个捕获组的子字符串，以此类推。如果正则表达式中没有定义捕获组，则使用空字符串 |
> > | $nn | 匹配第nn个捕获组的子字符串，其中nn等于01~99。例如，$01是匹配第一个捕获组的子字符串，$02是匹配第二个捕获组的子字符串，以此类推。如果正则表达式中没有定义捕获组，则使用空字符串 |
> >
> > ```js
> > var text = "cat, bat, sat, fat";
> > var result = text.replace(/(.at)/g, "word($1)");
> > alert(result);    // "word(cat), word(bat), word(sat), word(fat)"
> > ```
> >
> > ##### 第二个参数如果是函数，可以实现更精细的操作：
> >
> > ```js
> > function htmlEscape(text) {
> >     return text.replace(/[<>"&]/g, function(match, pos, originalText) {
> >             switch(match){
> >                     case "<":
> >                         return "$lt;";
> >                     case ">":
> >                         return "$gt;";
> >                     case "&":
> >                         return "$amp;";
> >                     case "\"":
> >                         return "$quot;";
> >                 }
> >         });
> >     }
> > alert(htmlEscape("<p class=\"greeting\">Hello world!</p>"));    
> > // $lt;p class=$quot;greeting$quot;$gt;Hello world!$lt;/p$gt;
> > ```
> >
> > ```js
> > name = 'aaa bbb ccc';
> > var upperWord = name.replace(/\b\w+\b/g, function(word){
> >   return word.substring(0,1).toUpperCase()+word.substring(1);
> > });
> > alert(upperWord);
> > ```
>
> #### split\(\) :
>
> > ```js
> > var colorText = "red, blue, green, yellow";
> > var colors1 = colorText.split(",");    // ["red","blue", "green", "yellow"]
> > var colors2 = colorText.split(",", 2); // ["red", "blue"]
> > ```
> >
> > ##### 使用正则 : 
> >
> > ```js
> > var str="a|b|c|";
> > var arr=str.split(/\W+/);
> > alert(arr); [a,b,c]
> > ```

### localeCompare\(\) 方法：

> ##### 按照字母表中的位置比较大小
>
> ```js
> var stringValue = "b";
> alert(stringValue.localeCompare("a"));    // 1
> alert(stringValue.localeCompare("b"));    // 0
> alert(stringValue.localeCompare("c"));    // -1
> ```

### fromCharCode\(\) 方法：

> 是charCodeAt\(\)方法的反操作，将字符编码转换为字符串
>
> ```js
> alert(String.fromCharCode(104, 101, 108, 108, 111));    // "hello"
> ```

### HTML方法：

> #### 作者建议：尽量不使用这些方法，因为它们创建的标记通常无法表达语义。

> | 方　　法 | 输出结果 |
> | :--- | :--- |
> | anchor（name） | &lt;a name = "name"&gt;string&lt;/a&gt; |
> | big\(\) | &lt;big&gt;string&lt;/big&gt; |
> | bold\(\) | &lt;b&gt;string&lt;/b&gt; |
> | fixed\(\) | &lt;tt&gt;string&lt;/tt&gt; |
> | fontcolor（color） | &lt;font color="color"&gt;string&lt;/font&gt; |
> | fontsize（size） | &lt;font size="size"&gt;string&lt;/font&gt; |
> | italics\(\) | &lt;i&gt;string&lt;/i&gt; |
> | link（url） | &lt;a href=“url"&gt;string&lt;/a&gt; |
> | small\(\) | &lt;small&gt;string&lt;/small&gt; |
> | strike\(\) | &lt;strike&gt;string&lt;/strike&gt; |
> | sub\(\) | &lt;strike&gt;string&lt;/strike&gt; |
> | sup\(\) | a&lt;sup&gt;string&lt;/sup&gt; |









