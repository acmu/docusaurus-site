---
sidebar_position: 2
---

# 列举 Number、String、Array、Object、Promise 有哪些 API


## Number

以下是对 JavaScript 中 `Number` 类型相关函数的详细介绍及其使用示例：

### 1. `Number.isNaN()`
`Number.isNaN()` 用于确定传递的值是否为 `NaN`（Not-a-Number）。与全局的 `isNaN()` 不同，`Number.isNaN()` 不会强制将参数转换为数字。

#### 用法：
```javascript
Number.isNaN(value);
```

#### 示例：
```javascript
console.log(Number.isNaN(NaN)); // true
console.log(Number.isNaN(123)); // false
console.log(Number.isNaN('ed123')); // false
```

### 2. `Number.isInteger()`
`Number.isInteger()` 用于确定传递的值是否为整数。

#### 用法：
```javascript
Number.isInteger(value);
```

#### 示例：
```javascript
console.log(Number.isInteger(123)); // true
console.log(Number.isInteger(123.45)); // false
console.log(Number.isInteger(123.0)); // true 注意
console.log(Number.isInteger('123')); // false
console.log(Number.isInteger(NaN)); // false
console.log(Number.isInteger(Infinity)); // false
```

### 3. `Number.isFinite()`
`Number.isFinite()` 用于确定传递的值是否为有限数值。与全局的 `isFinite()` 不同，`Number.isFinite()` 不会强制将参数转换为数字。

#### 用法：
```javascript
Number.isFinite(value);
```

#### 示例：
```javascript
console.log(Number.isFinite(123)); // true
console.log(Number.isFinite(123.45)); // true
console.log(Number.isFinite(Infinity)); // false
console.log(Number.isFinite(-Infinity)); // false
console.log(Number.isFinite(NaN)); // false
console.log(Number.isFinite('123')); // false
```

### 4. `Number.isSafeInteger()`
`Number.isSafeInteger()` 用于确定传递的值是否为安全整数。安全整数是指在 JavaScript 中可以精确表示的整数，即范围在 \([-2^{53} + 1, 2^{53} - 1]\) 之间的整数。

#### 用法：
```javascript
Number.isSafeInteger(value);
```

#### 示例：
```javascript
console.log(Number.isSafeInteger(123)); // true
console.log(Number.isSafeInteger(123.45)); // false
console.log(Number.isSafeInteger(Math.pow(2, 53) - 1)); // true
console.log(Number.isSafeInteger(Math.pow(2, 53))); // false
console.log(Number.isSafeInteger('123')); // false
console.log(Number.isSafeInteger(NaN)); // false
```

### 5. `Number.prototype.toFixed()`
`Number.prototype.toFixed()` 方法用于将数字转换为指定小数位数的字符串。

#### 用法：
```javascript
num.toFixed(digits);
```
- `digits`：可选。小数点后的位数，范围为 `0` 到 `20`。默认值为 `0`。

#### 示例：
```javascript
let num = 123.456;

console.log(num.toFixed()); // "123"
console.log(num.toFixed(2)); // "123.46"
console.log(num.toFixed(5)); // "123.45600"
console.log((1.005).toFixed(2)); // "1.01" (注意浮点数的舍入误差)
```





## 以下是 JavaScript 中 `parseInt` 和 `parseFloat` 函数的详细介绍及其使用示例：

### 1. `parseInt()`
`parseInt()` 函数用于解析一个字符串并返回一个整数。该函数可以指定进制（基数）来解析字符串。

#### 用法：
```javascript
parseInt(string, radix);
```
- `string`：要解析的字符串。
- `radix`：介于 2 到 36 之间的整数，表示解析时使用的进制。如果省略该参数或其值为 `0`，则使用 10 作为基数（除非字符串以 "0x" 开头，此时使用 16 作为基数）。

#### 示例：
```javascript
console.log(parseInt("123")); // 123
console.log(parseInt("123.45")); // 123
console.log(parseInt("0x1A")); // 26 (16进制)
console.log(parseInt("101", 2)); // 5 (2进制)
console.log(parseInt("7F", 16)); // 127 (16进制)
console.log(parseInt("10", 8)); // 8 (8进制)
console.log(parseInt("abc")); // NaN (无法解析为数字)
console.log(parseInt("123abc")); // 123 (只解析前面的数字部分)
console.log(parseInt("   123   ")); // 123 (忽略前导和尾随空格)
```

