# Javascript 基本教程

JS 作为类C语言语法的脚本语言，入门还是比较简单的。

## 字符串

JS 可以使用 `' '` 或者 `" "` 来表示字符串。

```js
str = 'This is a string. 👏';
str2 = "This is the 2nd string. 💁";
```

并且他们之间是可以互相嵌套的。

```js
str = "It's six o'clock.";
str2 = 'Remember to say "please" and "thank you."';
```

或使用 `\` 也可以达到同样目的。

```js
str = 'It\'s six o\'clock.';
str2 = "Remember to say \"please\" and \"thank you.\"";
```

JS 里虽然没有 class 声明类方法，但是`所有类型都可以视为对象`，下面举例说明。

```js
// 这里 "caterpillar" 是个临时的字符串，而这个字符串也是个对象，他有他的成员 length 表达当前字符串长度。
"caterpillar".length;
// 以及 toLowerCase() 方法，转换大小写。
"THE KIDS".toLowerCase();
"I wish I were big.".toUpperCase();
// 去掉空格
"   but keep the middle spaces   ".trim();
// 还可以自己添加自定义方法 (这个内容比较高级，无需太过在意)
"This is a custom function of String.".hanggi();
```

字符串的输出和连接也非常方便

```js
// 在 ES5 版本中我们可以简单使用引号和加好
var a = 123
console.log("Value a is equal to " + a + "!!!");
// ES6 给我们带来了更方便的功能。
console.log(`Value a is equal to ${a}!!!`);
```

#### 【穿插内容】var, let, const 用法

在较早版本的 JS 中是只有 `var` 声明变量。首先 JS 本身是弱类型语言，所以在声明变量是可以简单使用 `var a = 1` 这种表达式，语言本身会判断类型并进行转换。

而在最新版本的 JS 中增加了 let 和 const。目的在于解决 `var` 本身的缺陷。
即，`var` 不支持块级声明。

```js
{
  let a = 10;
  var b = 1;
}

a // ReferenceError: a is not defined.
b // 1
```
这种特性可以解决很多问题，具体内容虚招ES6相关介绍。

## 数值

JS 是弱类型语言，他不区分整型，浮点型等。所以你可以用以下方式简单声明：

```js
var num = 123;
let float = 0.333;
const PI = 3.1415926;
```

并对他们进行加减乘除，你完全可以把它当做计算器来使用。

```js
10 + 3.1415;
1 + (4 / 3)
```

## 数组

数值之后，紧接着就是数组。JS 数组也非常灵活，我们可以使用一些简单的方法去声明它。

```js
// 初始化声明
var array = [1, 2, 3, 4];

// 对象实例创建
var mycars = new Array();
mycars[0] = "Saab";
mycars[1] = "Volvo";
mycars[2] = "BMW";
// 或者
var mycars2 = new Array("Saab", "Volvo", "BMW");
```

JS 数组还有一个神奇之处就是你可以在里面放任何类型，可能也正是因为所有事物都是对象，所以所有事物都可以共生吧。

```js
var arr = [1, "a", false, [2, "b"], function f() {console.log("hello f")}]
```

当然数组作为对象也有很多他自己的方法，常用的有以下几种：

```js
var arr = [1, 2, 3];
arr.push(4);                // [1, 2, 3, 4]
arr.pop();                  // [1, 2, 3]
var sort = [12, 4, 24, 51];
sort.sort();                // [12, 24, 4, 51] 因为他会把每一项转换为字符串，所以排序如此
// 这时我们可以个他一个比较函数
function compare(value1, value2) {
    if (value1 < value2) {
        return -1;
    } else if (value1 > value2) {
        return 1;
    } else {
        return 0;
    }
}

sort.sort(compare);         // [4, 12, 24, 51]
```

当然我们也可以给数组添加一些自定方法，同字符串。

## 布尔值

同样道理，简单使用 `true` 或 `false` 赋值即可。

```js
var bool = true;
if (bool) {
    bool = false;
}
```

## 函数

以下是典型的 JS 函数声明和调用:

```js
function foo(x, y) {
    return x + y;
}

foo(1, 2);          // return 3
```

我们还可以把一个函数付给一个变量

```js
var foo = function (a, b) {
    return a * b;
}
```

#### 【穿插内容】js 中的对象

传统 JS 是没有 class 等类声明方法的（ES6中添加了该方法，所以并不准确）。但是 JS 确实地地道道面向对象的语言。

JS 中所有事物都是对象，包括：数值、字符串、数组、函数...（之前也介绍过如何给一个字符串添加成员变量，与此类似）
对象通过点语法访问他的成员，即：`objectName.propertyName`

我们也可以创建对象。创建对象的方法很多，而且所有事物都是对象，所以对象无处不在。

**我们先通过实例创建获得对象**

```js
person = new Object();
person.firstname="Bill";
person.lastname="Gates";
person.age=56;
person.eyecolor="blue";
```

我们还可以更简单地使用 JSON 格式创建:

```js
person = {firstname: "John", lastname: "Doe", age: 50, eyecolor: "blue"};
```

其中 `{}` 就是一个空对象，我们可以给这个对象添加方法。

不仅如此，我们还能用函数创建对象（这时我们称这个函数为对象构造器）：

```js
function person(firstname, lastname, age, eyecolor) {
    this.firstname = firstname;
    this.lastname = lastname;
    this.age = age;
    this.eyecolor = eyecolor;
}
// 并用 new 创建实例
var myFather=new person("Bill","Gates",56,"blue");
var myMother=new person("Steve","Jobs",48,"green");
```

添加成员方法也非常简单，常见的有两种：

```js
person.gender = "male";
// 或者
person["gender"] = "female";
```

