### JavaScript

#### JavaScript 诞生前夕
1994年，美国网景公司开发的浏览器Netscape  0.9发布，虽然仍是beta版本，该浏览器获得重大成功，成为当时最热门的浏览器。但是这个版本的浏览器，只能用来浏览HTML网页，无法让网页和浏览器进行互动。比如注册页面需要输入两次密码进行确认，浏览器无法判断用户的两次密码是否一致，只能提交到服务器进行判断。对于拨号上网时代来说，这是非常低效的。

1995年，Netscape 公司招募了 Brendan Eich，最初网景公司的想法是将 Scheme 这门已有的语言嵌入到浏览器作为脚本语言。但在这之前，Netscape 和 Sun 公司达成了协议，将Java语言嵌入到浏览器，但因为Java语言太复杂，于是最后做出决策，嵌入网页的脚本语言必须「看上去和Java相似」，但必须比Java简单，让新手和业余的网页设计师也可以轻松上手。(Java was intended to be used by “real programmers”, not, for example, by lowly Web designers)

#### JavaScript诞生

最初这门语言的作用，仅仅是用来处理一些原本用服务器语言处理的表单验证等操作，同时为了赶上 Netscape Navigator 2.0的Beta版，Brendan Eich 仅花了10天时间，就完成了这门语言的原型设计。他知道他可能会存在错误或遗漏，因此他设计的这门语言具有很强的可塑性和扩展性，从而可以增强功能，并解决局限性。

最初这门语言命名为 Mocha，因为商标的关系，在Netscape Navigator 2.0的Beta版中改名为LiveScript。后来为了让这门语言搭上Java这个编程语言“热词”，又将这门语言改名为JavaScript，日后这成为了大众对这门语言有诸多误解的原因之一。

#### JavaScript 与 ECMAScript

JavaScript推出之后大获成功，被全世界用户大量使用，1996年8月，微软公司也退出了自己的脚本语言JScript，为了压制微软，1996年11月，网景公司决定将 JavaScript 提交给标准化组织 ECMA，希望这种语言能够成为浏览器脚本语言的国际标准。ECMA以JavaScript语言为基础制定了浏览器脚本语言标准规范ECMA-262，并将这种脚本语言称为ECMAScript。

简单来说：JavaScript是ECMAScript的实现，ECMAScript是JavaScript的标准，ActionScript和JScript也都是ECMAScript规范的实现语言。

#### JavaScript 运行时（Runtime）

JavaScript 的运行环境，对于网页来说，JavaScript的Runtime是浏览器，这时JavaScript就可以操作DOM和BOM了。而对于服务器来说，JavaScript的Runtime就是Node.js，Node.js提供了文件系统、网络请求等基础功能。




#### JavaScript 语法
- 区分大小写

- 变量都是弱类型

- 行尾的分号可有可无

- 注释与 Java、C 和 PHP 语言的注释相同

#### JavaScript 变量
JavaScript 通过 var 运算符加上变量名进行定义：
``` var a = 1; ```
JavaScript 是弱类型的，解释器会自动创建一个数值类型的值，无需类型声明，并且同一变量可以储存不同类型的的值。
``` 
var a = 1;
a = 'hello';
```

变量名遵循以下规则：  

 - 首字母必须是字母、\_或者\$  
 
 - 余下字母可以是字母、数字、\_或者\$

变量申明不是必须的，当解释器遇到没有声明过的变量是，会用该变量名创建一个全局变量：

```
a = 1 // 会创建一个叫做a的全局变量，浏览器下挂载在window.a，Node.js会挂载在global.a
```

#### JavaScript 原始类型
JavaScript 有 5 种原始数据类型，即 Undefined、Null、Boolean、Number 和 String。

通过 `typeof` 运算符，可以取得变量或值得类型：
```
typeof undefined; // "undefined"
typeof true; // "boolean"
typeof 123; // "number"
typeof '123'; // "string"
typeof {name: 'test'}; // "object"
typeof null; // "object"
```

typeof 对于 null 值返回 false。这实际上是 JavaScript 最初实现中的一个错误，我们可以将 null 理解成对象的占位符，从而解释这一矛盾。

**Undefined**
Undefined 类型只有一个值，即 undefined。当声明的变量未初始化时，该变量的默认值是 undefined。

```
var test;

console.log(typeof test); // "undefined"
console.log(typeof test2); // "undefined"
```

对于声明未初始化和未声明的变量，typeof 都会返回 undefined，但是对未声明变量使用 typeof 以外的运算符会引起错误。因为其他运算符只能用于已声明的变量上。

```
var test;

console.log(test === undefined); // true
console.log(test2 === undefined); // Uncaught ReferenceError: test2 is not defined
```

**Null**
Null 类型只有一个专用值null，null 用于表示尚未存在的对象。

**Boolean**
Boolean 类型有两个值 true 和 false。

**Number**
Number 类型既可以表示32位整数，还可以表示64位浮点数。

```
var num1 = 123;
var num2 = 070; // 八进制70，十进制56
var num3 = 0xFF; // 十六进制FF，十进制255
```

**String**
JavaScript 没有字符类型，因此双引号（"）和单引号（'）都可以声明字符串。

#### JavaScript 类型转换

JavaScript的原始类型其实是为对象，它们也具有属性和方法，通过toString()，可以将对象转换成String类型。
```
var test = 10;
alert(test.toString(2));	//输出 "1010"
alert(test.toString(8));	//输出 "12"
alert(test.toString(16));	//输出 "A"
```


parseInt()、parseFloat() 可以将非数字转换为 Number 类型：
```
var num1 = parseInt("123456test"); // 123456
var num2 = parseFloat("11.2"); // 11.2
```

Boolean(value)、Number(value)、String(value) 可以进行强制类型转换，强制类型转换是对参数的整体转换：
``` 
var num1 = parseInt("123456test"); // 123456
var num2 = Number("123456test"); // NaN
```


#### JavaScript 的原始值和引用值
JavaScript中，变量可以存在两种类型的值，即原始值和引用值。
**原始值**
存储在栈（stack）中的简单数据段，也就是说，它们的值直接存储在变量访问的位置。JavaScript的原始类型，Null、Boolean、Number 和 String都存储在栈空间中。
**引用值**
存储在堆（heap）中的对象，也就是说，存储在变量处的值是一个指针（point），指向存储对象的内存处。
![image](https://s1.ax1x.com/2018/08/20/Ph4UhR.png)



#### JavaScript 作用域和变量提升
JavaScript中使用var定义的变量


#### 参考资料
> 
JavaScript WikiPedia
https://zh.wikipedia.org/wiki/JavaScript
JavaScript cheat sheet
http://overapi.com/javascript