### 2. `parseFloat()`
`parseFloat()` 函数用于解析一个字符串并返回一个浮点数。

#### 用法：
```javascript
parseFloat(string);
```
- `string`：要解析的字符串。

#### 示例：
```javascript
console.log(parseFloat("123")); // 123
console.log(parseFloat("123.45")); // 123.45
console.log(parseFloat("123.45.67")); // 123.45 (只解析第一个有效的浮点数部分)
console.log(parseFloat("0.123e2")); // 12.3 (科学计数法)
console.log(parseFloat("   123.45   ")); // 123.45 (忽略前导和尾随空格)
console.log(parseFloat("abc")); // NaN (无法解析为数字)
console.log(parseFloat("123abc")); // 123 (只解析前面的数字部分)
```

### 总结
`parseInt` 和 `parseFloat` 是 JavaScript 中常用的字符串解析函数，用于将字符串转换为整数或浮点数。它们在处理用户输入、解析配置文件或处理字符串数据时非常有用。需要注意的是，这两个函数会忽略字符串中的前导和尾随空格，但只会解析字符串中第一个有效的数值部分，遇到无效字符时会停止解析。




## 如何理解标签函数


```js
function toUpperCase(strings, ...values) {
  console.log(strings);
  console.log(values);
  return strings.reduce((acc, str, i) => {
    return acc + str + (values[i] || "").toUpperCase();
  }, "");
}
const name = "Joh23n";
console.log(toUpperCase`Hello ${name} haha ${name}${name}`); // 输出 "Hello JOHN"



// [object Array] (4)
["Hello "," haha ","",""]

// [object Array] (3)
["Joh23n","Joh23n","Joh23n"]

"Hello JOH23N haha JOH23NJOH23N"
```

String.raw 就是这样调用的

[模板字符串，可以被标签函数所调用](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Template_literals)

但是

```js
String.raw(["Hello "," haha ","",""], "Joh23n","Joh23n","Joh23n")
// 会报错

let rawString = String.raw({ raw: ["Hello ", " haha ", "", ""] }, "Joh23n", "Joh23n", "Joh23n");
console.log(rawString);
// 这样才正确，必须要有 raw 属性，模板参数是有 raw 属性的
```


## String.fromCharCode



`String.fromCharCode()` 是一个 JavaScript 中的静态方法，它返回由指定的 UTF-16 代码单元序列创建的字符串。这个方法常用于将 Unicode 编码（十进制或十六进制）转化为字符。

### 语法

```javascript
String.fromCharCode(num1, num2, ..., numN)
```

- `num1, num2, ..., numN`：一个或多个 Unicode 码点。这些参数必须是介于 `0` 和 `65535` 之间的有效的 UTF-16 代码单元。

### 返回值

返回由指定的 UTF-16 代码单元组成的字符串。

### 常见用法

1. **基本用法**：

```javascript
console.log(String.fromCharCode(65)); // 输出 "A"
console.log(String.fromCharCode(66, 67, 68)); // 输出 "BCD"
```

2. **使用十六进制表示法**：

```javascript
console.log(String.fromCharCode(0x41)); // 输出 "A"
console.log(String.fromCharCode(0x1F600)); // 由于超出范围，结果可能不是预期的表情符号
```

3. **将字符串分解为字符代码，再转回字符串**：

```javascript
let str = "Hello";
let charCodes = [];
for (let i = 0; i < str.length; i++) {
    charCodes.push(str.charCodeAt(i));
}
console.log(charCodes); // 输出 [72, 101, 108, 108, 111]

let newStr = String.fromCharCode(...charCodes);
console.log(newStr); // 输出 "Hello"
```

### 注意点

1. **范围限制**：
   `String.fromCharCode` 只能处理 UTF-16 代码单元（0 到 65535）。这意味着它无法直接创建超出 BMP（基本多语言平面）范围的字符，例如很多表情符号。这些字符需要两个码单元（代理对）来表示。

   ```javascript
   console.log(String.fromCharCode(0x1F600)); // 输出一个不正确的字符，这是因为 0x1F600 超出了 0 到 65535 的范围
   ```

   要正确处理这些字符，可以使用 `String.fromCodePoint`，这是一个 ES6 新增的方法：

   ```javascript
   console.log(String.fromCodePoint(0x1F600)); // 输出表情符号 😀
   ```

