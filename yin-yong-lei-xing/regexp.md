#### 书写格式：

> * #### var expression = /pattern/flags ;
> * #### var pattern = new RegExp\("pattern", "flags"\);
>
> > ##### patttern :正则表达式
> >
> > ##### flags :一个或多个匹配模式标志

#### 匹配模式：

> #### g : global模式，匹配到第一个结果不停止
>
> #### i : case-insensitive模式，忽略大小写
>
> #### m : multiline模式，多行匹配
>
> ```js
> var pattern1 = /at/g;    // 匹配字符串中所有“at”的实例
> var pattern2 = /[bc]at/i;  // 匹配第一个“bat”或“cat”，不区分大小写
> var pattern3 = /.at/gi;    // 匹配所有以“at”结尾并由3个字符组成的实例，不区分大小写
> ```

#### 元字符：

> #### （ \[  {    ^  $  \|  ） ?  \*  +  .  \]  }
>
> ##### 正则中这些字符需要使用 "\" 符号转译
>
> ```js
> var pattern = /\[bc\]at/i;   // 匹配第一个 “[bc]at” ，不区分大小写
> ```

#### 两种方式对比：

> | 字面量模式（/pattern/flags ） | 等价字符串（new RegExp\("pattern", "flags"\)） |
> | :---: | :---: |
> | /\\[bc\\]at/ | "\\[bc\\]at" |
> | /.at/ | ".at" |
> | /name\/age/ | "name\/age" |
> | /\d.\d{l,2}/ | "\d.\d\[l,2}" |
> | /\w\hello\123/ | "\w\hello\123" |
>
> #### 不同：
>
> ##### 字面量创建会共享一个RegExp实例，而构造函数每次都会返回新的实例

#### RegExp实例属性：

> ##### □　global:           布尔值，是否设置  g  标志。
>
> ##### □　ignoreCase:  布尔值，是否设置   i  标志。
>
> ##### □　multiline:       布尔值，是否设置 m 标志。
>
> ##### □　lastIndex:       整数，搜索下一个匹配项的字符从0算起的位置。
>
> ##### □　source:           正则表达式的字符串表示，按照字面量形式返回。

#### RegExp实例方法：

> #### exec\(\) :
>
> > ##### 匹配捕获组：
> >
> > ```js
> > var text = "mom and dad and baby";
> > var pattern = /mom( and dad( and baby)?)?/gi;
> > var matches = pattern.exec(text);
> > alert(matches.index);  // 0
> > alert(matches.input);  // "mom and dad and baby"
> > alert(matches[0]);     // "mom and dad and baby"
> > alert(matches[1]);     // " and dad and baby"
> > alert(matches[2]);     // " and baby"
> > ```
> >
> > ##### 不带g的模式，永远返回第一个匹配项
> >
> > ```js
> > var test = "cat, bat, sat, fat";
> > var pattern1 = /.at/;
> >
> > var matches = pattern1.exec(text);
> > alert(matches.index);       // 0
> > alert(matches[0]);          // cat
> > alert(pattern1.lastIndex);  // 0
> >
> > matches = pattern1.exec(text);
> > alert(matches.index);       // 0
> > alert(matches[0]);          // cat
> > alert(pattern1.lastIndex);  // 0
> > ```
> >
> > ##### 带g的模式，每次调用exec\(\)会接着匹配
> >
> > ```js
> > var test = "cat, bat, sat, fat";
> > var pattern1 = /.at/g;
> >
> > var matches = pattern1.exec(text);
> > alert(matches.index);       // 0
> > alert(matches[0]);          // cat
> > alert(pattern1.lastIndex);  // 3
> >
> > matches = pattern1.exec(text);
> > alert(matches.index);       // 5
> > alert(matches[0]);          // bat
> > alert(pattern1.lastIndex);  // 8
> > ```
>
> #### test\(\) :
>
> ```js
> var text = "000-00-0000";
> var pattern = /\d{3}-\d{2}-\d{4}/;
> if (pattern.test(text)) {
>     alert(111);   // 成功弹出
> }
> ```
>
> #### toString\(\) 和 toLocaleString\(\)都返回正则表达式字面量
>
> #### valueOf\(\)返回正则表达式本身

#### 构造函数属性：

> #### 主要属性：
>
> > ##### 这些属性基于所执行的最近一次正则表达式操作而变化
> >
> > | 长属性名 | 短属性名 | 说明 |
> > | :---: | :---: | :---: |
> > | input | $\_ | 最近一次要匹配的字符串 |
> > | lastMatch | $& | 最近一次的匹配项 |
> > | lastParen | $+ | 最近一次匹配的捕获组 |
> > | leftContext | $、 | input字符串中lastMatch之前的文本 |
> > | multiline | $\* | 布尔值，是否所有表达式都使用多行 |
> > | rightContext | $' | Input字符串中lastMatch之后的文本 |
> >
> > ![](/assets/01427.jpg)
>
> #### 用于存储捕获组的属性：
>
> > #### RegExp.$1、RegExp.$2  …  RegExp.$9，分别用于存储第一、第二…第九个匹配的捕获组
> >
> > ![](/assets/01602.jpg)

#### 



