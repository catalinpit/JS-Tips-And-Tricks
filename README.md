# JS Tips And Tricks
A collection of JavaScript tips and tricks.

No particular order or path.

I add things as I discover them. 

# TABLE OF CONTENTS
* [Optional Chaining](#optional-chaining)
* [Nullish Coalescing Operator](#nullish-coalescing-operator)
* [Merge Objects Together - Spread Operator](#merge-objects-together---spread-operator)

# OPTIONAL CHAINING

"Shorter and simpler expressions when accessing chained properties when the possibility exists that a reference may be missing." (Source: [MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Optional_chaining))

```
const person = {
  name: "Catalin Pit",
  socialMedia: {
    twitter: "@catalinmpit",
    instagram: "@catalinmpit",
    linkedin: "@catalinmpit",
  },
  experience: "Junior",
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

```
const person = {
  name: "Catalin Pit",
  socialMedia: {
    twitter: "@catalinmpit",
    instagram: "@catalinmpit",
    linkedin: "@catalinmpit",
  },
  experience: "Junior",
  employed: true
};

console.log(person.socialMedia.facebook ?? 'No Facebook account found!'); // Outputs 'No Facebook account found!'
console.log(person.socialMedia.instagram ?? person.socialMedia.instagram); // Outputs '@catalinmpit'


/// Another example ///
let name;

console.log(name ?? 'No name assigned'); // Outputs 'No name assigned'

let name = 'Catalin Pit';

console.log(name ?? 'No name assigned'); // Outputs 'Catalin Pit'
```

# MERGE OBJECTS TOGETHER - SPREAD OPERATOR

"Shallow-cloning (excluding prototype) or merging of objects is now possible using a shorter syntax than Object.assign()." (Source: [MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Spread_syntax))

```
const user = {
  name: "Catalin Pit",
  role: "Junior Fullstack Developer",
  age: 23
};

const uses = {
  machine: "MacBook Pro 15 inch",
  editor: "VS Code",
  language: "JavaScript",
  phone: "Samsung Note 10"
};

const summary = {...user, ...uses};

console.log(summary); 

// Outputs //
const summary = {
  name: "Catalin Pit",
  role: "Junior Fullstack Developer",
  age: 23,
  machine: "MacBook Pro 15 inch",
  editor: "VS Code",
  language: "JavaScript",
  phone: "Samsung Note 10"
}
```