2. **多个字符的创建**：
   `String.fromCharCode` 可以接受多个参数，每个参数表示一个 Unicode 码点。

   ```javascript
   console.log(String.fromCharCode(72, 101, 108, 108, 111)); // 输出 "Hello"
   ```

3. **性能**：
   大量调用 `String.fromCharCode` 可能会影响性能，特别是在处理长字符串时。

`String.fromCharCode` 是处理 Unicode 编码和字符转换的强大工具，但当处理超出 BMP 范围的字符时，最好使用 `String.fromCodePoint`。

`fromCodePoint` 就是更大范围的，比如可以处理 emoji。

`String.fromCodePoint()` 是 ES6 （ES2015）中引入的一个静态方法，它可以处理 Unicode 码点范围内的所有字符，包括那些超出基础多语言平面（BMP）范围的字符，如大多数表情符号和一些罕见的汉字。这个方法可以表示的范围是 0x000000 到 0x10FFFF。


对应的字符转编码也要使用 `char.codePointAt`



```js
let smiley = "😀😂😄";

// 遍历字符串并正确处理所有字符，包括代理对
for (let char of smiley) {
    console.log(char, char.codePointAt(0).toString(16));
}

//  😀 1f600
//  😂 1f602
//  😄 1f604

// 而且这里必须使用 for of （或 Array.from 他们都是用了迭代器） 如果是 单纯的for `for (let i =0 ;i<smiley.length;i++)` 那就会出错
```

```js
let str = "Hello, 🌍!";

for (let i = 0; i < str.length; i++) {
  console.log(str.charAt(i)); // 输出每个字符 🌍会变成2个奇怪的字符
}

// 遍历字符并正确处理代理对
for (let char of str) {
  console.log(char); // 输出每个字符，包括超出 BMP 范围的字符 🌍只是1个并且直接输出
} 
```

## String.prototype.concat()

 是一个用于连接字符串的方法，但通常在实际开发中，更为推荐和常用的是 + 运算符、模板字符串（ES6 引入）或者数组的 join() 方法。这些替代方案在可读性和性能上可能具有优势。




## String.prototype.startsWith()


对比 indexOf 方法：

虽然 indexOf 也可以用来检查子字符串是否出现在开始位置，但 startsWith 是更简洁和直观的方法：

javascript


```js
let str = "Hello, world!";

// 使用 indexOf
console.log(str.indexOf("Hello") === 0); // 输出 true

// 使用 startsWith 更简洁
console.log(str.startsWith("Hello")); // 输出 true
```

String.prototype.startsWith() 是一个简单且强大的方法，用于检查字符串是否以指定的子字符串开头。它语法简洁，支持可选的搜索开始位置，且简化了代码逻辑。记住它的区分大小写和可选参数特性，能让你更有信心地在各种场景中使用它。（还有 endsWith）


## String.prototype.includes()

对比 indexOf 方法： 虽然 indexOf 也可以用来检查子字符串是否存在，但 includes 是更简洁和直观的方法：




```js
let str = "Hello, world!";

// 使用 indexOf
console.log(str.indexOf("world") !== -1); // 输出 true

// 使用 includes 更简洁
console.log(str.includes("world")); // 输出 true
```

## String.prototype.indexOf() String.prototype.lastIndexOf()

这不用说的

## String.prototype.trim() trimStart trimEnd



```js
if (!String.prototype.trim) {
  String.prototype.trim = function() {
    return this.replace(/^\s+|\s+$/g, '');
  };
}
```

正则中 `|` 的操作符优先级低

## String.prototype.repeat()



```js
let str = "abc";

console.log(str.repeat(0));  // 输出： ""
console.log(str.repeat(1));  // 输出： "abc"
console.log(str.repeat(2));  // 输出： "abcabc"
console.log(str.repeat(3.5));  // 输出： "abcabcabc" (会向下取整为3)
console.log(str.repeat(-1));  // 抛出 RangeError
```


## String.prototype.slice()



```js
let str = "Hello, world!";

console.log(str.slice(7, 12)); // 输出: "world"
console.log(str.slice(7));      // 输出: "world!"
console.log(str.slice(-6, -1)); // 输出: "world"
console.log(str.slice(0, -1));  // 输出: "Hello, world"
console.log(str.slice(-6));     // 输出: "world!"
```


## String.prototype.split()




