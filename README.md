# JS Tips And Tricks
A collection of JavaScript tips and tricks.

No particular order or path.

I add things as I discover them. 

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