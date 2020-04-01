# JavaScript Tips And Tricks 🔥🚀⚡

A collection of JavaScript tips and tricks.

No particular order or path.

I add things as I discover them.

_Check [Codinghub.tips](https://codinghub.tips/), too, for JavaScript tips. It's not my project but I like it._ 🔥

# TABLE OF CONTENTS

- [JavaScript Tips And Tricks 🔥🚀⚡](#javascript-tips-and-tricks-%f0%9f%94%a5%f0%9f%9a%80%e2%9a%a1)
- [TABLE OF CONTENTS](#table-of-contents)
- [OPTIONAL CHAINING](#optional-chaining)
- [NULLISH COALESCING OPERATOR](#nullish-coalescing-operator)
- [MERGE OBJECTS TOGETHER - SPREAD OPERATOR](#merge-objects-together---spread-operator)
- [TWO WAYS TO CONVERT A STRING TO A CHARACTER ARRAY](#two-ways-to-convert-a-string-to-a-character-array)
- [DEFAULT PARAMETERS](#default-parameters)
- [FILTER UNIQUE VALUES / REMOVE DUPLICATE VALUES](#filter-unique-values--remove-duplicate-values)
- [FILTER OUT FALSY VALUES](#filter-out-falsy-values)
- [REQUIRED PARAMETERS](#required-parameters)
- [PASS AN EMPTY PARAMETER](#pass-an-empty-parameter)
- [REMOVE A PROPERTY FROM OBJECT](#remove-a-property-from-object)

# OPTIONAL CHAINING

"Shorter and simpler expressions when accessing chained properties when the possibility exists that a reference may be missing." (Source: [MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Optional_chaining))

```js
const person = {
  name: 'Catalin Pit',
  socialMedia: {
    twitter: '@catalinmpit',
    instagram: '@catalinmpit',
    linkedin: '@catalinmpit'
  },
  experience: 'Junior',
  employed: true
};

if (person && person.socialMedia && person.socialMedia.twitter) {
  console.log(person.socialMedia.twitter);
}

// The same thing with optional chaining
if (person?.socialMedia?.twitter) {
  console.log(person.socialMedia.twitter); // outputs @catalinmpit
}

// or
console.log(person?.socialMedia?.twitter);
```

# NULLISH COALESCING OPERATOR

"The nullish coalescing operator (??) is a logical operator that returns its right-hand side operand when its left-hand side operand is null or undefined, and otherwise returns its left-hand side operand." (Source: [MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Nullish_coalescing_operator))

```js
const person = {
  name: 'Catalin Pit',
  socialMedia: {
    twitter: '@catalinmpit',
    instagram: '@catalinmpit',
    linkedin: '@catalinmpit'
  },
  experience: 'Junior',
  employed: true
};

console.log(person.socialMedia.facebook ?? 'No Facebook account found!'); // Outputs 'No Facebook account found!'
console.log(person.socialMedia.instagram ?? 'No Instagram account found!'); // Outputs '@catalinmpit'

/// Another example ///
let name;

console.log(name ?? 'No name assigned'); // Outputs 'No name assigned'

let name = 'Catalin Pit';

console.log(name ?? 'No name assigned'); // Outputs 'Catalin Pit'
```

# MERGE OBJECTS TOGETHER - SPREAD OPERATOR

"Shallow-cloning (excluding prototype) or merging of objects is now possible using a shorter syntax than Object.assign()." (Source: [MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Spread_syntax))

```js
const user = {
  name: 'Catalin Pit',
  role: 'Junior Fullstack Developer',
  age: 23
};

const uses = {
  machine: 'MacBook Pro 15 inch',
  editor: 'VS Code',
  language: 'JavaScript',
  phone: 'Samsung Note 10'
};

const summary = { ...user, ...uses };

console.log(summary);

// Outputs //
const summary = {
  name: 'Catalin Pit',
  role: 'Junior Fullstack Developer',
  age: 23,
  machine: 'MacBook Pro 15 inch',
  editor: 'VS Code',
  language: 'JavaScript',
  phone: 'Samsung Note 10'
};
```

# TWO WAYS TO CONVERT A STRING TO A CHARACTER ARRAY

These are two quick ways to convert your string to an array of characters.

```js
const firstName = 'Catalin';

const firstNameArr1 = firstName.split('');
console.log(firstNameArr1);

const firstNameArr2 = [...firstName];
console.log(firstNameArr2);
```

# DEFAULT PARAMETERS

"Default function parameters allow named parameters to be initialized with default values if no value or undefined is passed." (Source: [MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Default_parameters))

```js
function add(x = 1, y = 2) {
  return x + y;
}

add(); // Returns 3
add(10); // Returns 12
add(5, 5); // Returns 10
```

# FILTER UNIQUE VALUES / REMOVE DUPLICATE VALUES

"Set objects are collections of values. You can iterate through the elements of a set in insertion order. A value in the Set may only occur once; it is unique in the Set's collection." (Source: [MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Set))

```js
// Strings
const names = [
  'Catalin',
  'Catalin',
  'Pit',
  'Pit',
  'Tom',
  'Tom',
  'John',
  'John'
];
const uniqueNames = [...new Set(names)];

console.log(uniqueNames); // Outputs ['Catalin', 'Pit', 'Tom', 'John']

// Numbers
const examScores = [
  50,
  75,
  100,
  99,
  95,
  67,
  43,
  43,
  43,
  100,
  99,
  50,
  50,
  50,
  50
];
const uniqueExamScores = [...new Set(examScores)];

console.log(uniqueExamScores); // Outputs [50, 75, 100, 99, 95, 67, 43];
```

# FILTER OUT FALSY VALUES

Remove falsy values such as `null, undefined, 0, boolean` and so on, from an array.

```js
const myArray = [
  'Catalin',
  1,
  'Macbook',
  false,
  true,
  'Car',
  'Peace',
  191,
  false
];

const filteredArray = myArray.filter(Boolean);

console.log(filteredArray); // Returns ["Catalin", 1, "Macbook", true, "Car", "Peace", 191]
```

# REQUIRED PARAMETERS

Default parameters allows us to require an argument to be passed to the function.

We can create a function which throws an error and assign it as default value for required parameters.

```js
const required = () => {
  throw new TypeError('You did not pass the required argument!');
};

const greet = (name = required()) => console.log(`Hello ${name}!`);

greet(); // Returns "Uncaught TypeError: You did not pass the required argument!"
greet('Catalin Pit'); // Returns "Hello Catalin Pit!"
```

# PASS AN EMPTY PARAMETER

With the help of the spread syntax, we can now pass an empty parameter to a function.

"Spread syntax allows an iterable such as an array expression or string to be expanded in places where zero or more arguments (for function calls) or elements (for array literals) are expected, or an object expression to be expanded in places where zero or more key-value pairs (for object literals) are expected." (Source: [MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Spread_syntax))

```js
function greet(fullName, instagramHandle, twitterHandle) {
  let message = `Hello, my name is ${fullName}.`;

  if (instagramHandle) {
    message += ` My Instagram handle is ${instagramHandle}.`;
  }

  if (twitterHandle) {
    message += ` My Twitter handle is ${twitterHandle}.`;
  }

  return message;
}

// Returns "Hello, my name is Catalin Pit."
console.log(greet('Catalin Pit'));

// Returns "Hello, my name is Catalin Pit. My Instagram handle is @cpit. My Twitter handle is @catapit."
console.log(greet('Catalin Pit', '@cpit', '@catapit'));

// Returns "Hello, my name is Catalin Pit. My Twitter handle is @cpit."
greet(...['Catalin Pit', , '@cpit']);

// Returns "Hello, my name is Catalin Pit. My Instagram handle is @catapit."
greet(...['Catalin Pit', '@catapit']);
```

# REMOVE A PROPERTY FROM OBJECT

With the help of reduce, we can remove an unwanted property from an object.

"The reduce() method executes a reducer function (that you provide) on each element of the array, resulting in a single output value."(Source: [MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/reduce))

```js
//Remove selected keys from an object
const params = {
  data: 'random text',
  pickup: 'tokyo',
  delivery: 'delhi',
  book: 'anything you want derek sivers'
};
const unwantedKeys = ['data', 'book'];
const newParams = Object.keys(params).reduce((obj, key) => {
  if (!unwantedKeys.includes(key)) obj[key] = params[key];
  return obj;
}, {});

console.log(newParams); // { pickup: 'tokyo', delivery: 'delhi' }

//Remove falsy values from an object
const params = {
  data: undefined,
  pickup: 'tokyo',
  delivery: 'delhi',
  price: null
};
const newParams = Object.keys(params).reduce((obj, key) => {
  if (params[key]) obj[key] = params[key];
  return obj;
}, {});

console.log(newParams); // { pickup: 'tokyo', delivery: 'delhi' }
```