```js
let str = "Hello, world! How are you?";

// 按逗号和空格分割字符串
let result1 = str.split(", ");
console.log(result1); // 输出: ["Hello", "world! How are you?"]

// 按空格分割字符串
let result2 = str.split(" ");
console.log(result2); // 输出: ["Hello,", "world!", "How", "are", "you?"]

// 使用正则表达式按非字母字符分割字符串
let result3 = str.split(/\W+/);
console.log(result3); // 输出: ["Hello", "world", "How", "are", "you", ""]

// 限制返回的子字符串数量
let result4 = str.split(" ", 3);
console.log(result4); // 输出: ["Hello,", "world!", "How"]

// 分隔符为空字符串，按每个字符分割
let result5 = str.split("");
console.log(result5); // 输出: ["H", "e", "l", "l", "o", ",", " ", "w", "o", "r", "l", "d", "!", " ", "H", "o", "w", " ", "a", "r", "e", " ", "y", "o", "u", "?"]

// 未指定分隔符，返回包括字符串本身的数组
let result6 = str.split();
console.log(result6); // 输出: ["Hello, world! How are you?"]
```

`\W+`（非字母字符） 使用正则分割



## String.prototype.substring()

参数不能有负数，如果第一个参数，比第二个大，那么就会自动交换，和 slice 功能类似


```js
let str = "Hello, world!";

console.log(str.substring(7, 12));  // 输出: "world"
console.log(str.substring(7));       // 输出: "world!"
console.log(str.substring(0, 5));    // 输出: "Hello"
console.log(str.substring(7, 7));    // 输出: ""
console.log(str.substring(12, 7));   // 输出: "world"
console.log(str.substring(0, -3));   // 输出: "" (负数被当作0)
console.log(str.substring(7, 50));   // 输出: "world!" (超出长度被视作末尾)
```



```js
str.substring(indexStart, indexEnd)
// 参数是开始和结束

str.substr(start, length)
// 参数是开始和长度（已经不建议使用了）

str.slice(-6, -1)
// 最推荐的还是 slice 因为它支持负数
```

## String.prototype.padStart()

前面填充内容，常用于日志输出 padEnd 同理

```js
let str = "123";

// 使用默认的空格进行填充
console.log(str.padStart(5));        // 输出: "  123"

// 使用指定的填充字符串
console.log(str.padStart(5, '0'));   // 输出: "00123"
console.log(str.padStart(10, 'abc')); // 输出: "abcabca123"

// 当目标长度小于原字符串长度时，返回原字符串
console.log(str.padStart(2));        // 输出: "123"

// 填充字符串超过需要的长度时，只会使用必要的部分
console.log(str.padStart(8, '1234')); // 输出: "12341123"

```


## String.prototype.search()

搜索字符，返回下标，类似于 indexof，如果没有返回-1，但是参数可以是正则，但正则的 g 标志在这里没用

```js
const str = " $20.";
console.log(str.search(/\$\d+/)); // 1
```


## String.prototype.match() 和 exec 方法的区别

搜索正则的捕获组

String.prototype.match 方法用于在字符串中匹配正则表达式，并返回匹配的结果。如果没有找到匹配项，则返回 null。

分为两种情况：
1. 如果使用g标志，则将返回所有匹配完整正则表达式的结果，但不包括捕获组
2. 如果不使用g标志，则仅返回第一个完整的匹配及其相关的捕获组。在这种情况下，match()将返回与RegExp.prototype.exec()（具有一些额外属性的数组）相同的结果。


该使用哪些函数？

1. 如果需要知道字符串是否与正则表达式RegExp匹配，请使用RegExp.prototype.test（）。
2. 如果您只想找到第一个匹配项，则可能需要使用RegExp.prototype.exec（）。
3. 如果您想获取捕获组并且设置了全局标志，则需要使用RegExp.prototype.exec（）或String.prototype.matchAll（）。

所以 match 函数用处不大，用于 g 的时候搜索全部的匹配项

```js
const str = "ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz";
const regexp = /[A-E]/gi;
const matches = str.match(regexp);

console.log(matches);
// ['A', 'B', 'C', 'D', 'E', 'a', 'b', 'c', 'd', 'e']
```

命名捕获组

```js
const regexp = /t(?<reName>e)(st(\d?))/g;
const str = "test1test2";

str.match(regexp); // ['test1', 'test2']
const array = [...str.matchAll(regexp)];
array[0]; // ['test1', 'e', 'st1', '1', index: 0, input: 'test1test2', length: 4]
array[1]; // ['test2', 'e', 'st2', '2', index: 5, input: 'test1test2', length: 4]
```

