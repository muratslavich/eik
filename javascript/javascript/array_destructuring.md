# array\_destructuring

## array destructuring

[https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Destructuring\_assignment#array\_destructuring](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Destructuring\_assignment#array\_destructuring)

```
```

## Destructuring assignment

The **destructuring assignment**syntax is a JavaScript expression that makes it possible to unpack values from arrays, or properties from objects, into distinct variables.

### [Syntax](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Destructuring\_assignment#syntax)

```
let a, b, rest;
[a, b] = [10, 20];
console.log(a); // 10
console.log(b); // 20

[a, b, ...rest] = [10, 20, 30, 40, 50];
console.log(a); // 10
console.log(b); // 20
console.log(rest); // [30, 40, 50]

({ a, b } = { a: 10, b: 20 });
console.log(a); // 10
console.log(b); // 20

// Stage 4(finished) proposal
({a, b, ...rest} = {a: 10, b: 20, c: 30, d: 40});
console.log(a); // 10
console.log(b); // 20
console.log(rest); // {c: 30, d: 40}
```

Copy to Clipboard

### [Description](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Destructuring\_assignment#description)

The object and array literal expressions provide an easy way to create \_ad hoc\_packages of data.

```
const x = [1, 2, 3, 4, 5];
```

Copy to Clipboard

The destructuring assignment uses similar syntax, but on the left-hand side of the assignment to define what values to unpack from the sourced variable.

```
const x = [1, 2, 3, 4, 5];
const [y, z] = x;
console.log(y); // 1
console.log(z); // 2
```

Copy to Clipboard

Similarly, you can destructure arrays on the left-hand side of the assignment

```
const [firstElement, secondElement] = list;
// is equivalent to:
// const firstElement = list[0];
// const secondElement = list[1];
```

Copy to Clipboard

This capability is similar to features present in languages such as Perl and Python.

### [Examples](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Destructuring\_assignment#examples)

#### [Array destructuring](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Destructuring\_assignment#array\_destructuring)

**Basic variable assignment**

```
const foo = ['one', 'two', 'three'];

const [red, yellow, green] = foo;
console.log(red); // "one"
console.log(yellow); // "two"
console.log(green); // "three"
```

Copy to Clipboard

**Assignment separate from declaration**

A variable can be assigned its value via destructuring, separate from the variable's declaration.

```
let a, b;

[a, b] = [1, 2];
console.log(a); // 1
console.log(b); // 2
```

Copy to Clipboard

In an array destructuring from an array of length \_N\_specified on the right-hand side of the assignment, if the number of variables specified on the left-hand side of the assignment is greater than _N_, only the first \_N\_variables are assigned values. The values of the remaining variables will be undefined.

```
const foo = ['one', 'two'];

const [red, yellow, green, blue] = foo;
console.log(red); // "one"
console.log(yellow); // "two"
console.log(green); // undefined
console.log(blue);  //undefined
```

Copy to Clipboard

**Default values**

A variable can be assigned a default, in the case that the value unpacked from the array is undefined.

```
let a, b;

[a=5, b=7] = [1];
console.log(a); // 1
console.log(b); // 7
```

Copy to Clipboard

**Swapping variables**

Two variables values can be swapped in one destructuring expression.

Without destructuring assignment, swapping two values requires a temporary variable (or, in some low-level languages, the [XOR-swap trick](https://en.wikipedia.org/wiki/XOR\_swap\_algorithm)).

```
let a = 1;
let b = 3;

[a, b] = [b, a];
console.log(a); // 3
console.log(b); // 1

const arr = [1,2,3];
[arr[2], arr[1]] = [arr[1], arr[2]];
console.log(arr); // [1,3,2]
```

Copy to Clipboard

**Parsing an array returned from a function**

It's always been possible to return an array from a function. Destructuring can make working with an array return value more concise.

In this example, f()returns the values \[1, 2]as its output, which can be parsed in a single line with destructuring.

```
function f() {
  return [1, 2];
}

let a, b;
[a, b] = f();
console.log(a); // 1
console.log(b); // 2
```

Copy to Clipboard

**Ignoring some returned values**

You can ignore return values that you're not interested in:

```
function f() {
  return [1, 2, 3];
}

const [a, , b] = f();
console.log(a); // 1
console.log(b); // 3

const [c] = f();
console.log(c); // 1
```

Copy to Clipboard

You can also ignore all returned values:

```
[,,] = f();
```

Copy to Clipboard

**Assigning the rest of an array to a variable**

When destructuring an array, you can unpack and assign the remaining part of it to a variable using the rest pattern:

```
const [a, ...b] = [1, 2, 3];
console.log(a); // 1
console.log(b); // [2, 3]
```

Copy to Clipboard

Be aware that a [SyntaxError](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global\_Objects/SyntaxError)will be thrown if a trailing comma is used on the right-hand side of a rest element:

```
const [a, ...b,] = [1, 2, 3];

// SyntaxError: rest element may not have a trailing comma
// Always consider using rest operator as the last element
```

Copy to Clipboard

**Unpacking values from a regular expression match**

When the regular expression [exec()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global\_Objects/RegExp/exec)method finds a match, it returns an array containing first the entire matched portion of the string and then the portions of the string that matched each parenthesized group in the regular expression. Destructuring assignment allows you to unpack the parts out of this array easily, ignoring the full match if it is not needed.

```
function parseProtocol(url) {
  const parsedURL = /^(\w+)\:\/\/([^\/]+)\/(.*)$/.exec(url);
  if (!parsedURL) {
    return false;
  }
  console.log(parsedURL);
  // ["https://developer.mozilla.org/en-US/docs/Web/JavaScript", 
  // "https", "developer.mozilla.org", "en-US/docs/Web/JavaScript"]

  const [, protocol, fullhost, fullpath] = parsedURL;
  return protocol;
}

console.log(parseProtocol('https://developer.mozilla.org/en-US/docs/Web/JavaScript'));
// "https"
```

Copy to Clipboard

#### [Object destructuring](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Destructuring\_assignment#object\_destructuring)

**Basic assignment**

```
const user = {
    id: 42,
    isVerified: true
};

const {id, isVerified} = user;

console.log(id); // 42
console.log(isVerified); // true
```

Copy to Clipboard

**Assignment separate from declaration**

A variable can be assigned its value with destructuring separate from its declaration.

```
let a, b;

({a, b} = {a: 1, b: 2});
```

Copy to Clipboard

\*\*Note:\*\*The parentheses ( ... )around the assignment statement are required when using object literal destructuring assignment without a declaration.

{a, b} = {a: 1, b: 2}is not valid stand-alone syntax, as the {a, b}on the left-hand side is considered a block and not an object literal.

However, ({a, b} = {a: 1, b: 2})is valid, as is const {a, b} = {a: 1, b: 2}

Your ( ... )expression needs to be preceded by a semicolon or it may be used to execute a function on the previous line.

**Assigning to new variable names**

A property can be unpacked from an object and assigned to a variable with a different name than the object property.

```
const o = {p: 42, q: true};
const {p: foo, q: bar} = o;

console.log(foo); // 42
console.log(bar); // true
```

Copy to Clipboard

Here, for example, const {p: foo} = otakes from the object othe property named pand assigns it to a local variable named foo.

**Default values**

A variable can be assigned a default, in the case that the value unpacked from the object is undefined.

```
const {a = 10, b = 5} = {a: 3};

console.log(a); // 3
console.log(b); // 5
```

Copy to Clipboard

**Assigning to new variables names and providing default values**

A property can be both

* Unpacked from an object and assigned to a variable with a different name.
* Assigned a default value in case the unpacked value is undefined.

```
const {a: aa = 10, b: bb = 5} = {a: 3};

console.log(aa); // 3
console.log(bb); // 5
```

Copy to Clipboard

**Unpacking fields from objects passed as a function parameter**

```
const user = {
  id: 42,
  displayName: 'jdoe',
  fullName: {
    firstName: 'John',
    lastName: 'Doe'
  }
};

function userId({id}) {
  return id;
}

function whois({displayName, fullName: {firstName: name}}) {
  return `${displayName} is ${name}`;
}

console.log(userId(user)); // 42
console.log(whois(user));  // "jdoe is John"
```

Copy to Clipboard

This unpacks the id, displayNameand firstNamefrom the user object and prints them.

**Setting a function parameter's default value**

```
function drawChart({size = 'big', coords = {x: 0, y: 0}, radius = 25} = {}) {
  console.log(size, coords, radius);
  // do some chart drawing
}

drawChart({
  coords: {x: 18, y: 30},
  radius: 30
});
```

Copy to Clipboard

\*\*Note:\*\*In the function signature for **drawChart**above, the destructured left-hand side is assigned to an empty object literal on the right-hand side:

```
{size = 'big', coords = {x: 0, y: 0}, radius = 25} = {}
```

Copy to Clipboard

You could have also written the function without the right-hand side assignment. However, if you leave out the right-hand side assignment, the function will look for at least one argument to be supplied when invoked, whereas in its current form, you can call \*\*drawChart()\*\*without supplying any parameters. The current design is useful if you want to be able to call the function without supplying any parameters. The other can be useful when you want to ensure an object is passed to the function.

**Nested object and array destructuring**

```
const metadata = {
  title: 'Scratchpad',
  translations: [
    {
      locale: 'de',
      localization_tags: [],
      last_edit: '2014-04-14T08:43:37',
      url: '/de/docs/Tools/Scratchpad',
      title: 'JavaScript-Umgebung'
    }
  ],
  url: '/en-US/docs/Tools/Scratchpad'
};

let {
  title: englishTitle, // rename
  translations: [
    {
       title: localeTitle, // rename
    },
  ],
} = metadata;

console.log(englishTitle); // "Scratchpad"
console.log(localeTitle);  // "JavaScript-Umgebung"
```

Copy to Clipboard

**For of iteration and destructuring**

```
const people = [
  {
    name: 'Mike Smith',
    family: {
      mother: 'Jane Smith',
      father: 'Harry Smith',
      sister: 'Samantha Smith'
    },
    age: 35
  },
  {
    name: 'Tom Jones',
    family: {
      mother: 'Norah Jones',
      father: 'Richard Jones',
      brother: 'Howard Jones'
    },
    age: 25
  }
];

for (const {name: n, family: {father: f}} of people) {
  console.log('Name: ' + n + ', Father: ' + f);
}

// "Name: Mike Smith, Father: Harry Smith"
// "Name: Tom Jones, Father: Richard Jones"
```

Copy to Clipboard

**Computed object property names and destructuring**

Computed property names, like on [object literals](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Object\_initializer#computed\_property\_names), can be used with destructuring.

```
let key = 'z';
let {[key]: foo} = {z: 'bar'};

console.log(foo); // "bar"
```

Copy to Clipboard

**Rest in Object Destructuring**

The [Rest/Spread Properties for ECMAScript](https://github.com/tc39/proposal-object-rest-spread)proposal (stage 4) adds the [rest](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/rest\_parameters)syntax to destructuring. Rest properties collect the remaining own enumerable property keys that are not already picked off by the destructuring pattern.

```
let {a, b, ...rest} = {a: 10, b: 20, c: 30, d: 40}
a; // 10
b; // 20
rest; // { c: 30, d: 40 }
```

Copy to Clipboard

**Invalid JavaScript identifier as a property name**

Destructuring can be used with property names that are not valid JavaScript [identifiers](https://developer.mozilla.org/en-US/docs/Glossary/Identifier)by providing an alternative identifier that is valid.

```
const foo = { 'fizz-buzz': true };
const { 'fizz-buzz': fizzBuzz } = foo;

console.log(fizzBuzz); // true
```

Copy to Clipboard

**Combined Array and Object Destructuring**

Array and Object destructuring can be combined. Say you want the third element in the array propsbelow, and then you want the nameproperty in the object, you can do the following:

```
const props = [
  { id: 1, name: 'Fizz'},
  { id: 2, name: 'Buzz'},
  { id: 3, name: 'FizzBuzz'}
];

const [,, { name }] = props;

console.log(name); // "FizzBuzz"
```

Copy to Clipboard

**The prototype chain is looked up when the object is deconstructed**

When deconstructing an object, if a property is not accessed in itself, it will continue to look up along the prototype chain.

```
let obj = {self: '123'};
obj.__proto__.prot = '456';
const {self, prot} = obj;
// self "123"
// prot "456" (Access to the prototype chain)
```
