# JavaScript Tips And Tricks
A collection of JavaScript tips and tricks.

No particular order or path.

I add things as I discover them. 

*Check [Codinghub.tips](https://codinghub.tips/), too, for JavaScript tips. It's not my project but I like it.* 🔥

# TABLE OF CONTENTS
- [JavaScript Tips And Tricks](#javascript-tips-and-tricks)
- [TABLE OF CONTENTS](#table-of-contents)
- [OPTIONAL CHAINING](#optional-chaining)
- [NULLISH COALESCING OPERATOR](#nullish-coalescing-operator)
- [MERGE OBJECTS TOGETHER - SPREAD OPERATOR](#merge-objects-together---spread-operator)
- [TWO WAYS TO CONVERT A STRING TO A CHARACTER ARRAY](#two-ways-to-convert-a-string-to-a-character-array)

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

# TWO WAYS TO CONVERT A STRING TO A CHARACTER ARRAY 

These are two quick ways to convert your string to an array of characters.

```
const firstName = "Catalin";

const firstNameArr1 = firstName.split('');
console.log(firstNameArr1);

const firstNameArr2 = [...firstName];
console.log(firstNameArr2);
```