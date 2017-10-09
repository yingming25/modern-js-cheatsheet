# <a name="modern-javascript-cheatsheet"></a> Modern JavaScript Cheatsheet

![Modern JavaScript cheatsheet](https://i.imgur.com/aexPxMb.png)
<small>圖像 來源: [Ahmad Awais ⚡️](https://github.com/ahmadawais)</small>

## <a name="introduction"></a> 介紹

### <a name="motivation"></a> 動機

This document is a cheatsheet for JavaScript you will frequently encounter in modern projects and most contemporary sample code.<br>
這個文件是一個給 JavaScript 的作弊表 在現代的示例程式碼和現代專案你將會經常地遭遇到.


This guide is not intended to teach you JavaScript from the ground up, but to help developers with basic knowledge who may struggle to get familiar with modern codebases (or let's say to learn React for instance) because of the JavaScript concepts used.<br>
這個指南不打算從頭開始教你 JavaScript ,
而是為了幫助有基本知識的開發者可以盡力去熟悉用現代代碼庫( 或讓我們說為了學 React 實例 )因為 JavaScript  概念被使用.

Besides, I will sometimes provide personal tips that may be debatable but will take care to mention that it's a personal recommendation when I do so.<br>
此外,我將有時提供個人秘訣可能是可爭論的但是將小心提到它是一個個人建議當我這樣做.

> **Note:** Most of the concepts introduced here are coming from a JavaScript language update (ES2015, often called ES6). You can find new features added by this update [here](http://es6-features.org); it's very well done.<br>
> **注意:** 這裡介紹的大部分概念來自於 JavaScript 語言更新（ES2015，通常稱為ES6）. 透過這個更新你可以發現新特色 [這裡](http://es6-features.org); 做得很好.

### <a name="complementary-resources"></a> 補充資源

When you struggle to understand a notion, I suggest you look for answers on the following resources:<br>
當你盡力去了解概念, 我建議你在以下資源尋找答案：

- [MDN ( Mozilla 網路開發)](https://developer.mozilla.org/en-US/search?q=)
- [你不知道的 JS (書本)](https://github.com/getify/You-Dont-Know-JS)
- [ES6 特性和例子](http://es6-features.org)
- [WesBos 部落格 (ES6)](http://wesbos.com/category/es6/)
- [Reddit (電子布告欄) (JavaScript)](https://www.reddit.com/r/javascript/)
- [ Google ](https://www.google.com/) 為了搜尋明確的部落格和資源
- [StackOverflow (程式設計問答網站)](https://stackoverflow.com/questions/tagged/javascript)


## <a name="table-of-contents"></a> 目錄

- [Modern JavaScript cheatsheet](#modern-javascript-cheatsheet)
  * [介紹](#introduction)
    + [動機](#motivation)
    + [補充資源](#complementary-resources)
  * [目錄](#table-of-contents)
  * [概念](#notions)
    + [變數宣告: var, const, let](#variable-declaration-var-const-let)
      - [簡短說明](#short-explanation)
      - [示例代碼](#sample-code)
      - [詳細說明](#detailed-explanation)
      - [外部資源](#external-resource)
    + [箭頭函式](#-arrow-function)
      - [示例代碼](#sample-code-1)
      - [詳細說明](#detailed-explanation-1)
        * [簡要](#concision)
        * [*this* 參考](#this-reference)
      - [有用的資源](#useful-resources)
    + [函式預設參數](#function-default-parameter-value)
      - [外部資源](#external-resource-1)
    + [objects 和 arrays 的解構](#destructuring-objects-and-arrays-12)
      - [示例代碼說明](#explanation-with-sample-code-13)
      - [有用資源](#useful-resources-14)
    + [陣列方法 - map / filter / reduce](#array-methods---map--filter--reduce)
      - [示例代碼](#sample-code-2)
      - [示例代碼說明](#explanation-with-sample-code-0)
        * [Array.prototype.map()](#arrayprototypemap)
        * [Array.prototype.filter()](#arrayprototypefilter)
        * [Array.prototype.reduce()](#arrayprototypereduce)
      - [外部資源](#external-resource-2)
    + [展開運算子 "..."](#spread-operator-)
      - [示例代碼](#sample-code-3)
      - [說明](#explanation-1)
        * [迭代用法 (如同 array)](#in-iterables-like-array-25)
        * [函式剩餘參數](#function-rest-parameter)
        * [物件屬性擴展](#object-properties-spreading)
      - [外部資源](#external-resources)
    + [Object 屬性簡寫](#object-property-shorthand-29)
      - [說明](#explanation-2)
      - [外部資源](#external-resources-31)
    + [Promises](#promises)
      - [示例代碼](#sample-code-4)
      - [說明](#explanation-3)
        * [創建 promise](#create-the-promise)
        * [Promise 處理器運用](#promise-handlers-usage)
      - [外部資源](#external-resources-32)
    + [模板字面量](#template-literals)
      - [示例代碼](#sample-code-5)
      - [外部資源](#external-resources-2)
    + [標記模板字面量](#tagged-template-literals)
      - [外部資源](#external-resources-4)
    + [Imports / Exports](#imports--exports)
      - [示例代碼說明](#explanation-with-sample-code-1)
        * [命名 exports](#named-exports)
        * [預設 import / export](#default-import--export)
      - [外部資源](#external-resources-3)
    + [JavaScript *this*](#-javascript-this)
      - [外部資源](#external-resources-42)
    + [Class](#class)
      - [示例](#samples)
      - [外部資源](#external-resources-5)
    + [Async Await](#async-await)
      - [示例代碼](#sample-code-6)
      - [示例代碼說明](#explanation-with-sample-code-2)
      - [外部資源](#external-resources-6)
    + [Truthy / Falsy](#truthy--falsy)
  * [詞彙表](#glossary)
    + [範圍](#-scope)
    + [變數變化](#-variable-mutation)


## <a name="notions"></a> 概念

### <a name="variable-declaration-var-const-let"></a> 變數宣告: var, const, let

In JavaScript, there are three keywords available to declare a variable, and each has its differences. Those are ```var```, ```let``` and ```const```.<br>
在 JavaScript 裡, 有三個可用的關鍵字宣告變數, 以及每個有它們的不同. 那些是 ```var```, ```let``` and ```const```.

#### <a name="short-explanation"></a> 簡短說明


Variables declared with ```const``` keyword can't be reassigned, while ```let``` and ```var``` can.<br>
宣告變數用 ```const``` 關鍵字不能被重新分配, 然而 ```let``` 和 ```var``` 能.

I recommend always declaring your variables with ```const``` by default, and with ```let``` if you need to *mutate* it or reassign it later.<br>
我總是推薦宣告你的變數用 ```const``` 透過預設, 以及用 ```let``` 如果之後你必須改變它或重新分配它.

<table>
  <tr>
    <th></th>
    <th>範圍</th>
    <th>重新指派</th>
    <th>可變的</th>
   <th><a href="#tdz_sample">暫時性死區</a></th>
  </tr>
  <tr>
    <th>const</th>
    <td>區塊</td>
    <td>No</td>
    <td><a href="#const_mutable_sample">Yes</a></td>
    <td>Yes</td>
  </tr>
  <tr>
    <th>let</th>
    <td>區塊</td>
    <td>Yes</td>
    <td>Yes</td>
    <td>Yes</td>
  </tr>
   <tr>
    <th>var</th>
    <td>函式</td>
    <td>Yes</td>
    <td>Yes</td>
    <td>No</td>
  </tr>
</table>

#### <a name="sample-code"></a> 示例代碼

```javascript
const person = "Nick";
person = "John" // Will raise an error, person can't be reassigned 會引發錯誤, person 不能被重新分配
```

```javascript
let person = "Nick";
person = "John";
console.log(person) // "John", reassignment is allowed with let 用let重新分配是被允許的
```

#### <a name="detailed-explanation"></a> 詳細說明

The [*scope*](#scope_def) of a variable roughly means "where is this variable available in the code".<br>
這個 [*範圍*](#scope_def) 的變數大概的方法 "在程式碼中哪裡是這個變數可用的".

##### var

```var``` declared variables are *function scoped*, meaning that when a variable is created in a function, everything in that function can access that variable. Besides, a *function scoped* variable created in a function can't be accessed outside this function.<br>
```var``` 宣告變數 是 *函式範圍*, 意味當一個變數在函式中被創建, 每件事(物)在函式裡可以訪問那變數. 此外, 一個 *函式範圍*, 變數在函式裡被創建不能被這個函式外訪問.

I recommend you to picture it as if an *X scoped* variable meant that this variable was a property of X.<br>
我建議你描寫一個* X範圍的*變量意味著這個變量是X的屬性。


```javascript
function myFunction() {
  var myVar = "Nick";
  console.log(myVar); // "Nick" - myVar is accessible inside the function myVar可以在函數內部訪問
}
console.log(myVar); // Throws a ReferenceError, myVar is not accessible outside the function.拋出一個參考錯誤，myVar在函數外不可訪問。
```

Still focusing on the variable scope, here is a more subtle example:<br>
仍然關注在變數範圍, 這是一個更細微的範例:

```javascript
function myFunction() {
  var myVar = "Nick";
  if (true) {
    var myVar = "John";
    console.log(myVar); // "John"
    // actually, myVar being function scoped, we just erased the previous myVar value "Nick" for "John"
    //事實上, myVar 是函數範圍的, 我們只是擦拭之前 myVar 值 "Nick" 給 "John"
  }
  console.log(myVar); // "John" - see how the instructions in the if block affected this value
  //"John" - 看在 if 區塊中的指令如何影響這個值
}
console.log(myVar); // Throws a ReferenceError, myVar is not accessible outside the function.
//拋出一個參考錯誤, 這個函數外部 myVar 是不能可訪問的
```

Besides, *var* declared variables are moved to the top of the scope at execution. This is what we call [var hoisting](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/var#var_hoisting).<br>
此外, *var* 宣告的變數在執行時移動到範圍的頂部。這就是我們所說的 [var hoisting](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/var#var_hoisting).

This portion of code:<br>
這個代碼的部分:


```js
console.log(myVar) // undefined -- no error raised 沒有錯誤提出
var myVar = 2;
```

is understood at execution like:

```js
var myVar;
console.log(myVar) // undefined -- no error raised 沒有錯誤提出
myVar = 2;
```

##### let

```var``` and ```let ``` are about the same, but ```let``` declared variables
```var``` 與 ```let ``` 是差不多的,但 ```let``` 宣告變數

- are *block scoped*
- 是 *區塊範圍*
- are **not** accessible before they are assigned
- 是 **不** 可使用的在他們被分配之前
- can't be re-declared in the same scope
- 在相同的範圍不能被重複宣告

Let's see the impact of block-scoping taking our previous example:
讓我們看這區塊範圍的影響以我們以前的例子:

```javascript
function myFunction() {
  let myVar = "Nick";
  if (true) {
    let myVar = "John";
    console.log(myVar); // "John"
    // actually, myVar being block scoped, we just created a new variable myVar.
    // 事實上, myVar 是區塊範圍, 我們只是創建一個新的變數 myVar
    // this variable is not accessible outside this block and totally independent
    // 這個變數在這個區塊外面是不可使用的以及完全獨立的
    // from the first myVar created !
    // 從第一個 myVar 被創造!<br> 
  }
  console.log(myVar); // "Nick", see how the instructions in the if block DID NOT affect this value!
  //"Nick", 看看 if 區塊裡的指令如何不影響這個值!
}
console.log(myVar); // Throws a ReferenceError, myVar is not accessible outside the function.
//拋出一個參考錯誤, myVar 在這個函數外面是不可使用的.
```

<a name="tdz_sample"></a> Now, what it means for *let* (and *const*) variables for not being accessible before being assigned:<br>
<a name="tdz_sample"></a> 現在,:意味著 *let* (and *const*) 變數在指派前不可使用

```js
console.log(myVar) // raises a ReferenceError !
// 引發一個參考錯誤
let myVar = 2;
```

By contrast with *var* variables, if you try to read or write on a *let* or *const* variable before they are assigned an error will be raised. This phenomenon is often called [*Temporal dead zone*](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/let#Temporal_Dead_Zone_and_errors_with_let) or *TDZ*.<br>
和 *var* 變數相比之下, 假如你嘗試去讀或寫一個 *let* or *const* 變數 在他們被指派之前 一個錯誤將被引發. 這個現象經常被稱為 [*暫時性死區*](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/let#Temporal_Dead_Zone_and_errors_with_let) or *TDZ*.


> **Note:** Technically, *let* and *const* variables declarations are being hoisted too, but not their assignation. Since they're made so that they can't be used before assignation, it intuitively feels like there is no hoisting, but there is. Find out more on this [very detailed explanation here](http://jsrocks.org/2015/01/temporal-dead-zone-tdz-demystified) if you want to know more.<br>
> **注意:** 技術上, *let* 和 *const* 變數宣告也是被提升, 但不是他們的分配. 因為它們是在分配之前不能使用的, 他直觀地感覺像沒有提升,但有. 了解更多信息[這裡非常詳細的說明](http://jsrocks.org/2015/01/temporal-dead-zone-tdz-demystified) 如果你想要知道更多.

In addition, you can't re-declare a *let* variable:<br>
此外, 你不能重新宣告一個 *let* 變數:

```js
let myVar = 2;
let myVar = 3; // Raises a SyntaxError 引發一個語法錯誤
```

##### const

```const``` declared variables behave like *let* variables, but also they can't be reassigned.<br>
```const``` 宣告變數表現像  *let* 變數, 但他們也不能被重新分配.

To sum it up, *const* variables:<br>
總而言之, *const* 變數:

- are *block scoped*
- 是 *區塊範圍*
- are not accessible before being assigned
- 在被分配之前是不可使用的
- can't be re-declared in the same scope
- 在相同的範圍不能被重新宣告
- can't be reassigned
- 無法重新分配

```js
const myVar = "Nick";
myVar = "John" // raises an error, reassignment is not allowed 引發錯誤,不允許重新分配
```

```js
const myVar = "Nick";
const myVar = "John" // raises an error, re-declaration is not allowed 引發錯誤, 不允許重新宣告
```

<a name="const_mutable_sample"></a> But there is a subtlety : ```const``` variables are not [**immutable**](#mutation_def) ! Concretely, it means that *object* and *array* ```const``` declared variables **can** be mutated.<br>
<a name="const_mutable_sample"></a>但有一個微妙之處: ```const``` 變數不是 [**不變**](#mutation_def) ! 具體地, 它意味著 *物件* 與 *陣列* ```const``` 宣告變數 **可以** 被改變.

對於物件:
```js
const person = {
  name: 'Nick'
};
person.name = 'John' // this will work ! person variable is not completely reassigned, but mutated
// 這能運行 ! person 變數沒有完全重新分配, 但改變
console.log(person.name) // "John"
person = "Sandra" // raises an error, because reassignment is not allowed with const declared variables
//引發錯誤, 因為重新分配不被允許用 const 宣告變數
```

對於陣列:
```js
const person = [];
person.push('John'); // this will work ! person variable is not completely reassigned, but mutated
//這能運行 ! person 變數沒有完全重新分配, 但改變
console.log(person[0]) // "John"
person = ["Nick"] // raises an error, because reassignment is not allowed with const declared variables
//因為重新分配是不被允許用 const 宣告變數
```


#### <a name="external-resource"></a> 外部資源

- [How let and const are scoped in JavaScript - WesBos](http://wesbos.com/javascript-scoping/)
- [Temporal Dead Zone (TDZ) Demystified](http://jsrocks.org/2015/01/temporal-dead-zone-tdz-demystified)

### <a name="-arrow-function"></a> 箭頭函式

The ES6 JavaScript update has introduced *arrow functions*, which is another way to declare and use functions. Here are the benefits they bring:<br>
這 ES6 JavaScript 更新已經提出 *箭頭函式*, 是另一種宣告和使用函數的方法. 這裡是它帶來的好處:

- More concise
- 更簡潔
- *this* is picked up from surroundings
- *this* 從周圍拾起
- implicit return
- 返回值成為一部分

#### <a name="sample-code-1"></a> 示例代碼

- Concision and implicit return
- 簡潔和隱含的回報

```js
function double(x) { return x * 2; } // Traditional way 傳統方式
console.log(double(2)) // 4
```

```js
const double = x => x * 2; // Same function written as an arrow function with implicit return
//相同函式寫為一個箭頭函式帶有隱含的回報
console.log(double(2)) // 4
```

- *this* reference

- *this* 參考

In an arrow function, *this* is equal to the *this* value of the enclosing execution context. Basically, with arrow functions, you don't have to do the "that = this" trick before calling a function inside a function anymore.<br>
在一個箭頭函式中. *this* 等於 *this* 封閉執行內容的值. 基本上, 用箭頭函式, 你不必做 "that = this" 手法在函式中調用一個函式之前.

```js
function myFunc() {
  this.myVar = 0;
  setTimeout(() => {
    this.myVar++;
    console.log(this.myVar) // 1
  }, 0);
}
```

#### <a name="detailed-explanation-1"></a> 詳細說明

##### <a name="concision"> 簡要

Arrow functions are more concise than traditional functions in many ways. Let's review all the possible cases:<br>
箭頭函式是比傳統函式更簡潔在許多方面. 讓我們來看看所有可能情況:


- Implicit VS Explicit return
- 隱含 VS 明確 返回

An **explicit return** is a function where the *return* keyword is used in its body.<br>
一個 **明確返回** 是一個函式 *return* 關鍵字在其正文中使用.

```js
  function double(x) {
    return x * 2; // this function explicitly returns x * 2, *return* keyword is used
    //這個函式 明確返回 x * 2, *return* 關鍵字被使用
  }
```

In the traditional way of writing functions, the return was always explicit. But with arrow functions, you can do *implicit return* which means that you don't need to use the keyword *return* to return a value.<br>
在寫函式的傳統方法中, 回傳總是明確的. 但用箭頭函式, 你可以做 *隱含返回* 意味著你不需要使用關鍵字 *return* 返回一個值

To do an implicit return, the code must be written in a one-line sentence.<br>
做一個隱含返回, 程式碼必須用一行句子寫成

```js
  const double = (x) => {
    return x * 2; // Explicit return here 這裡隱含返回
  }
```

Since there only is a return value here, we can do an implicit return.<br>
由於這裡者有一個返回值, 我們可以做一個隱含返回.

```js
  const double = (x) => x * 2;
```

To do so, we only need to **remove the brackets** and the **return** keyword. That's why it's called an *implicit* return, the *return* keyword is not there, but this function will indeed return ```x * 2```.<br>
為此, 我們只需要 **刪除括號** 和這 **return** 關鍵字. 那是為什麼他稱為一個 *隱含* 返回, 這 *return* 關鍵字不在那裡, 但這函式確實會返回 ```x * 2``` .


> **Note:** If your function does not return a value (with *side effects*), it doesn't do an explicit nor an implicit return.<br>
> **注意:** 如果你的函示不返回一個值 (有 *副作用*), 它不做一個明確也不做一個隱含返回.

Besides, if you want to implicitly return an *object* you **must have parenthesis around it** since it will conflict with the block braces:<br>
此外, 如果你想要隱含地返回一個 *object* 你 **必須有周圍的括號** 因為它將與塊大括號衝突:

```js
const getPerson = () => ({ name: "Nick", age: 24 })
console.log(getPerson()) // { name: "Nick", age: 24 } -- object implicitly returned by arrow function
// 物件隱含地透過箭頭函式返回
```

- Only one argument
- 只有一個參數

If your function only takes one parameter, you can omit the parenthesis around it. If we take back the above *double* code:<br>
如果你的函式只有一個參數, 你能省略周圍的小括號. 如果我們要取回上述 *兩倍* 程式碼:

```js
  const double = (x) => x * 2; // this arrow function only takes one parameter
  //這個箭頭函式只需要一個參數
```

Parenthesis around the parameter can be avoided:<br>

```js
  const double = x => x * 2; // this arrow function only takes one parameter
  //這個箭頭函式只需要一個參數
```

- No arguments
- 沒有參數

When there is no argument provided to an arrow function, you need to provide parentheses, or it won't be valid syntax.<br>
當沒有參數提供給一個箭頭函式, 你必須提供小括號, 否則它不會是有效的語法.

```js
  () => { // parenthesis are provided, everything is fine 小括號被提供, 一切很好
    const x = 2;
    return x;
  }
```

```js
  => { // No parenthesis, this won't work! 沒有小括號, 這不會運行
    const x = 2;
    return x;
  }
```

##### <a name="this-reference"></a> *this* 參考

To understand this subtlety introduced with arrow functions, you must know how [this](#this_def) behaves in JavaScript.<br>
為了了解這個帶有箭頭函數的微妙之處, 你必須知道 [this](#this_def) 如何在 JavaScript 中表現.

In an arrow function, *this* is equal to the *this* value of the enclosing execution context. What it means is that an arrow function doesn't create a new *this*, it grabs it from its surrounding instead.<br>
在一個箭頭函數, *this* 等於 *this* 封閉執行內容的值. 它意思是一個箭頭函式不創建一個新的 *this*, 它從它的周圍抓住它

Without arrow function, if you wanted to access a variable from *this* in a function inside a function, you had to use the *that = this* or *self = this* trick.<br>
沒有箭頭函式, 如果你想要從一個函式裡面的函式存取一個變數, 你必須使用 *that = this* 或 *self = this* 技巧.

For instance, using setTimeout function inside myFunc:<br>
例如, 使用 setTimeout 函式裡面的 myFunc:

```js
function myFunc() {
  this.myVar = 0;
  var that = this; // that = this trick 技巧
  setTimeout(
    function() { // A new *this* is created in this function scope
    //一個新的 *this* 被創建在這個函式範圍
      that.myVar++;
      console.log(that.myVar) // 1

      console.log(this.myVar) // undefined -- see function declaration above 見上面的函式宣告
    },
    0
  );
}
```

But with arrow function, *this* is taken from its surrounding:<br>
但用箭頭函式, *this* 從他的周圍被取:

```js
function myFunc() {
  this.myVar = 0;
  setTimeout(
    () => { // this taken from surrounding, meaning myFunc here
    // this 從周圍取, 意味 myFunc 在這裡
      this.myVar++;
      console.log(this.myVar) // 1
    },
    0
  );
}
```

#### <a name="useful-resources"></a> 有用的資源

- [Arrow functions introduction - WesBos](http://wesbos.com/arrow-functions/)
- [JavaScript arrow function - MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Arrow_functions)
- [Arrow function and lexical *this*](https://hackernoon.com/javascript-es6-arrow-functions-and-lexical-this-f2a3e2a5e8c4)

### <a name="function-default-parameter-value"></a> 函式預設參數

Starting from ES2015 JavaScript update, you can set default value to your function parameters using the following syntax:<br>
從 ES2015 開始 JavaScript 更新, 你可以設定預設值到你的函式參數使用以下語法:

```js
function myFunc(x = 10) {
  return x;
}
console.log(myFunc()) // 10 -- no value is provided so x default value 10 is assigned to x in myFunc
//10 -- 沒有值被提供所以預設值 10 被指派到 x 在 myFunc 中
console.log(myFunc(5)) // 5 -- a value is provided so x is equal to 5 in myFunc
//5 -- 一個值被提供所以 x 是等於5在 myFunc 中
console.log(myFunc(undefined)) // 10 -- undefined value is provided so default value is assigned to x
// 10 -- undefined 值被提供所以預設值被指派到 x
console.log(myFunc(null)) // null -- a value (null) is provided, see below for more details
// null -- 一個值 (null) 被提供, 請參閱下面的更多細節
```

The default parameter is applied in two and only two situations:<br>
這預設參數是被採用只在兩個狀況:

- No parameter provided
- 沒有參數提供
- *undefined* parameter provided
- *undefined* 參數提供

In other words, if you pass in *null* the default parameter **won't be applied**.<br>
換一種說法, 如果你通過在 *null* 中這預設參數 **不被採用**

> **Note:** Default value assignment can be used with destructured parameters as well (see next notion to see an example)<br>
> **注意:** 預設值可以被很好的使用在構造參數 (看下一個概念來看一個例子)

#### <a name="external-resource-1"></a> 外部資源

- [Default parameter value - ES6 Features](http://es6-features.org/#DefaultParameterValues)
- [Default parameters - MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Default_parameters)

### <a name="destructuring-objects-and-arrays-12"></a> objects 和 arrays 的解構

*Destructuring* is a convenient way of creating new variables by extracting some values from data stored in objects or arrays.<br>
*解構* 是一個創建新變數的便利方法透過從資料儲存在物件或陣列提取一些值

To name a few use cases, *destructuring* can be used to destructure function parameters or *this.props* in React projects for instance.<br>
舉幾個例子, *解構* 能被用在解構函式參數或 *this.props* 在 React 專案實例中

#### <a name="explanation-with-sample-code-13"></a> 示例代碼說明

- Object
- 物件

Let's consider the following object for all the samples:<br>
讓我們為思考所有示例以下物件

```js
const person = {
  firstName: "Nick",
  lastName: "Anderson",
  age: 35,
  sex: "M"
}
```

Without destructuring<br>
沒用解構

```js
const first = person.firstName;
const age = person.age;
const city = person.city || "Paris";
```

With destructuring, all in one line:<br>
用解構, 所有在一行:

```js
const { firstName: first, age, city = "Paris" } = person; // That's it ! 是的!

console.log(age) // 35 -- A new variable age is created and is equal to person.age
//35 -- 一個新 age 變數被創建以及等於 person.age
console.log(first) // "Nick" -- A new variable first is created and is equal to person.firstName
// "Nick" -- 一個新 first 被創建以及等於 person.firstName
console.log(firstName) // Undefined -- person.firstName exists BUT the new variable created is named first
// Undefined -- person.firstName 存在 但這個新的變數創建被命名 first
console.log(city) // "Paris" -- A new variable city is created and since person.city is undefined, city is equal to the default value provided "Paris".
// "Paris" -- 一個新的變數 city 被創建以及因為 person.city 是未定義, city 等於 這個預設值提供 "Paris".
```

**Note :** In ```const { age } = person;```, the brackets after *const* keyword are not used to declare an object nor a block but is the *destructuring* syntax.<br>
**注意 :** 在 ```const { age } = person;``` 中. 這個在關鍵字 *const* 之後的大括號不是用來宣告一個物件也不是用來宣告一個區塊 但這個是 *解構*  語法.

- Function parameters
- 函式參數

*Destructuring* is often used to destructure objects parameters in functions.<br>
*解構* 在函式中經常被用來解構物件參數

Without destructuring<br>
沒用解構

```js
function joinFirstLastName(person) {
  const firstName = person.firstName;
  const lastName = person.lastName;
  return firstName + '-' + lastName;
}

joinFirstLastName(person); // "Nick-Anderson"
```

In destructuring the object parameter *person*, we get a more concise function:<br>
在解構這物件參數 *person*, 我們取得一個更簡潔的函式:

```js
function joinFirstLastName({ firstName, lastName }) { // we create firstName and lastName variables by destructuring person parameter
//我們創建 firstName 和 lastName 變數 透過解構 person 參數
  return firstName + '-' + lastName;
}

joinFirstLastName(person); // "Nick-Anderson"
```

Destructuring is even more pleasant to use with [arrow functions](#arrow_func_concept):<br>
解構是更愉快去使用 [arrow functions](#arrow_func_concept):


```js
const joinFirstLastName = ({ firstName, lastName }) => firstName + '-' + lastName;

joinFirstLastName(person); // "Nick-Anderson"
```

- Array
- 陣列

Lets consider the following array:<br>
讓我們思考以下陣列:

```js
const myArray = ["a", "b", "c"];
```

Without destructuring<br>
沒用解構

```js
const x = myArray[0];
const y = myArray[1];
```

With destructuring<br>
用解構

```js
const [x, y] = myArray; // That's it ! 是的!

console.log(x) // "a"
console.log(y) // "b"
```

#### <a name="useful-resources-14"></a>有用資源

- [ES6 Features - Destructuring Assignment](http://es6-features.org/#ArrayMatching)
- [Destructuring Objects - WesBos](http://wesbos.com/destructuring-objects/)
- [ExploringJS - Destructuring](http://exploringjs.com/es6/ch_destructuring.html)

### <a name="array-methods---map--filter--reduce"></a> 陣列方法 - map / filter / reduce

*Map*, *filter* and *reduce* are array methods that are coming from a programming paradigm named [*functional programming*](https://medium.com/javascript-scene/master-the-javascript-interview-what-is-functional-programming-7f218c68b3a0).<br>
*Map*, *filter* and *reduce* 是陣列方法來自於一個編程範例稱作 [*functional programming*](https://medium.com/javascript-scene/master-the-javascript-interview-what-is-functional-programming-7f218c68b3a0).


To sum it up:<br>
總而言之:

- **Array.prototype.map()** takes an array, does something on its elements and returns an array with the transformed elements.
- **Array.prototype.map()** 採取一個陣列, 在其元素上做某事以及返回一個陣列與轉化的元素.
- **Array.prototype.filter()** takes an array, decides element by element if it should keep it or not and returns an array with the kept elements only
- **Array.prototype.filter()** 採取一個陣列, 逐個元素決定假如它應該保留它或不保留以及返回一個陣列與只保留的元素
- **Array.prototype.reduce()** takes an array and aggregates the elements into a single value (which is returned)
- **Array.prototype.reduce()** 採取一個陣列以及聚合這元素們為單個值 (返回哪一個)

I recommend to use them as much as possible in following the principles of functional programming because they are composable, concise and elegant.<br>
我建議盡量使用它們在以下函式程式設計原則中因為他們是可組合的, 簡潔與優雅的.



With those three methods, you can avoid the use of *for* and *forEach* loops in most situations. When you are tempted to do a *for* loop, try to do it with *map*, *filter* and *reduce* composed. You might struggle to do it at first because it requires you to learn a new way of thinking, but once you've got it things gets easier.<br>
用這三種方法, 你可以避免使用 *for* 和 *forEach* 迴圈在大多的情況. 當你被誘惑去做一個 *for* 迴圈, 嘗試用 *map* 去做它, *filter* 和 *reduce* 組合. 你或許掙扎去做它在一開始因為它需要你學一個新的思考的方法, 但一但你有了它事情變得更容易.

#### <a name="sample-code-2"></a> 示例代碼

```js
const numbers = [0, 1, 2, 3, 4, 5, 6];
const doubledNumbers = numbers.map(n => n * 2); // [0, 2, 4, 6, 8, 10, 12]
const evenNumbers = numbers.filter(n => n % 2 === 0); // [0, 2, 4, 6]
const sum = numbers.reduce((prev, next) => prev + next, 0); // 21
```

Compute total grade sum for students above 10 by composing map, filter and reduce:<br>
計算總成績加總給學生 10 以上透過 map 組成, filter and reduce:



```js
const students = [
  { name: "Nick", grade: 10 },
  { name: "John", grade: 15 },
  { name: "Julia", grade: 19 },
  { name: "Nathalie", grade: 9 },
];

const aboveTenSum = students
  .map(student => student.grade) // we map the students array to an array of their grades
  //我們 map 學生們陣列到一個他們成績的陣列
  .filter(grade => grade >= 10) // we filter the grades array to keep those above 10
  //我們 filter 保持那些10以上成績陣列
  .reduce((prev, next) => prev + next, 0); // we sum all the grades above 10 one by one
  //我們加總全部每一個10以上的成績

console.log(aboveTenSum) // 44 -- 10 (Nick) + 15 (John) + 19 (Julia), Nathalie below 10 is ignored 10以下被忽略
```


#### <a name="explanation-with-sample-code-0"></a> 示例代碼說明

Let's consider the following array of numbers for our examples:<br>
讓我們思考以下數字的陣列對於我們的例子:

```js
const numbers = [0, 1, 2, 3, 4, 5, 6];
```

##### <a name="arrayprototypemap"></a> Array.prototype.map()

```js
const doubledNumbers = numbers.map(function(n) {
  return n * 2;
});
console.log(doubledNumbers); // [0, 2, 4, 6, 8, 10, 12]
```

What's happening here? We are using .map on the *numbers* array, the map is iterating on each element of the array and passes it to our function. The goal of the function is to produce and return a new value from the one passed so that map can replace it.<br>
這裡發生什麼事? 被我們使用 .map 在這 *numbers* 陣列, 這個 map 正在迭代每一個元素從陣列之中以及通過它到我們的函式. 這個函式的目的是為了生產與返回一個新的值從一個通過以便 map 可以取代它.

Lets extract this function to make it more clear, just for this once:<br>
讓我們提取這個函式讓它更乾淨，只是為了這一次:


```js
const doubleN = function(n) { return n * 2; };
const doubledNumbers = numbers.map(doubleN);
console.log(doubledNumbers); // [0, 2, 4, 6, 8, 10, 12]
```

```numbers.map(doubleN)``` produces ```[doubleN(0), doubleN(1), doubleN(2), doubleN(3), doubleN(4), doubleN(5), doubleN(6)]``` which is equal to ```[0, 2, 4, 6, 8, 10, 12]```.<br>
```numbers.map(doubleN)``` 生產 ```[doubleN(0), doubleN(1), doubleN(2), doubleN(3), doubleN(4), doubleN(5), doubleN(6)]``` 哪一個等於 ```[0, 2, 4, 6, 8, 10, 12]```.

> **Note:** If you do not need to return a new array and just want to do a loop that has side effects, you might just want to use a for / forEach loop instead of a map.<br>
> **注意:** 如果你不需要返回一個陣列以及只想要執行迴圈那有副作用, 你或許只想要使用一個 for / forEach 迴圈取代一個 map.

##### <a name="arrayprototypefilter"></a> Array.prototype.filter()

```js
const evenNumbers = numbers.filter(function(n) {
  return n % 2 === 0; // true if "n" is par, false if "n" isn't
});
console.log(evenNumbers); // [0, 2, 4, 6]
```

We are using .filter on the *numbers* array, filter is iterating on each element of the array and passes it to our function. The goal of the function is to return a boolean that will determine whether the current value will be kept or not. Filter then returns the array with only the kept values.<br>
我們正在使用 .filter 在這 *numbers* 陣列, filter 正在迭代在每一個元素上在這陣列以及通過它到我們的函式中. 函式的目標是返回一個布爾值，它將確定當前值是否被保留. Filter 接著返回陣列只有保留值.


##### <a name="arrayprototypereduce"></a> Array.prototype.reduce()

The reduce method goal is to *reduce* all elements of the array it iterates on into a single value. How it aggregates those elements is up to you.<br>
這 reduce 方法目的是為了 *reduce* 每個正在迭代的陣列元素在進入一個單一值.它如何聚合這些元素取決於你.

```js
const sum = numbers.reduce(
  function(acc, n) {
    return acc + n;
  },
  0 // accumulator variable value at first iteration step
);

console.log(sum) //21
```

Just like for .map and .filter methods, .reduce is applied on an array and takes a function as the first parameter.<br>
就像.map和.filter方法一樣, .reduce應用於一個陣列，並將一個函式作為第一個參數。

This time though, there are changes:<br>
這一次, 有改變:

- .reduce takes two parameters
- .reduce 需要兩個參數

The first parameter is a function that will be called at each iteration step.<br>
第一個參數是在每個迭代步驟中調用的函式

The second parameter is the value of the accumulator variable (*acc* here) at the first iteration step (read next point to understand).<br>
第二個參數是累加器變數的值  (*acc* 在這裡) 在第一個迭代步驟 (閱讀下一點來了解).

- Function parameters
- 函式參數

The function you pass as the first parameter of .reduce takes two parameters. The first one (*acc* here) is the accumulator variable, whereas the second parameter (*n*) is the current element.<br>
這函式你作為第一個參數傳遞在 .reduce 中需要兩個參數. 第一個 (*acc* 在這裡) 是一個累加器變數, 而第二個參數 (*n*) 是現在的元素


The accumulator variable is equal to the return value of your function at the **previous** iteration step. At the first step of the iteration, *acc* is equal to the value you passed as .reduce second parameter.<br>
累加器變數等於函式的返回值在這 **previous** 迭代步驟. 在迭代的第一步, *acc* 等於你傳遞的 .reduce 第二個參數.

###### 迭代第一步

```acc = 0``` because we passed in 0 as the second parameter for reduce<br>
```acc = 0``` 因為我們通過0作為reduce的第二個參數

```n = 0``` first element of the *number* array<br>
```n = 0``` 在這 *number* 陣列中第一個元素

Function returns *acc* + *n* --> 0 + 0 --> 0<br>
函式回傳 *acc* + *n* --> 0 + 0 --> 0

###### 迭代第二步

```acc = 0``` because its the value the function returned at the previous iteration step<br>
```acc = 0``` 因為它在上一次迭代步驟中返回函式的值

```n = 1``` second element of the *number* array<br>
```n = 1``` 在這個 *number* 陣列中第二個元素

Function returns *acc* + *n* --> 0 + 1 --> 1<br>
函式返回 *acc* + *n* --> 0 + 1 --> 1

###### 迭代第三步

```acc = 1``` because its the value the function returned at the previous iteration step<br>
```acc = 1``` 因為它在上一次迭代步驟中返回函式的值

```n = 2``` third element of the *number* array<br>
```n = 2``` 在這個 *number* 陣列中第三個元素

Function returns *acc* + *n* --> 1 + 2 --> 3<br>
函式返回 *acc* + *n* --> 1 + 2 --> 3

###### 迭代第四步

```acc = 3``` because it's the value the function returned at the previous iteration step<br>
```acc = 3``` 因為它在上一次迭代步驟中返回函式的值

```n = 3``` fourth element of the *number* array<br>
```n = 3``` 在這個 *number* 陣列中第四個元素

Function returns *acc* + *n* --> 3 + 3 --> 6 <br>
函式返回 *acc* + *n* --> 3 + 3 --> 6 

###### [...] 迭代最後一步

```acc = 15``` because it's the value the function returned at the previous iteration step<br>
```acc = 15``` 因為它在上一次迭代步驟中返回函式的值

```n = 6``` last element of the *number* array<br>
```n = 6``` 在這個 *number* 陣列中最後一個元素

Function returns *acc* + *n* --> 15 + 6 --> 21<br>
函式返回 *acc* + *n* --> 15 + 6 --> 21

As it is the last iteration step, **.reduce** returns 21.<br>
因為它是最後的迭代步驟, **.reduce** 返回21.

#### <a name="external-resource-2"></a> 外部資源 

- [Understanding map / filter / reduce in JS](https://hackernoon.com/understanding-map-filter-and-reduce-in-javascript-5df1c7eee464)


### <a name="spread-operator-"></a> 展開運算子 "..."

The spread operator ```...``` has been introduced with ES2015 and is used to expand elements of an iterable (like an array) into places where multiple elements can fit.<br>
展開運算子 ```...``` 已經被提出在 ES2015 以及用於將一個可迭代的元素（像陣列）擴展到多個元素可以適合的地方。

#### <a name="sample-code-3"></a> 示例代碼

```js
const arr1 = ["a", "b", "c"];
const arr2 = [...arr1, "d", "e", "f"]; // ["a", "b", "c", "d", "e", "f"]
```

```js
function myFunc(x, y, ...params) {
  console.log(x);
  console.log(y);
  console.log(params)
}

myFunc("a", "b", "c", "d", "e", "f")
// "a"
// "b"
// ["c", "d", "e", "f"]
```

```js
const { x, y, ...z } = { x: 1, y: 2, a: 3, b: 4 };
console.log(x); // 1
console.log(y); // 2
console.log(z); // { a: 3, b: 4 }

const n = { x, y, ...z };
console.log(n); // { x: 1, y: 2, a: 3, b: 4 }
```


#### <a name="explanation-1"></a> 說明

##### <a name="in-iterables-like-array-25"></a> 迭代用法 (如同 array)

If we have the two following arrays:<br>
如果我們有以下兩個陣列:

```js
const arr1 = ["a", "b", "c"];
const arr2 = [arr1, "d", "e", "f"]; // [["a", "b", "c"], "d", "e", "f"]
```

*arr2* the first element is an array because *arr1* is injected as is into *arr2*. But what we want is *arr2* to be an array of letters. To do so, we can *spread* the elements of *arr1* into *arr2*.<br>
*arr2* 這個第一個元素是一個陣列因為 *arr1* 被注入作為進入 *arr2*. 但我們想要的是* arr2 *是一個字母數組.為此, 我們可以 *擴展* 這元素 *arr1* 到 *arr2*.

With spread operator<br>
用展開運算子


```js
const arr1 = ["a", "b", "c"];
const arr2 = [...arr1, "d", "e", "f"]; // ["a", "b", "c", "d", "e", "f"]
```

##### <a name="function-rest-parameter"></a> 函式剩餘參數

In function parameters, we can use the rest operator to inject parameters into an array we can loop in. There is already an **argument** object bound to every function that is equal to an array of all the parameters passed into the function.<br>
在函式參數中, 我們可以使用這個剩餘的運算子注入參數進入一個我們可以循環陣列. 已經有一個 **argument** 物件範圍到每一個函式等於一個陣列在全部參數通過進入這個函式中.

```js
function myFunc() {
  for (var i = 0; i < arguments.length; i++) {
    console.log(arguments[i]);
  }
}

myFunc("Nick", "Anderson", 10, 12, 6);
// "Nick"
// "Anderson"
// 10
// 12
// 6
```

But let's say that we want this function to create a new student with its grades and with its average grade. Wouldn't it be more convenient to extract the first two parameters into two separate variables, and then have all the grades in an array we can iterate over?<br>
但是讓我們說，我們希望這個功能可以創建一個具有成績和平均成績的新學生. 將前兩個參數提取為兩個單獨的變量不是更方便, 然後我們可以遍歷一個陣列中的所有成績?

That's exactly what the rest operator allows us to do!<br>
就是這樣剩餘運算子允許我們這麼做!



```js
function createStudent(firstName, lastName, ...grades) {
  // firstName = "Nick"
  // lastName = "Anderson"
  // [10, 12, 6] -- "..." takes all other parameters passed and creates a "grades" array variable that contains them
  //獲取傳遞的所有其他參數，並創建一個“grade” 陣列變數包含他們

  const avgGrade = grades.reduce((acc, curr) => acc + curr, 0) / grades.length; // computes average grade from grades
  //計算平均成績從每個成績

  return {
    firstName: firstName,
    lastName: lastName,
    grades: grades,
    avgGrade: avgGrade
  }
}

const student = createStudent("Nick", "Anderson", 10, 12, 6);
console.log(student);
// {
//   firstName: "Nick",
//   lastName: "Anderson",
//   grades: [10, 12, 6],
//   avgGrade: 9,33
// }
```

> **Note:** createStudent function is bad because we don't check if grades.length exists or is different from 0. But it's easier to read this way, so I didn't handle this case.<br>
> **注意:** createStudent 函式是壞的因為我們不檢查假如 grades.length 存在或不同從 0. 但這種方式很容易讀, 所以我不處理這種情況.


##### <a name="object-properties-spreading"></a> 物件屬性擴展

For this one, I recommend you read previous explanations about the rest operator on iterables and function parameters.<br>
對於這一個，我建議您閱讀有關剩餘運算子以前的有關迭代和函式參數的說明.


```js
const myObj = { x: 1, y: 2, a: 3, b: 4 };
const { x, y, ...z } = myObj; // object destructuring here 在這裡物件解構
console.log(x); // 1
console.log(y); // 2
console.log(z); // { a: 3, b: 4 }

// z is the rest of the object destructured: myObj object minus x and y properties destructured
// z 是這個物件的剩餘解構: myObj 物件減去 x 和 y 屬性解構

const n = { x, y, ...z };
console.log(n); // { x: 1, y: 2, a: 3, b: 4 }

// Here z object properties are spread into n
// 這裡 z 物件屬性擴展到 n 
```

#### <a name="external-resources"></a> 外部資源

- [TC39 - Object rest/spread](https://github.com/tc39/proposal-object-rest-spread)
- [Spread operator introduction - WesBos](https://github.com/wesbos/es6-articles/blob/master/28%20-%20Spread%20Operator%20Introduction.md)
- [JavaScript & the spread operator](https://codeburst.io/javascript-the-spread-operator-a867a71668ca)
- [6 Great uses of the spread operator](https://davidwalsh.name/spread-operator)

### <a name="object-property-shorthand-29"></a> Object 屬性簡寫

When assigning a variable to an object property, if the variable name is equal to the property name, you can do the following:<br>
當一個變數分配給一個物件屬性, 假如這個變數名稱等於這個屬性名稱, 你可以做以下:

```js
const x = 10;
const myObj = { x };
console.log(myObj.x) // 10
```

#### <a name="explanation-2"></a> 說明

Usually (pre-ES2015) when you declare a new *object literal* and want to use variables as object properties values, you would write this kind of code:<br>
通常（在ES2015之前）當你聲明一個新的 *物件字面量* 並且想要使用變數作為物件屬性值時，你會寫這樣的代碼:

```js
const x = 10;
const y = 20;

const myObj = {
  x: x, // assigning x variable value to myObj.x  //分配 x 變數值到 myObj.x 
  y: y // assigning y variable value to myObj.y  //分配 y 變數值到 myObj.y 
};

console.log(myObj.x) // 10
console.log(myObj.y) // 20
```

As you can see, this is quite repetitive because the properties name of myObj are the same as the variable names you want to assign to those properties.<br>
正如你看到的, 這是相當重複的因為這個屬性名稱與要分配給這些屬性的變數名稱相同

With ES2015, when the variable name is the same as the property name, you can do this shorthand:
用 ES2015, 當變量名與屬性名稱相同時可以進行簡化:

```js
const x = 10;
const y = 20;

const myObj = {
  x,
  y
};

console.log(myObj.x) // 10
console.log(myObj.y) // 20
```

#### <a name="external-resources-31"></a> 外部資源

- [Property shorthand - ES6 Features](http://es6-features.org/#PropertyShorthand)

### <a name="promises"></a> Promises

A promise is an object which can be returned synchronously from an asynchronous function ([ref](https://medium.com/javascript-scene/master-the-javascript-interview-what-is-a-promise-27fc71e77261#3cd0)).<br>
一個 promise 是一個物件可以同步地被返回從一個非同步函式 ([ref](https://medium.com/javascript-scene/master-the-javascript-interview-what-is-a-promise-27fc71e77261#3cd0)).

Promises can be used to avoid [callback hell](http://callbackhell.com/), and they are more and more frequently encountered in modern JavaScript projects.<br>
Promises 可以被用來避免 [回呼地獄](http://callbackhell.com/), 以及它們是越來越頻繁地遇到在現代 JavaScript 專案中.

#### <a name="sample-code-4"></a> 示例代碼

```js
const fetchingPosts = new Promise((res, rej) => {
  $.get("/posts")
    .done(posts => res(posts))
    .fail(err => rej(err));
});

fetchingPosts
  .then(posts => console.log(posts))
  .catch(err => console.log(err));
```

#### <a name="explanation-3"></a> 說明

When you do an *Ajax request* the response is not synchronous because you want a resource that takes some time to come. It even may never come if the resource you have requested is unavailable for some reason (404).<br>
當你做一個 *Ajax 請求* 這個反應不是同步因為你想要一個資源需要一些時間. 它甚至可能永遠不會來假如這個資源你已經請求由於某些原因不可用 (404).

To handle that kind of situations, ES2015 has given us *promises*. Promises can have three different states:<br>
為了處理這些情況, ES2015 已經給我們 *promises*. Promises 可以有三種不同狀態:

- Pending 進行中
- Fulfilled 已成功
- Rejected 已失敗

Let's say we want to use promises to handle an Ajax request to fetch the resource X.<br>
讓我們說我們想要使用 promises 處理一個 Ajax 請求為了取這個資源 X.

##### <a name="create-the-promise"></a> 創建 promise

We firstly are going to create a promise. We will use the jQuery get method to do our Ajax request to X.<br>
我們首先要創建一個 promise. 我們將會使用這個 jQuery 取得方法做我們的 Ajax 請求給 X.


```js
const xFetcherPromise = new Promise( // Create promise using "new" keyword and store it into a variable
// 創建一個 promise 使用 "new" 關鍵字以及將其儲存在變數中
  function(resolve, reject) { // Promise constructor takes a function parameter which has resolve and reject parameters itself
  // Promise 構造函數需要它自己的解析和拒絕的函式參數
    $.get("X") // Launch the Ajax request 啟動這個 Ajax請求
      .done(function(X) { // Once the request is done... 請求完成...
        resolve(X); // ... resolve the promise with the X value as parameter
        // ... 解析這個 promise 用這個 X 作為參數值
      })
      .fail(function(error) { // If the request has failed... 假如請求失敗...
        reject(error); // ... reject the promise with the error as parameter
        //...拒絕這個 promise 用這個 error 作為參數
      });
  }
)
```

As seen in the above sample, the Promise object takes an *executor* function which takes two parameters **resolve** and **reject**. Those parameters are functions which when called are going to move the promise *pending* state to respectively a *fulfilled* and *rejected* state.<br>
如上例所示, 這個 Promise 物件採取 *executor* 函式需要兩個參數 **resolve** 以及 **reject**. 那些參數是當參數被取用將要移動這個 promise *進行中* 狀態到各自的一個 *已成功* 和 *已失敗* 狀態時的功能


The promise is in pending state after instance creation and it's *executor* function is executed immediately. Once one of the function *resolve* or *reject* is called in the *executor* function, the promise will call its associated handlers.<br>
這個 promise 是在進行中狀態在實例創建之後以及它是 *執行者* 函式被立即執行. 一次一個函式中的 *解析* 或 *已失敗* 在函式中被稱作 *執行者*, 這個 promise 會呼叫它的相關處理器.

##### <a name="promise-handlers-usage"></a> Promise 處理器運用

To get the promise result (or error), we must attach to it handlers by doing the following:<br>
為了取得這個 promise 結果 (或 錯誤), 我們必須通過執行以下操作來附加到處理器：

```js
xFetcherPromise
  .then(function(X) {
    console.log(X);
  })
  .catch(function(err) {
    console.log(err)
  })
```

If the promise succeeds, *resolve* is executed and the function passed as ```.then``` parameter is executed.<br>
如果這個 promise 成功, *解析* 被執行以及這個函式通過 ```.then``` 參數被執行.

If it fails, *reject* is executed and the function passed as ```.catch``` parameter is executed.<br>
如果它失敗, *拒絕* 被執行以及這個函式通過 ```.catch``` 參數被執行.

> **Note :** If the promise has already been fulfilled or rejected when a corresponding handler is attached, the handler will be called, so there is no race condition between an asynchronous operation completing and its handlers being attached. [(Ref: MDN)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise#Description)<br>
> **注意 :** 如果這個 promise 已經成功或拒絕當一個對應的處理器被附加, 這個處理器將會被呼叫, 所以沒有競爭條件在非同步操作完成之間以及它的處理器被附加. [(Ref: MDN)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise#Description)

#### <a name="external-resources-32"></a> 外部資源

- [JavaScript Promises for dummies - Jecelyn Yeen](https://scotch.io/tutorials/javascript-promises-for-dummies)
- [JavaScript Promise API - David Walsh](https://davidwalsh.name/promises)
- [Using promises - MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Using_promises)
- [What is a promise - Eric Elliott](https://medium.com/javascript-scene/master-the-javascript-interview-what-is-a-promise-27fc71e77261)
- [JavaScript Promises: an Introduction - Jake Archibald](https://developers.google.com/web/fundamentals/getting-started/primers/promises)
- [Promise documentation - MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise)

### <a name="template-literals"></a> 模板字面量

Template literals is an [*expression interpolation*](https://en.wikipedia.org/wiki/String_interpolation) for single and multiple-line strings.<br>
模板字面輛是一個 [*表達式插值*](https://en.wikipedia.org/wiki/String_interpolation) for single and multiple-line strings.

In other words, it is a new string syntax in which you can conveniently use any JavaScript expressions (variables for instance).<br>
在另一方面, 它是一個新的字串語法您可以在其中方便地使用任何 JavaScript 表達式 (例如變數).

#### <a name="sample-code-5"></a> 示例代碼

```js
const name = "Nick";
`Hello ${name}, the following expression is equal to four : ${2+2}`;

// Hello Nick, 以下表達式等於4 : 4
```

#### <a name="external-resources-2"></a> 外部資源

- [String interpolation - ES6 Features](http://es6-features.org/#StringInterpolation)
- [ES6 Template Strings - Addy Osmani](https://developers.google.com/web/updates/2015/01/ES6-Template-Strings)

### <a name="tagged-template-literals"></a> 標記模板字面量

Template tags are *functions that can be prefixed to a [template literal](#template-literals)*. When a function is called this way, the first parameter is an array of the *strings* that appear between the template's interpolated variables, and the subsequent paremeters are the interpolated values. Use a spread operator `...` to capture all of them. [(Ref: MDN)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Template_literals#Tagged_template_literals).<br>
模板標籤是* 可以作為前綴 [template literal](#template-literals) 的函式 *.當一個函式用這個方式呼叫,第一個參數是一個陣列在這 *字串* 出現在模板的插值變數之間,並且隨後的參數是插值. 使用一個展開運算子 `...` 抓取他們的全部 [(Ref: MDN)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Template_literals#Tagged_template_literals).


> **Note :** A famous library named [styled-components](https://www.styled-components.com/) heavily relies on this feature.<br>
> **注意 :** 一個知名函式庫叫作[styled-components](https://www.styled-components.com/) 重度依賴於此功能.

Below is a toy example on they work.<br>
以下是一個他們運行小例子
```js
function highlight(strings, ...values) {
  const interpolation = strings.reduce((prev, next) => {
    return prev + next + (values.shift() || "");
  }, "");

  return `<mark>${interpolation}</mark>`;
}

const condiment = "jam";
const meal = "toast";

highlight`I like ${condiment} on ${meal}.`;
// "<mark>I like jam on toast.</mark>"
```

A more interesting example: <br>
一個更有趣的例子:
```js
function comma(strings, ...values) {
  return strings.reduce((prev, next) => {
    let value = values.shift() || [];
    value = value.join(", ");
    return prev + next + value;
  }, "");
}

const snacks = ['apples', 'bananas', 'cherries'];
comma`I like ${snacks} to snack on.`;
// "I like apples, bananas, cherries to snack on." 我喜歡吃蘋果, 香蕉, 櫻桃
```

#### <a name="external-resources-4"></a> 外部資源
- [Wes Bos on Tagged Template Literals](http://wesbos.com/tagged-template-literals/)
- [Library of common template tags](https://github.com/declandewet/common-tags)

### <a name="imports--exports"></a> Imports / Exports

ES6 modules are used to access variables or functions in a module explicitly exported by the modules it imports.<br>
ES6模塊被使用來存取變數或函式在一個模塊明確地輸出透過這模塊輸入.


I highly recommend to take a look at MDN resources on import/export (see external resources below), it is both straightforward and complete.<br>
我強烈建議您查看MDN資源在 import/export , 它既簡單又完整.

#### <a name="explanation-with-sample-code-1"></a> 示例代碼說明

##### <a name="named-exports"></a> 命名 exports

Named exports are used to export several values from a module.<br>
命名的導出用於從模塊輸出多個值.

> **Note :** You can only name-export [first-class citizens](https://en.wikipedia.org/wiki/First-class_citizen) that have a name.<br>
> **注意 :** 你可以只有輸出名稱 [first-class citizens](https://en.wikipedia.org/wiki/First-class_citizen) 有一個名稱

```js
// mathConstants.js
export const pi = 3.14;
export const exp = 2.7;
export const alpha = 0.35;

// -------------

// myFile.js
import { pi, exp } from './mathConstants.js'; // Named import -- destructuring-like syntax
//命名輸入 -- 類似解構語法
console.log(pi) // 3.14
console.log(exp) // 2.7

// -------------

// mySecondFile.js
import * as constants from './mathConstants.js'; // Inject all exported values into constants variable
//注入全部輸出值進常量變數
console.log(constants.pi) // 3.14
console.log(constants.exp) // 2.7
```

While named imports looks like *destructuring*, they have a different syntax and are not the same. They don't support default values nor *deep* destructuring.<br>
而命名的輸入看起來像 *解構*,他們有一個不同的語法與不同.他們不支援預設值也不支援 *深度* 解構.

Besides, you can do aliases but the syntax is different from the one used in destructuring:<br>
此外, 你可以您可以使用別名，但語法與在解構中使用的語法不同:

```js
import { foo as bar } from 'myFile.js'; // foo is imported and injected into a new bar variable
// foo 被輸入並注入到一個新的 bar 變數中
```


##### <a name="default-import--export"></a> 預設 import / export

Concerning the default export, there is only a single default export per module. A default export can be a function, a class, an object or anything else. This value is considered the "main" exported value since it will be the simplest to import. [Ref: MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/export#Description)<br>
關於預設輸出, 只有一個單個預設輸出給模塊. A 預設輸出可以是一個函式, 一個類, 一個物件或其他任何東西. 這個值是週密考慮過的 "主要" 輸出值因為它將是最簡單的輸入. [Ref: MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/export#Description)

```js
// coolNumber.js
const ultimateNumber = 42;
export default ultimateNumber;

// ------------

// myFile.js
import number from './coolNumber.js';
// Default export, independently from its name, is automatically injected into number variable;
//預設輸出, 獨立於它的命名, 是自動地注入進 number 變數;
console.log(number) // 42
```

Function exporting:<br>
函式輸出: 

```js
// sum.js
export default function sum(x, y) {
  return x + y;
}
// -------------

// myFile.js
import sum from './sum.js';
const result = sum(1, 2);
console.log(result) // 3
```

#### <a name="external-resources-3"></a> 外部資源

- [ES6 Modules in bulletpoints](https://ponyfoo.com/articles/es6#modules)
- [Export - MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/export)
- [Import - MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/import)
- [Understanding ES6 Modules](https://www.sitepoint.com/understanding-es6-modules/)
- [Destructuring special case - import statements](https://ponyfoo.com/articles/es6-destructuring-in-depth#special-case-import-statements)
- [Misunderstanding ES6 Modules - Kent C. Dodds](https://medium.com/@kentcdodds/misunderstanding-es6-modules-upgrading-babel-tears-and-a-solution-ad2d5ab93ce0)
- [Modules in JavaScript](http://exploringjs.com/es6/ch_modules.html#sec_modules-in-javascript)

### <a name="-javascript-this"></a> JavaScript *this*

*this* operator behaves differently than in other languages and is in most cases determined by how a function is called. ([Ref: MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/this)).<br>
*this* 運算子比其他語言表現不同地, 並且在大多數情況下由函式的調用決定. ([Ref: MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/this)).

This notion is having many subtleties and being quite hard, I highly suggest you to deep dive in the external resources below. Thus, I will provide what I personally have in mind to determine what *this* is equal to. I have learned this tip from [this article written by Yehuda Katz](http://yehudakatz.com/2011/08/11/understanding-javascript-function-invocation-and-this/).<br>
這個概念有許多微妙之處以及相當難, 我強烈建議您深入了解下面的外部資源. 因此, 我將提供我個人想到要確定 *this* 等於什麼. 我已經學習 this 訣竅從 [this article written by Yehuda Katz](http://yehudakatz.com/2011/08/11/understanding-javascript-function-invocation-and-this/).

```js
function myFunc() {
  ...
}

// After each statement, you find the value of *this* in myFunc
//在每個聲明之後,你發現這個在 myFunc 中的  *this* 值

myFunc.call("myString", "hello") // "myString" -- first .call parameter value is injected into *this*
// "myString" -- 首先 .call參數值被注入進 *this*

// In non-strict-mode
//在不嚴格模式
myFunc("hello") // window -- myFunc() is syntax sugar for myFunc.call(window, "hello")
// window -- myFunc() 是語法糖對於 myFunc.call(window, "hello")

// In strict-mode
//在嚴格模式
myFunc("hello") // undefined -- myFunc() is syntax sugar for myFunc.call(undefined, "hello")
// undefined -- myFunc() 是語法糖對於 myFunc.call(undefined, "hello")
```

```js
var person = {
  myFunc: function() { ... }
}

person.myFunc.call(person, "test") // person Object -- first call parameter is injected into *this*
// person 物件 -- 首先 call 參數被注入進 *this*
person.myFunc("test") // person Object -- person.myFunc() is syntax sugar for person.myFunc.call(person, "test")
// person 物件 -- person.myFunc() 是語法糖對於 person.myFunc.call(person, "test")

var myBoundFunc = person.myFunc.bind("hello") // Creates a new function in which we inject "hello" in *this* value
// 創建一個新函式在我們注入 "hello"值 進  *this* 
person.myFunc("test") // person Object -- The bind method has no effect on the original method
// person 物件 -- 這個 bind 方法沒效果在這原型方法
myBoundFunc("test") // "hello" -- myBoundFunc is person.myFunc with "hello" bound to *this*
// "hello" -- myBoundFunc 是 person.myFunc 隨著 "hello" 限制 *this*
```

#### <a name="external-resources-42"></a> 外部資源

- [Understanding JavaScript Function Invocation and "this" - Yehuda Katz](http://yehudakatz.com/2011/08/11/understanding-javascript-function-invocation-and-this/)
- [JavaScript this - MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/this)

### <a name="class"></a> Class

JavaScript is a [prototype-based](https://en.wikipedia.org/wiki/Prototype-based_programming) language (whereas Java is [class-based](https://en.wikipedia.org/wiki/Class-based_programming) language, for instance). ES6 has introduced JavaScript classes which are meant to be a syntactic sugar for prototype-based inheritance and **not** a new class-based inheritance model ([ref](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes)).<br>
JavaScript 是一個 [基於原型](https://en.wikipedia.org/wiki/Prototype-based_programming) 語言(而 Java 是 [基於類](https://en.wikipedia.org/wiki/Class-based_programming) 語言, 對於實例). ES6引入了 JavaScript 類，它們是一種語法糖給基於原型繼承以及 **不是** 一個新的基於類繼承模型([ref](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes)).

The word *class* is indeed error prone if you are familiar with classes in other languages. If you do, avoid assuming how JavaScript classes work on this basis and consider it an entirely different notion.<br>
這個字 *class* 確實是錯誤傾向於假如你熟悉其他語言的類. 如果你做, 避免假設JavaScript類是如何工作的在這個基礎以及認為它是一個完全不同的概念中.


Since this document is not an attempt to teach you the language from the ground up, I will believe you know what prototypes are and how they behave. But here are some links I found great to understand this notion:<br>
因為這個文件不一個嘗試教你語言從頭開始, 我將相信你知道原型和它們的行為. 但這裡是一些鏈結我發現很好去了解這個概念:


- [Understanding Prototypes in JS - Yehuda Katz](http://yehudakatz.com/2011/08/12/understanding-prototypes-in-javascript/)
- [A plain English guide to JS prototypes - Sebastian Porto](http://sporto.github.io/blog/2013/02/22/a-plain-english-guide-to-javascript-prototypes/)
- [Inheritance and the prototype chain - MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Inheritance_and_the_prototype_chain)

#### <a name="samples"></a> 示例

Before ES6, prototype syntax:<br>
在 ES6 之前, 原型語法:

```js
var Person = function(name, age) {
  this.name = name;
  this.age = age;
}
Person.prototype.stringSentence = function() {
  return "Hello, my name is " + this.name + " and I'm " + this.age;
}
```

With ES6 class syntax: <br>
使用 ES6 語法:


```js
class Person {
  constructor(name, age) {
    this.name = name;
    this.age = age;
  }

  stringSentence() {
    return "Hello, my name is " + this.name + " and I'm " + this.age;
  }
}

const myPerson = new Person("Manu", 23);
console.log(myPerson.age) // 23
console.log(myPerson.stringSentence()) // "Hello, my name is Manu and I'm 23
// 你好, 我的名字是馬努我23歲
```

#### <a name="external-resources-5"></a> 外部資源

For prototype understanding:<br>
對於了解原型:

- [Understanding Prototypes in JS - Yehuda Katz](http://yehudakatz.com/2011/08/12/understanding-prototypes-in-javascript/)
- [A plain English guide to JS prototypes - Sebastian Porto](http://sporto.github.io/blog/2013/02/22/a-plain-english-guide-to-javascript-prototypes/)
- [Inheritance and the prototype chain - MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Inheritance_and_the_prototype_chain)

For classes understanding:<br>
對於了解類:

- [ES6 Classes in Depth - Nicolas Bevacqua](https://ponyfoo.com/articles/es6-classes-in-depth)
- [ES6 Features - Classes](http://es6-features.org/#ClassDefinition)
- [JavaScript Classes - MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes)

### <a name="async-await"></a> Async Await

In addition to [Promises](#promises), there is a new syntax you might encounter to handle asynchronous code named *async / await*.<br>
除了 [Promises](#promises), 有一個新的語法你可能遇到處理非同步程式碼稱為 *async / await*.

The purpose of async/await functions is to simplify the behavior of using promises synchronously and to perform some behavior on a group of Promises. Just as Promises are similar to structured callbacks, async/await is similar to combining generators and promises. ([Ref: MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/async_function))<br>
async/await 函式的目的是為了簡化行為使用 promises 同步地並在一組 Promise 上執行一些行為. 正如 Promise 類似於結構化回調, async/await 類似結合產生器與 promises. ([Ref: MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/async_function))

> **Note :** You must understand what are promises and how they work before trying to understand async / await since they rely on it.<br>
> **注意 :**  你必須了解什麼是 promises 以及它們如何運作在嘗試去了解 async / await 之前因為他們依賴於它.

> **Note 2:** [*await* must be used in an *async* function](https://hackernoon.com/6-reasons-why-javascripts-async-await-blows-promises-away-tutorial-c7ec10518dd9#f3f0), which means that you can't use await in the top level of our code since that is not inside an async function.<br>
> **Note 2:** [*await* 必須被使用在一個 *async* 函式中]

#### <a name="sample-code-6"></a> 示例代碼

```js
async function getGithubUser(username) { // async keyword allows usage of await in the function and means function returns a promise
// async 關鍵字允許 await 的使用在函式中以及意味著函式返回一個 promise
  try { // this is how errors are handled with async / await
  //這是如何用 async / await 處理錯誤
    const response = await fetch(`https://api.github.com/users/${username}`); // "synchronously" waiting fetch promise to resolve before going to next line
    //"同步地" 等待取回 promise 給  resolve 在下一行之前
    return response.json();
  } catch (err) {
    alert(err);
  }
}

getGithubUser('mbeaudru').then(user => console.log(user)); // logging user response - cannot use await syntax since this code isn't in async function
//登入使用者響應 - 不能使用 await 語法因為這個程式碼不是 async 函式
```

#### <a name="explanation-with-sample-code-2"></a> 示例代碼說明

*Async / Await* is built on promises but they allow a more imperative style of code.<br>
*Async / Await* 被建立在 promises 上但他們允許一個必要的程式碼的樣式.

*async* operator turns a function into a *promise* in which you can use the *await* operator.<br>
*async* 運算子將函式轉換成一個 *promise* 在每一個這個 *await* 你可以使用

```js
async function myFunc() {
  // we can use await operator because this function is async
  //我們可以使用 await 運算子 因為這個函式是非同步
  try {
    return "hello world";
  } catch(e) {
    throw new Error();
  }
}

myFunc().then(msg => console.log(msg)) // "hello world" -- myFunc is turned into a promise because of async operator
// "hello world" -- myFunc 被變成了一個 promise 因為 async 運算子
```

When the *return* statement of an async function is reached, the promise is fulfilled with the value returned. If an error is thrown inside an async function, the promise state will turn to *rejected*.<br>
當這個 *返回* 聲明一個非同步函式被實現, 這個 promise 已被完成隨著這個返回值. 如果一個錯誤被拋出在一個非同步函式裡面, 這個 promise 狀態將變成 *已失敗*.

*await* operator is used to wait for a *Promise* to be fulfilled and only can be used inside an *async* function body. When encountered, the code execution is paused until the promise is fulfilled.<br>
*await* 運算子被用來等待一個 *Promise* 變成已成功 以及只有可以被一個裡面的 *async* 函式內文使用. 遇到時, 這個程式碼執行被暫停直到這個 promise 是已完成.

> **Note :** *fetch* is a Promise that allows to do an AJAX request<br>
> **注意 :** *fetch* 是一個 Promise 允許做一個 AJAX 請求

Let's see how we could fetch a github user with promises first:<br>
讓我們看我們可以獲取一個 github 使用者首先用 promises:

```js
function getGithubUser(username) {
  return new Promise((resolve, reject) => {
    fetch(`https://api.github.com/users/${username}`)
      .then(response => {
        const user = response.json();
        resolve(user);
      })
      .catch(err => reject(err));
  })
}

getGithubUser('mbeaudru')
  .then(user => console.log(user))
  .catch(err => console.log(err));
```

Here's the *async / await* equivalent:<br>
*async / await* 在這裡是相等的:

```js
async function getGithubUser(username) { // promise + await keyword usage allowed
// promise + await 關鍵字允許使用
  try { // We handle async function errors with try / catch
  //我們處理非同步函式錯誤用try / catch
    const response = await fetch(`https://api.github.com/users/${username}`); // Execution stops here until fetch promise is fulfilled.
    //執行暫停直到獲取 promise 成功
    const user = response.json();
    return user; // equivalent of resolving the getGithubUser promise with user value.
    //相當於用使用者的值解析這 getGithubUser promise
  } catch (err) {
    throw new Error(err); // equivalent of rejecting getGithubUser promise with err value.
    //相當於用錯誤的值解析這 getGithubUser promise
  }
}

getGithubUser('mbeaudru')
  .then(user => console.log(user))
  .catch(err => console.log(err));
```

*async / await* syntax is particularly convenient when you need to chain promises that are interdependent.<br>
*async / await* 語法是特別方便的當你需要鏈結 promises 是相互依賴的.

For instance, if you need to get a token in order to be able to fetch a blog post on a database and then the author informations:<br>
例如, 如果你必須獲取一個憑證以便能夠在資料庫上獲取部落格文章以及作者資訊:

```js
async function fetchPostById(postId) {
  try {
    const token = await fetch('token_url');
    const post = await fetch(`/posts/${postId}?token=${token}`);
    const author = await fetch(`/users/${post.authorId}`);

    post.author = author;
    return post;
  } catch(e) {
    throw new Error(e);
  }
}

fetchPostById('gzIrzeo64')
  .then(post => console.log(post))
  .catch(err => console.log(err));
```

> **Note :** As you can see, *try / catch* are necessary to handle errors. But if you are making *express routes*, you can use a middleware to avoid error handling and have a very pleasant code to read. See [this article from Alex Bazhenov](https://medium.com/@Abazhenov/using-async-await-in-express-with-node-8-b8af872c0016) to learn more.<br>
> **注意 :** 正如你看到的, *try / catch* 去處理錯誤是必要的. 但假如你正在做 *表達路由*, 你可以使用一個中間件來避免錯誤處理以及有一個非常愉快的程式碼可讀. 看看 [這個文章來自 Alex Bazhenov](https://medium.com/@Abazhenov/using-async-await-in-express-with-node-8-b8af872c0016) 來學習更多.

#### <a name="external-resources-6"></a> 外部資源

- [Async/Await - JavaScript.Info](https://javascript.info/async-await)
- [ES7 Async/Await](http://rossboucher.com/await/#/)
- [6 Reasons Why JavaScript’s Async/Await Blows Promises Away](https://hackernoon.com/6-reasons-why-javascripts-async-await-blows-promises-away-tutorial-c7ec10518dd9)
- [JavaScript awaits](https://dev.to/kayis/javascript-awaits)
- [Using Async Await in Express with Node 8](https://medium.com/@Abazhenov/using-async-await-in-express-with-node-8-b8af872c0016)
- [Async Function](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/async_function)
- [Await](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/await)
- [Using async / await in express with node 8](https://medium.com/@Abazhenov/using-async-await-in-express-with-node-8-b8af872c0016)

### <a name="truthy--falsy"></a> Truthy / Falsy

In JavaScript, a truthy or falsy value is a value that is being casted into a boolean when evaluated in a boolean context. An example of boolean context would be the evaluation of an ```if``` condition:<br>
在 JavaScript 中, 一個真的或假的值是一個值正在鑄造成一個布林值當執行在一個布林環境. 一個布林環境的例子將被這個值的計算在一個 ```if``` 條件:

Every value will be casted to ```true``` unless they are equal to:<br>
每一個值將被鑄造給 ```true``` 直到他們相等:

- false
- 0
- "" (empty string)
- null
- undefined
- NaN

Here are examples of *boolean context*:<br>
這裡是一個 *布林語意* 的例子:

- ```if``` condition evaluation 條件值的計算

```js
if (myVar) {}
```

```myVar``` can be any [first-class citizen](https://en.wikipedia.org/wiki/First-class_citizen) (variable, function, boolean) but it will be casted into a boolean because it's evaluated in a boolean context.<br>
```myVar``` 可以被任何 [第一類居民](https://en.wikipedia.org/wiki/First-class_citizen) (變數, 函式, 布林值) 但它將被鑄造成一個布林值因為它是直行在一個布林環境.

- After logical **NOT** ```!``` operator<br>
- 在邏輯 **NOT** ```!``` 運算子


This operator returns false if its single operand can be converted to true; otherwise, returns true.<br>
這個運算子返回 false 假如它的單個運算可以被轉換成 true; 否則, 返回 true.

```js
!0 // true -- 0 is falsy so it returns true
// true -- 0 是假的所以它返回 true
!!0 // false -- 0 is falsy so !0 returns true so !(!0) returns false
//// false -- 0 是假的所以 !0 返回 true 所以 !(!0) 返回  false
!!"" // false -- empty string is falsy so NOT (NOT false) equals false
// false -- 空字串是假的所以NOT (NOT false) 等於 false
```

- With the *Boolean* object constructor<br>
用這個 *Boolean* 物件構造函數

```js
new Boolean(0) // false
new Boolean(1) // true
```

- In a ternary evaluation 在一個三元值的計算

```js
myVar ? "truthy" : "falsy"
```

myVar is evaluated in a boolean context.<br>
myVar 被計算在一個布林環境


## <a name="glossary"></a> 詞彙表

### <a name="-scope"></a> 範圍

The context in which values and expressions are "visible," or can be referenced. If a variable or other expression is not "in the current scope," then it is unavailable for use.<br>
這在環境在值與表達式是 "變數" 中或可以被參考, 如果一個變數或其他表達式不是 "在現在的範圍中" 它不能使用.

Source: [MDN](https://developer.mozilla.org/en-US/docs/Glossary/Scope)

### <a name="-variable-mutation"></a> 變數變化

A variable is said to have been mutated when its initial value has changed afterward.<br>
一個變數被稱作是已經改變當它的初始值已經改變之後

```js
var myArray = [];
myArray.push("firstEl") // myArray is being mutated myArray已經被改變
```

A variable is said to be *immutable* if it can't be mutated.<br>
一個變數被稱作是 *不可變* 假如它不能被改變

[Check MDN Mutable article](https://developer.mozilla.org/en-US/docs/Glossary/Mutable) 對於更多細節.