`(?<reName>e)` 是命名捕获组，reName 是他的命名 `(?<...>)` 其中的 `...` 是命名（但注意：这个特性浏览器兼容性不好）



```js
const str = '123 abc 456 def 789';
const numbers = str.match(/\d+/g);
console.log(numbers); // 输出：["123", "456", "789"]
```



```js
const str = "2023-09-08 14:30:00";
const regex = /(\d{4})-(\d{2})-(\d{2}) (\d{2}):(\d{2}):(\d{2})/;
const match = str.match(regex);

console.log(match);
// 输出：
// [
//   "2023-09-08 14:30:00",
//   "2023",
//   "09",
//   "08",
//   "14",
//   "30",
//   "00"
// ]
```
在这个例子中，match 方法返回的第一个元素是整个匹配的字符串，后面的元素是每个捕获组匹配到的结果。第一个捕获组 (\d{4}) 匹配四位年份，第二个捕获组 (\d{2}) 匹配两位月份，依此类推。

请注意，当正则表达式包含全局标志 g 时，match 方法不会返回捕获组的信息。因此，在使用捕获组时，通常不使用 g 标志。

如果只需要捕获组的结果，而不需要整个匹配的字符串，可以使用 exec 方法，它总是返回包含捕获组的数组。


###  String.prototype.matchAll() 方法 

String值的matchAll()方法返回与正则表达式匹配此字符串的所有结果的迭代器，包括捕获组。

```js
const regexp = /t(e)(st(\d?))/;
const str = 'test1test2';

const array = [...str.matchAll(regexp)];

console.log(array[0]);
// Expected output: Array ["test1", "e", "st1", "1"]

console.log(array[1]);
// Expected output: Array ["test2", "e", "st2", "2"]
```

如果regexp是没有设置全局（g）标志的正则表达式（其flags属性不包含"g"），则抛出异常，所以 matchAll 的正则参数必须包含 g 标志




### match 和 exec 区别

match 在字符串上调用， exec 在正则上调用

```js
const str = "cat, bat, sat, fat";
const regex = /[a-z]at/g;

// 使用 .match() 方法
const matchResult = str.match(regex);
console.log(matchResult); // 输出：["cat", "bat", "sat", "fat"]

// 使用 exec() 方法
const execResult1 = regex.exec(str);
console.log(execResult1); // 输出：["cat"]
const execResult2 = regex.exec(str);
console.log(execResult2); // 输出：["bat"]
// ...继续调用exec()将返回下一个匹配项
```

```js
const str = "cat, bat, sat, fat";
const regex = /[a-z]at/g;

// 使用 exec() 方法
regex.exec(str); // 返回 ["cat"]
regex.exec(str); // 返回 ["bat"]
console.log(regex.lastIndex); // 输出：8，因为下一次匹配将从索引8开始

// 使用 match() 方法后，lastIndex不会改变
str.match(regex);
console.log(regex.lastIndex); // 输出：8，因为match()不更新lastIndex
```


## 正则表达式中的贪婪匹配和非贪婪匹配


在正则表达式中，贪婪匹配和非贪婪匹配是指正则表达式引擎在匹配字符串时，对于量词（如 *、+、?、`{n}` 等）的匹配行为。

贪婪匹配
默认情况下，正则表达式的量词是贪婪的，这意味着它们会尽可能多地匹配字符。贪婪匹配总是尝试在可能的情况下匹配更多的字符。


```js
const str = "123 456 789";
const regexGreedy = /\d+/;
const matchGreedy = str.match(regexGreedy);
console.log(matchGreedy[0]); // 输出："123"
```





非贪婪匹配
非贪婪匹配（也称为懒惰匹配或最小匹配）则尽可能少地匹配字符。要实现非贪婪匹配，需要在量词后面加上一个问号 ?。



```js
const str = "123 456 789";
const regexNonGreedy = /\d+?/;
const matchNonGreedy = str.match(regexNonGreedy);
console.log(matchNonGreedy[0]); // 输出："1"，只匹配了第一个数字
```

常见量词及其非贪婪形式
贪婪匹配：* （匹配0次或多次）变为非贪婪匹配： *?
贪婪匹配：+（匹配1次或多次）变为非贪婪匹配：+?




```js

```



```js

```

