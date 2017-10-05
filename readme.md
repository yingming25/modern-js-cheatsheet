# <a name="modern-javascript-cheatsheet"></a> Modern JavaScript Cheatsheet

![Modern JavaScript cheatsheet](https://i.imgur.com/aexPxMb.png)
<small>圖像 信用: [Ahmad Awais ⚡️](https://github.com/ahmadawais)</small>

## <a name="introduction"></a> 介紹

### <a name="motivation"></a> 動機

這個文件是一個給 JavaScript 的作弊表 在現代的示例程式碼和現代專案你將會經常地遭遇到.

這個指南不打算從頭開始教你 JavaScript ,
而是為了幫助有基本知識的開發者可以盡力去熟悉用現代代碼庫( 或讓我們說為了學 React 實例 )因為 JavaScript  概念被使用.

此外,我將有時提供個人秘訣可能是可爭論的但是將小心提到它是一個個人建議當我這樣做.


> **注意:** 這裡介紹的大部分概念來自於 JavaScript 語言更新（ES2015，通常稱為ES6）. 透過這個更新你可以發現新特色 [這裡](http://es6-features.org); 做得很好.

### <a name="complementary-resources"></a> 補充資源

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
      - [示例](#示例)
      - [外部資源](#external-resources-5)
    + [Async Await](#async-await)
      - [示例代碼](#sample-code-6)
      - [示例代碼說明](#explanation-with-sample-code-2)
      - [外部資源](#external-resources-6)
    + [Truthy / Falsy](#truthy--falsy)
      - [外部資源](#external-resources-7)
  * [詞彙表](#glossary)
    + [範圍](#-scope)
    + [變數變化](#-variable-mutation)


## <a name="notions"></a> 概念

### <a name="variable-declaration-var-const-let"></a> 變數宣告: var, const, let

In JavaScript, there are three keywords available to declare a variable, and each has its differences. Those are ```var```, ```let``` and ```const```.

#### <a name="short-explanation"></a> 簡短說明

Variables declared with ```const``` keyword can't be reassigned, while ```let``` and ```var``` can.

I recommend always declaring your variables with ```const``` by default, and with ```let``` if you need to *mutate* it or reassign it later.

<table>
  <tr>
    <th></th>
    <th>Scope</th>
    <th>Reassignable</th>
    <th>Mutable</th>
   <th><a href="#tdz_sample">Temporal Dead Zone</a></th>
  </tr>
  <tr>
    <th>const</th>
    <td>Block</td>
    <td>No</td>
    <td><a href="#const_mutable_sample">Yes</a></td>
    <td>Yes</td>
  </tr>
  <tr>
    <th>let</th>
    <td>Block</td>
    <td>Yes</td>
    <td>Yes</td>
    <td>Yes</td>
  </tr>
   <tr>
    <th>var</th>
    <td>Function</td>
    <td>Yes</td>
    <td>Yes</td>
    <td>No</td>
  </tr>
</table>

#### <a name="sample-code"></a> 示例代碼

```javascript
const person = "Nick";
person = "John" // Will raise an error, person can't be reassigned
```

```javascript
let person = "Nick";
person = "John";
console.log(person) // "John", reassignment is allowed with let
```

#### <a name="detailed-explanation"></a> 詳細說明

The [*scope*](#scope_def) of a variable roughly means "where is this variable available in the code".

##### var

```var``` declared variables are *function scoped*, meaning that when a variable is created in a function, everything in that function can access that variable. Besides, a *function scoped* variable created in a function can't be accessed outside this function.

I recommend you to picture it as if an *X scoped* variable meant that this variable was a property of X.

```javascript
function myFunction() {
  var myVar = "Nick";
  console.log(myVar); // "Nick" - myVar is accessible inside the function
}
console.log(myVar); // Throws a ReferenceError, myVar is not accessible outside the function.
```

Still focusing on the variable scope, here is a more subtle example:

```javascript
function myFunction() {
  var myVar = "Nick";
  if (true) {
    var myVar = "John";
    console.log(myVar); // "John"
    // actually, myVar being function scoped, we just erased the previous myVar value "Nick" for "John"
  }
  console.log(myVar); // "John" - see how the instructions in the if block affected this value
}
console.log(myVar); // Throws a ReferenceError, myVar is not accessible outside the function.
```

Besides, *var* declared variables are moved to the top of the scope at execution. This is what we call [var hoisting](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/var#var_hoisting).

This portion of code:

```js
console.log(myVar) // undefined -- no error raised
var myVar = 2;
```

is understood at execution like:

```js
var myVar;
console.log(myVar) // undefined -- no error raised
myVar = 2;
```

##### let

```var``` and ```let ``` are about the same, but ```let``` declared variables

- are *block scoped*
- are **not** accessible before they are assigned
- can't be re-declared in the same scope

Let's see the impact of block-scoping taking our previous example:

```javascript
function myFunction() {
  let myVar = "Nick";
  if (true) {
    let myVar = "John";
    console.log(myVar); // "John"
    // actually, myVar being block scoped, we just created a new variable myVar.
    // this variable is not accessible outside this block and totally independent
    // from the first myVar created !
  }
  console.log(myVar); // "Nick", see how the instructions in the if block DID NOT affect this value
}
console.log(myVar); // Throws a ReferenceError, myVar is not accessible outside the function.
```

<a name="tdz_sample"></a> Now, what it means for *let* (and *const*) variables for not being accessible before being assigned:

```js
console.log(myVar) // raises a ReferenceError !
let myVar = 2;
```

By contrast with *var* variables, if you try to read or write on a *let* or *const* variable before they are assigned an error will be raised. This phenomenon is often called [*Temporal dead zone*](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/let#Temporal_Dead_Zone_and_errors_with_let) or *TDZ*.

> **Note:** Technically, *let* and *const* variables declarations are being hoisted too, but not their assignation. Since they're made so that they can't be used before assignation, it intuitively feels like there is no hoisting, but there is. Find out more on this [very detailed explanation here](http://jsrocks.org/2015/01/temporal-dead-zone-tdz-demystified) if you want to know more.

In addition, you can't re-declare a *let* variable:

```js
let myVar = 2;
let myVar = 3; // Raises a SyntaxError
```

##### const

```const``` declared variables behave like *let* variables, but also they can't be reassigned.

To sum it up, *const* variables:

- are *block scoped*
- are not accessible before being assigned
- can't be re-declared in the same scope
- can't be reassigned

```js
const myVar = "Nick";
myVar = "John" // raises an error, reassignment is not allowed
```

```js
const myVar = "Nick";
const myVar = "John" // raises an error, re-declaration is not allowed
```

<a name="const_mutable_sample"></a> But there is a subtlety : ```const``` variables are not [**immutable**](#mutation_def) ! Concretely, it means that *object* and *array* ```const``` declared variables **can** be mutated.

For objects:
```js
const person = {
  name: 'Nick'
};
person.name = 'John' // this will work ! person variable is not completely reassigned, but mutated
console.log(person.name) // "John"
person = "Sandra" // raises an error, because reassignment is not allowed with const declared variables
```

For arrays:
```js
const person = [];
person.push('John'); // this will work ! person variable is not completely reassigned, but mutated
console.log(person[0]) // "John"
person = ["Nick"] // raises an error, because reassignment is not allowed with const declared variables
```


#### <a name="external-resource"></a> 外部資源

- [How let and const are scoped in JavaScript - WesBos](http://wesbos.com/javascript-scoping/)
- [Temporal Dead Zone (TDZ) Demystified](http://jsrocks.org/2015/01/temporal-dead-zone-tdz-demystified)

### <a name="-arrow-function"></a> 箭頭函式

The ES6 JavaScript update has introduced *arrow functions*, which is another way to declare and use functions. Here are the benefits they bring:

- More concise
- *this* is picked up from surroundings
- implicit return

#### <a name="sample-code-1"></a> 示例代碼

- Concision and implicit return

```js
function double(x) { return x * 2; } // Traditional way
console.log(double(2)) // 4
```

```js
const double = x => x * 2; // Same function written as an arrow function with implicit return
console.log(double(2)) // 4
```

- *this* reference

In an arrow function, *this* is equal to the *this* value of the enclosing execution context. Basically, with arrow functions, you don't have to do the "that = this" trick before calling a function inside a function anymore.

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

Arrow functions are more concise than traditional functions in many ways. Let's review all the possible cases:

- Implicit VS Explicit return

An **explicit return** is a function where the *return* keyword is used in its body.

```js
  function double(x) {
    return x * 2; // this function explicitly returns x * 2, *return* keyword is used
  }
```

In the traditional way of writing functions, the return was always explicit. But with arrow functions, you can do *implicit return* which means that you don't need to use the keyword *return* to return a value.

To do an implicit return, the code must be written in a one-line sentence.

```js
  const double = (x) => {
    return x * 2; // Explicit return here
  }
```

Since there only is a return value here, we can do an implicit return.

```js
  const double = (x) => x * 2;
```

To do so, we only need to **remove the brackets** and the **return** keyword. That's why it's called an *implicit* return, the *return* keyword is not there, but this function will indeed return ```x * 2```.

> **Note:** If your function does not return a value (with *side effects*), it doesn't do an explicit nor an implicit return.

Besides, if you want to implicitly return an *object* you **must have parenthesis around it** since it will conflict with the block braces:

```js
const getPerson = () => ({ name: "Nick", age: 24 })
console.log(getPerson()) // { name: "Nick", age: 24 } -- object implicitly returned by arrow function
```

- Only one argument

If your function only takes one parameter, you can omit the parenthesis around it. If we take back the above *double* code:

```js
  const double = (x) => x * 2; // this arrow function only takes one parameter
```

Parenthesis around the parameter can be avoided:

```js
  const double = x => x * 2; // this arrow function only takes one parameter
```

- No arguments

When there is no argument provided to an arrow function, you need to provide parentheses, or it won't be valid syntax.

```js
  () => { // parenthesis are provided, everything is fine
    const x = 2;
    return x;
  }
```

```js
  => { // No parenthesis, this won't work!
    const x = 2;
    return x;
  }
```

##### <a name="this-reference"></a> *this* 參考

To understand this subtlety introduced with arrow functions, you must know how [this](#this_def) behaves in JavaScript.

In an arrow function, *this* is equal to the *this* value of the enclosing execution context. What it means is that an arrow function doesn't create a new *this*, it grabs it from its surrounding instead.

Without arrow function, if you wanted to access a variable from *this* in a function inside a function, you had to use the *that = this* or *self = this* trick.

For instance, using setTimeout function inside myFunc:

```js
function myFunc() {
  this.myVar = 0;
  var that = this; // that = this trick
  setTimeout(
    function() { // A new *this* is created in this function scope
      that.myVar++;
      console.log(that.myVar) // 1

      console.log(this.myVar) // undefined -- see function declaration above
    },
    0
  );
}
```

But with arrow function, *this* is taken from its surrounding:

```js
function myFunc() {
  this.myVar = 0;
  setTimeout(
    () => { // this taken from surrounding, meaning myFunc here
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

Starting from ES2015 JavaScript update, you can set default value to your function parameters using the following syntax:

```js
function myFunc(x = 10) {
  return x;
}
console.log(myFunc()) // 10 -- no value is provided so x default value 10 is assigned to x in myFunc
console.log(myFunc(5)) // 5 -- a value is provided so x is equal to 5 in myFunc

console.log(myFunc(undefined)) // 10 -- undefined value is provided so default value is assigned to x
console.log(myFunc(null)) // null -- a value (null) is provided, see below for more details
```

The default parameter is applied in two and only two situations:

- No parameter provided
- *undefined* parameter provided

In other words, if you pass in *null* the default parameter **won't be applied**.

> **Note:** Default value assignment can be used with destructured parameters as well (see next notion to see an example)

#### <a name="external-resource-1"></a> 外部資源

- [Default parameter value - ES6 Features](http://es6-features.org/#DefaultParameterValues)
- [Default parameters - MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Default_parameters)

### <a name="destructuring-objects-and-arrays-12"></a> objects 和 arrays 的解構

*Destructuring* is a convenient way of creating new variables by extracting some values from data stored in objects or arrays.

To name a few use cases, *destructuring* can be used to destructure function parameters or *this.props* in React projects for instance.

#### <a name="explanation-with-sample-code-13"></a> 示例代碼說明

- Object

Let's consider the following object for all the samples:

```js
const person = {
  firstName: "Nick",
  lastName: "Anderson",
  age: 35,
  sex: "M"
}
```

Without destructuring

```js
const first = person.firstName;
const age = person.age;
const city = person.city || "Paris";
```

With destructuring, all in one line:

```js
const { firstName: first, age, city = "Paris" } = person; // That's it !

console.log(age) // 35 -- A new variable age is created and is equal to person.age
console.log(first) // "Nick" -- A new variable first is created and is equal to person.firstName
console.log(firstName) // Undefined -- person.firstName exists BUT the new variable created is named first
console.log(city) // "Paris" -- A new variable city is created and since person.city is undefined, city is equal to the default value provided "Paris".
```

**Note :** In ```const { age } = person;```, the brackets after *const* keyword are not used to declare an object nor a block but is the *destructuring* syntax.

- Function parameters

*Destructuring* is often used to destructure objects parameters in functions.

Without destructuring

```js
function joinFirstLastName(person) {
  const firstName = person.firstName;
  const lastName = person.lastName;
  return firstName + '-' + lastName;
}

joinFirstLastName(person); // "Nick-Anderson"
```

In destructuring the object parameter *person*, we get a more concise function:

```js
function joinFirstLastName({ firstName, lastName }) { // we create firstName and lastName variables by destructuring person parameter
  return firstName + '-' + lastName;
}

joinFirstLastName(person); // "Nick-Anderson"
```

Destructuring is even more pleasant to use with [arrow functions](#arrow_func_concept):

```js
const joinFirstLastName = ({ firstName, lastName }) => firstName + '-' + lastName;

joinFirstLastName(person); // "Nick-Anderson"
```

- Array

Lets consider the following array:

```js
const myArray = ["a", "b", "c"];
```

Without destructuring

```js
const x = myArray[0];
const y = myArray[1];
```

With destructuring

```js
const [x, y] = myArray; // That's it !

console.log(x) // "a"
console.log(y) // "b"
```

#### <a name="useful-resources-14"></a>有用資源

- [ES6 Features - Destructuring Assignment](http://es6-features.org/#ArrayMatching)
- [Destructuring Objects - WesBos](http://wesbos.com/destructuring-objects/)
- [ExploringJS - Destructuring](http://exploringjs.com/es6/ch_destructuring.html)

### <a name="array-methods---map--filter--reduce"></a> 陣列方法 - map / filter / reduce

*Map*, *filter* and *reduce* are array methods that are coming from a programming paradigm named [*functional programming*](https://medium.com/javascript-scene/master-the-javascript-interview-what-is-functional-programming-7f218c68b3a0).

To sum it up:

- **Array.prototype.map()** takes an array, does something on its elements and returns an array with the transformed elements.
- **Array.prototype.filter()** takes an array, decides element by element if it should keep it or not and returns an array with the kept elements only
- **Array.prototype.reduce()** takes an array and aggregates the elements into a single value (which is returned)

I recommend to use them as much as possible in following the principles of functional programming because they are composable, concise and elegant.

With those three methods, you can avoid the use of *for* and *forEach* loops in most situations. When you are tempted to do a *for* loop, try to do it with *map*, *filter* and *reduce* composed. You might struggle to do it at first because it requires you to learn a new way of thinking, but once you've got it things gets easier.

#### <a name="sample-code-2"></a> 示例代碼

```js
const numbers = [0, 1, 2, 3, 4, 5, 6];
const doubledNumbers = numbers.map(n => n * 2); // [0, 2, 4, 6, 8, 10, 12]
const evenNumbers = numbers.filter(n => n % 2 === 0); // [0, 2, 4, 6]
const sum = numbers.reduce((prev, next) => prev + next, 0); // 21
```

Compute total grade sum for students above 10 by composing map, filter and reduce:

```js
const students = [
  { name: "Nick", grade: 10 },
  { name: "John", grade: 15 },
  { name: "Julia", grade: 19 },
  { name: "Nathalie", grade: 9 },
];

const aboveTenSum = students
  .map(student => student.grade) // we map the students array to an array of their grades
  .filter(grade => grade >= 10) // we filter the grades array to keep those above 10
  .reduce((prev, next) => prev + next, 0); // we sum all the grades above 10 one by one

console.log(aboveTenSum) // 44 -- 10 (Nick) + 15 (John) + 19 (Julia), Nathalie below 10 is ignored
```


#### <a name="explanation-with-sample-code-0"></a> 示例代碼說明

Let's consider the following array of numbers for our examples:

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

What's happening here? We are using .map on the *numbers* array, the map is iterating on each element of the array and passes it to our function. The goal of the function is to produce and return a new value from the one passed so that map can replace it.

Lets extract this function to make it more clear, just for this once:

```js
const doubleN = function(n) { return n * 2; };
const doubledNumbers = numbers.map(doubleN);
console.log(doubledNumbers); // [0, 2, 4, 6, 8, 10, 12]
```

```numbers.map(doubleN)``` produces ```[doubleN(0), doubleN(1), doubleN(2), doubleN(3), doubleN(4), doubleN(5), doubleN(6)]``` which is equal to ```[0, 2, 4, 6, 8, 10, 12]```.

> **Note:** If you do not need to return a new array and just want to do a loop that has side effects, you might just want to use a for / forEach loop instead of a map.

##### <a name="arrayprototypefilter"></a> Array.prototype.filter()

```js
const evenNumbers = numbers.filter(function(n) {
  return n % 2 === 0; // true if "n" is par, false if "n" isn't
});
console.log(evenNumbers); // [0, 2, 4, 6]
```

We are using .filter on the *numbers* array, filter is iterating on each element of the array and passes it to our function. The goal of the function is to return a boolean that will determine whether the current value will be kept or not. Filter then returns the array with only the kept values.

##### <a name="arrayprototypereduce"></a> Array.prototype.reduce()

The reduce method goal is to *reduce* all elements of the array it iterates on into a single value. How it aggregates those elements is up to you.

```js
const sum = numbers.reduce(
  function(acc, n) {
    return acc + n;
  },
  0 // accumulator variable value at first iteration step
);

console.log(sum) //21
```

Just like for .map and .filter methods, .reduce is applied on an array and takes a function as the first parameter.

This time though, there are changes:

- .reduce takes two parameters

The first parameter is a function that will be called at each iteration step.

The second parameter is the value of the accumulator variable (*acc* here) at the first iteration step (read next point to understand).

- Function parameters

The function you pass as the first parameter of .reduce takes two parameters. The first one (*acc* here) is the accumulator variable, whereas the second parameter (*n*) is the current element.

The accumulator variable is equal to the return value of your function at the **previous** iteration step. At the first step of the iteration, *acc* is equal to the value you passed as .reduce second parameter.

###### At first iteration step

```acc = 0``` because we passed in 0 as the second parameter for reduce

```n = 0``` first element of the *number* array

Function returns *acc* + *n* --> 0 + 0 --> 0


###### At second iteration step

```acc = 0``` because its the value the function returned at the previous iteration step

```n = 1``` second element of the *number* array

Function returns *acc* + *n* --> 0 + 1 --> 1

###### At third iteration step

```acc = 1``` because its the value the function returned at the previous iteration step

```n = 2``` third element of the *number* array

Function returns *acc* + *n* --> 1 + 2 --> 3

###### At fourth iteration step

```acc = 3``` because it's the value the function returned at the previous iteration step

```n = 3``` fourth element of the *number* array

Function returns *acc* + *n* --> 3 + 3 --> 6

###### [...] At last iteration step

```acc = 15``` because it's the value the function returned at the previous iteration step

```n = 6``` last element of the *number* array

Function returns *acc* + *n* --> 15 + 6 --> 21

As it is the last iteration step, **.reduce** returns 21.

#### <a name="external-resource-2"></a> 外部資源 

- [Understanding map / filter / reduce in JS](https://hackernoon.com/understanding-map-filter-and-reduce-in-javascript-5df1c7eee464)

### <a name="spread-operator-"></a> 展開運算子 "..."

The spread operator ```...``` has been introduced with ES2015 and is used to expand elements of an iterable (like an array) into places where multiple elements can fit.

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

If we have the two following arrays:

```js
const arr1 = ["a", "b", "c"];
const arr2 = [arr1, "d", "e", "f"]; // [["a", "b", "c"], "d", "e", "f"]
```

*arr2* the first element is an array because *arr1* is injected as is into *arr2*. But what we want is *arr2* to be an array of letters. To do so, we can *spread* the elements of *arr1* into *arr2*.

With spread operator

```js
const arr1 = ["a", "b", "c"];
const arr2 = [...arr1, "d", "e", "f"]; // ["a", "b", "c", "d", "e", "f"]
```

##### <a name="function-rest-parameter"></a> 函式剩餘參數

In function parameters, we can use the rest operator to inject parameters into an array we can loop in. There is already an **argument** object bound to every function that is equal to an array of all the parameters passed into the function.

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

But let's say that we want this function to create a new student with its grades and with its average grade. Wouldn't it be more convenient to extract the first two parameters into two separate variables, and then have all the grades in an array we can iterate over?

That's exactly what the rest operator allows us to do!

```js
function createStudent(firstName, lastName, ...grades) {
  // firstName = "Nick"
  // lastName = "Anderson"
  // [10, 12, 6] -- "..." takes all other parameters passed and creates a "grades" array variable that contains them

  const avgGrade = grades.reduce((acc, curr) => acc + curr, 0) / grades.length; // computes average grade from grades

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

> **Note:** createStudent function is bad because we don't check if grades.length exists or is different from 0. But it's easier to read this way, so I didn't handle this case.


##### <a name="object-properties-spreading"></a> 物件屬性擴展

For this one, I recommend you read previous explanations about the rest operator on iterables and function parameters.

```js
const myObj = { x: 1, y: 2, a: 3, b: 4 };
const { x, y, ...z } = myObj; // object destructuring here
console.log(x); // 1
console.log(y); // 2
console.log(z); // { a: 3, b: 4 }

// z is the rest of the object destructured: myObj object minus x and y properties destructured

const n = { x, y, ...z };
console.log(n); // { x: 1, y: 2, a: 3, b: 4 }

// Here z object properties are spread into n
```

#### <a name="external-resources"></a> 外部資源

- [TC39 - Object rest/spread](https://github.com/tc39/proposal-object-rest-spread)
- [Spread operator introduction - WesBos](https://github.com/wesbos/es6-articles/blob/master/28%20-%20Spread%20Operator%20Introduction.md)
- [JavaScript & the spread operator](https://codeburst.io/javascript-the-spread-operator-a867a71668ca)
- [6 Great uses of the spread operator](https://davidwalsh.name/spread-operator)

### <a name="object-property-shorthand-29"></a> Object 屬性簡寫

When assigning a variable to an object property, if the variable name is equal to the property name, you can do the following:

```js
const x = 10;
const myObj = { x };
console.log(myObj.x) // 10
```

#### <a name="explanation-2"></a> 說明

Usually (pre-ES2015) when you declare a new *object literal* and want to use variables as object properties values, you would write this kind of code:

```js
const x = 10;
const y = 20;

const myObj = {
  x: x, // assigning x variable value to myObj.x
  y: y // assigning y variable value to myObj.y
};

console.log(myObj.x) // 10
console.log(myObj.y) // 20
```

As you can see, this is quite repetitive because the properties name of myObj are the same as the variable names you want to assign to those properties.

With ES2015, when the variable name is the same as the property name, you can do this shorthand:

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

A promise is an object which can be returned synchronously from an asynchronous function ([ref](https://medium.com/javascript-scene/master-the-javascript-interview-what-is-a-promise-27fc71e77261#3cd0)).

Promises can be used to avoid [callback hell](http://callbackhell.com/), and they are more and more frequently encountered in modern JavaScript projects.

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

When you do an *Ajax request* the response is not synchronous because you want a resource that takes some time to come. It even may never come if the resource you have requested is unavailable for some reason (404).

To handle that kind of situations, ES2015 has given us *promises*. Promises can have three different states:

- Pending
- Fulfilled
- Rejected

Let's say we want to use promises to handle an Ajax request to fetch the resource X.

##### <a name="create-the-promise"></a> 創建 promise

We firstly are going to create a promise. We will use the jQuery get method to do our Ajax request to X.

```js
const xFetcherPromise = new Promise( // Create promise using "new" keyword and store it into a variable
  function(resolve, reject) { // Promise constructor takes a function parameter which has resolve and reject parameters itself
    $.get("X") // Launch the Ajax request
      .done(function(X) { // Once the request is done...
        resolve(X); // ... resolve the promise with the X value as parameter
      })
      .fail(function(error) { // If the request has failed...
        reject(error); // ... reject the promise with the error as parameter
      });
  }
)
```

As seen in the above sample, the Promise object takes an *executor* function which takes two parameters **resolve** and **reject**. Those parameters are functions which when called are going to move the promise *pending* state to respectively a *fulfilled* and *rejected* state.

The promise is in pending state after instance creation and it's *executor* function is executed immediately. Once one of the function *resolve* or *reject* is called in the *executor* function, the promise will call its associated handlers.

##### <a name="promise-handlers-usage"></a> Promise 處理器運用

To get the promise result (or error), we must attach to it handlers by doing the following:

```js
xFetcherPromise
  .then(function(X) {
    console.log(X);
  })
  .catch(function(err) {
    console.log(err)
  })
```

If the promise succeeds, *resolve* is executed and the function passed as ```.then``` parameter is executed.

If it fails, *reject* is executed and the function passed as ```.catch``` parameter is executed.

> **Note :** If the promise has already been fulfilled or rejected when a corresponding handler is attached, the handler will be called, so there is no race condition between an asynchronous operation completing and its handlers being attached. [(Ref: MDN)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise#Description)

#### <a name="external-resources-32"></a> 外部資源

- [JavaScript Promises for dummies - Jecelyn Yeen](https://scotch.io/tutorials/javascript-promises-for-dummies)
- [JavaScript Promise API - David Walsh](https://davidwalsh.name/promises)
- [Using promises - MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Using_promises)
- [What is a promise - Eric Elliott](https://medium.com/javascript-scene/master-the-javascript-interview-what-is-a-promise-27fc71e77261)
- [JavaScript Promises: an Introduction - Jake Archibald](https://developers.google.com/web/fundamentals/getting-started/primers/promises)
- [Promise documentation - MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise)

### <a name="template-literals"></a> 模板字面量

Template literals is an [*expression interpolation*](https://en.wikipedia.org/wiki/String_interpolation) for single and multiple-line strings.

In other words, it is a new string syntax in which you can conveniently use any JavaScript expressions (variables for instance).

#### <a name="sample-code-5"></a> 示例代碼

```js
const name = "Nick";
`Hello ${name}, the following expression is equal to four : ${2+2}`;

// Hello Nick, the following expression is equal to four: 4
```

#### <a name="external-resources-2"></a> 外部資源

- [String interpolation - ES6 Features](http://es6-features.org/#StringInterpolation)
- [ES6 Template Strings - Addy Osmani](https://developers.google.com/web/updates/2015/01/ES6-Template-Strings)

### <a name="tagged-template-literals"></a> 標記模板字面量

Template tags are *functions that can be prefixed to a [template literal](#template-literals)*. When a function is called this way, the first parameter is an array of the *strings* that appear between the template's interpolated variables, and the subsequent paremeters are the interpolated values. Use a spread operator `...` to capture all of them. [(Ref: MDN)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Template_literals#Tagged_template_literals).

> **Note :** A famous library named [styled-components](https://www.styled-components.com/) heavily relies on this feature.

Below is a toy example on they work.
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

A more interesting example: 
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
// "I like apples, bananas, cherries to snack on."
```

#### <a name="external-resources-4"></a> 外部資源
- [Wes Bos on Tagged Template Literals](http://wesbos.com/tagged-template-literals/)
- [Library of common template tags](https://github.com/declandewet/common-tags)

### <a name="imports--exports"></a> Imports / Exports

ES6 modules are used to access variables or functions in a module explicitly exported by the modules it imports.

I highly recommend to take a look at MDN resources on import/export (see external resources below), it is both straightforward and complete.

#### <a name="explanation-with-sample-code-1"></a> 示例代碼說明

##### <a name="named-exports"></a> 命名 exports

Named exports are used to export several values from a module.

> **Note :** You can only name-export [first-class citizens](https://en.wikipedia.org/wiki/First-class_citizen) that have a name.

```js
// mathConstants.js
export const pi = 3.14;
export const exp = 2.7;
export const alpha = 0.35;

// -------------

// myFile.js
import { pi, exp } from './mathConstants.js'; // Named import -- destructuring-like syntax
console.log(pi) // 3.14
console.log(exp) // 2.7

// -------------

// mySecondFile.js
import * as constants from './mathConstants.js'; // Inject all exported values into constants variable
console.log(constants.pi) // 3.14
console.log(constants.exp) // 2.7
```

While named imports looks like *destructuring*, they have a different syntax and are not the same. They don't support default values nor *deep* destructuring.

Besides, you can do aliases but the syntax is different from the one used in destructuring:

```js
import { foo as bar } from 'myFile.js'; // foo is imported and injected into a new bar variable
```


##### <a name="default-import--export"></a> 預設 import / export

Concerning the default export, there is only a single default export per module. A default export can be a function, a class, an object or anything else. This value is considered the "main" exported value since it will be the simplest to import. [Ref: MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/export#Description)

```js
// coolNumber.js
const ultimateNumber = 42;
export default ultimateNumber;

// ------------

// myFile.js
import number from './coolNumber.js';
// Default export, independently from its name, is automatically injected into number variable;
console.log(number) // 42
```

Function exporting:

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

*this* operator behaves differently than in other languages and is in most cases determined by how a function is called. ([Ref: MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/this)).

This notion is having many subtleties and being quite hard, I highly suggest you to deep dive in the external resources below. Thus, I will provide what I personally have in mind to determine what *this* is equal to. I have learned this tip from [this article written by Yehuda Katz](http://yehudakatz.com/2011/08/11/understanding-javascript-function-invocation-and-this/).

```js
function myFunc() {
  ...
}

// After each statement, you find the value of *this* in myFunc

myFunc.call("myString", "hello") // "myString" -- first .call parameter value is injected into *this*

// In non-strict-mode
myFunc("hello") // window -- myFunc() is syntax sugar for myFunc.call(window, "hello")

// In strict-mode
myFunc("hello") // undefined -- myFunc() is syntax sugar for myFunc.call(undefined, "hello")
```

```js
var person = {
  myFunc: function() { ... }
}

person.myFunc.call(person, "test") // person Object -- first call parameter is injected into *this*
person.myFunc("test") // person Object -- person.myFunc() is syntax sugar for person.myFunc.call(person, "test")

var myBoundFunc = person.myFunc.bind("hello") // Creates a new function in which we inject "hello" in *this* value
person.myFunc("test") // person Object -- The bind method has no effect on the original method
myBoundFunc("test") // "hello" -- myBoundFunc is person.myFunc with "hello" bound to *this*
```

#### <a name="external-resources-42"></a> 外部資源

- [Understanding JavaScript Function Invocation and "this" - Yehuda Katz](http://yehudakatz.com/2011/08/11/understanding-javascript-function-invocation-and-this/)
- [JavaScript this - MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/this)

### <a name="class"></a> Class

JavaScript is a [prototype-based](https://en.wikipedia.org/wiki/Prototype-based_programming) language (whereas Java is [class-based](https://en.wikipedia.org/wiki/Class-based_programming) language, for instance). ES6 has introduced JavaScript classes which are meant to be a syntactic sugar for prototype-based inheritance and **not** a new class-based inheritance model ([ref](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes)).

The word *class* is indeed error prone if you are familiar with classes in other languages. If you do, avoid assuming how JavaScript classes work on this basis and consider it an entirely different notion.

Since this document is not an attempt to teach you the language from the ground up, I will believe you know what prototypes are and how they behave. But here are some links I found great to understand this notion:

- [Understanding Prototypes in JS - Yehuda Katz](http://yehudakatz.com/2011/08/12/understanding-prototypes-in-javascript/)
- [A plain English guide to JS prototypes - Sebastian Porto](http://sporto.github.io/blog/2013/02/22/a-plain-english-guide-to-javascript-prototypes/)
- [Inheritance and the prototype chain - MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Inheritance_and_the_prototype_chain)

#### <a name="samples-code-52"></a> 示例代碼

Before ES6, prototype syntax:

```js
var Person = function(name, age) {
  this.name = name;
  this.age = age;
}
Person.prototype.stringSentence = function() {
  return "Hello, my name is " + this.name + " and I'm " + this.age;
}
```

With ES6 class syntax:

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
```

#### <a name="external-resources-5"></a> 外部資源

For prototype understanding:

- [Understanding Prototypes in JS - Yehuda Katz](http://yehudakatz.com/2011/08/12/understanding-prototypes-in-javascript/)
- [A plain English guide to JS prototypes - Sebastian Porto](http://sporto.github.io/blog/2013/02/22/a-plain-english-guide-to-javascript-prototypes/)
- [Inheritance and the prototype chain - MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Inheritance_and_the_prototype_chain)

For classes understanding:

- [ES6 Classes in Depth - Nicolas Bevacqua](https://ponyfoo.com/articles/es6-classes-in-depth)
- [ES6 Features - Classes](http://es6-features.org/#ClassDefinition)
- [JavaScript Classes - MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes)

### <a name="async-await"></a> Async Await

In addition to [Promises](#promises), there is a new syntax you might encounter to handle asynchronous code named *async / await*.

The purpose of async/await functions is to simplify the behavior of using promises synchronously and to perform some behavior on a group of Promises. Just as Promises are similar to structured callbacks, async/await is similar to combining generators and promises. ([Ref: MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/async_function))

> **Note :** You must understand what are promises and how they work before trying to understand async / await since they rely on it.

> **Note 2:** [*await* must be used in an *async* function](https://hackernoon.com/6-reasons-why-javascripts-async-await-blows-promises-away-tutorial-c7ec10518dd9#f3f0), which means that you can't use await in the top level of our code since that is not inside an async function.

#### <a name="sample-code-6"></a> 示例代碼

```js
async function getGithubUser(username) { // async keyword allows usage of await in the function and means function returns a promise
  try { // this is how errors are handled with async / await
    const response = await fetch(`https://api.github.com/users/${username}`); // "synchronously" waiting fetch promise to resolve before going to next line
    return response.json();
  } catch (err) {
    alert(err);
  }
}

getGithubUser('mbeaudru').then(user => console.log(user)); // logging user response - cannot use await syntax since this code isn't in async function
```

#### <a name="explanation-with-sample-code-2"></a> 示例代碼說明

*Async / Await* is built on promises but they allow a more imperative style of code.

*async* operator turns a function into a *promise* in which you can use the *await* operator.

```js
async function myFunc() {
  // we can use await operator because this function is async
  try {
    return "hello world";
  } catch(e) {
    throw new Error();
  }
}

myFunc().then(msg => console.log(msg)) // "hello world" -- myFunc is turned into a promise because of async operator
```

When the *return* statement of an async function is reached, the promise is fulfilled with the value returned. If an error is thrown inside an async function, the promise state will turn to *rejected*.

*await* operator is used to wait for a *Promise* to be fulfilled and only can be used inside an *async* function body. When encountered, the code execution is paused until the promise is fulfilled.

> **Note :** *fetch* is a Promise that allows to do an AJAX request

Let's see how we could fetch a github user with promises first:

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

Here's the *async / await* equivalent:

```js
async function getGithubUser(username) { // promise + await keyword usage allowed
  try { // We handle async function errors with try / catch
    const response = await fetch(`https://api.github.com/users/${username}`); // Execution stops here until fetch promise is fulfilled.
    const user = response.json();
    return user; // equivalent of resolving the getGithubUser promise with user value.
  } catch (err) {
    throw new Error(err); // equivalent of rejecting getGithubUser promise with err value.
  }
}

getGithubUser('mbeaudru')
  .then(user => console.log(user))
  .catch(err => console.log(err));
```

*async / await* syntax is particularly convenient when you need to chain promises that are interdependent.

For instance, if you need to get a token in order to be able to fetch a blog post on a database and then the author informations:

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

> **Note :** As you can see, *try / catch* are necessary to handle errors. But if you are making *express routes*, you can use a middleware to avoid error handling and have a very pleasant code to read. See [this article from Alex Bazhenov](https://medium.com/@Abazhenov/using-async-await-in-express-with-node-8-b8af872c0016) to learn more.

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

In JavaScript, a truthy or falsy value is a value that is being casted into a boolean when evaluated in a boolean context. An example of boolean context would be the evaluation of an ```if``` condition:

Every value will be casted to ```true``` unless they are equal to:

- false
- 0
- "" (empty string)
- null
- undefined
- NaN

Here are examples of *boolean context*:

- ```if``` condition evaluation

```js
if (myVar) {}
```

```myVar``` can be any [first-class citizen](https://en.wikipedia.org/wiki/First-class_citizen) (variable, function, boolean) but it will be casted into a boolean because it's evaluated in a boolean context.

- After logical **NOT** ```!``` operator

This operator returns false if its single operand can be converted to true; otherwise, returns true.

```js
!0 // true -- 0 is falsy so it returns true
!!0 // false -- 0 is falsy so !0 returns true so !(!0) returns false
!!"" // false -- empty string is falsy so NOT (NOT false) equals false
```

- With the *Boolean* object constructor

```js
new Boolean(0) // false
new Boolean(1) // true
```

- In a ternary evaluation

```js
myVar ? "truthy" : "falsy"
```

myVar is evaluated in a boolean context.


## <a name="glossary"></a> 詞彙表

### <a name="-scope"></a> 範圍

The context in which values and expressions are "visible," or can be referenced. If a variable or other expression is not "in the current scope," then it is unavailable for use.

Source: [MDN](https://developer.mozilla.org/en-US/docs/Glossary/Scope)

### <a name="-variable-mutation"></a> 變數變化

A variable is said to have been mutated when its initial value has changed afterward.

```js
var myArray = [];
myArray.push("firstEl") // myArray is being mutated
```

A variable is said to be *immutable* if it can't be mutated.

[Check MDN Mutable article](https://developer.mozilla.org/en-US/docs/Glossary/Mutable) for more details.
