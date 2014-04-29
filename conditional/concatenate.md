# Concatenate conditions

Furthermore you can concatenate different conditions with "or” or “and” statements, to test whether either statement is true, or both are true, respectively.

In JavaScript “or” is written as `||` and “and” is written as `&&`.

Say you want to test if the value of x is between 10 and 20—you could do that with a condition stating:

```
if(x > 10 && x < 20) {
    ...
}
```

If you want to make sure that country is either “England” or “Germany” you use:

```
if(country === 'England' || country === 'Germany') {
    ...
}
```

**Note**: Just like operations on numbers, Condtions can be grouped using parenthesis, ex: ```if ( (name === "John" || name === "Jennifer") && country === "France")```.

---

Fill up the 2 conditions so that `primaryCategory` equals `"E/J"` only if name equals `"John"` and country is `"England"`, and so that `secondaryCategory` equals `"E|J"` only if name equals `"John"` or country is `"England"`

```js
var name = "John";
var country = "England";
var primaryCategory, secondaryCategory;

if ( /* Fill here */ ) {
    primaryCategory = "E/J";
}
if ( /* Fill here */ ) {
    secondaryCategory = "E|J";
}
```

```js
var name = "John";
var country = "England";
var primaryCategory, secondaryCategory;

if (name === "John" && country === "England") {
    primaryCategory = "E/J";
}
if (name === "John" || country === "England") {
    secondaryCategory = "E|J";
}
```

```js
assert(primaryCategory === "E/J" && secondaryCategory === "E|J");
```

---
