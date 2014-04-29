# Comparators

Lets now focus on the conditional part:

```javascript
if (country === "France") {
    ...
}
```

The conditional part is the variable `country` followed by the three equal signs (`===`). Three equal signs tests if the variable `country` has both the correct value (`France`) and also the correct type (`String`). You can test conditions with double equal signs, too, however a conditional such as `if (x == 5)` would then return true for both `var x = 5;` and `var x = "5";`. Depending on what your program is doing, this could make quite a difference.  It is highly recommended as a best practice that you always compare equality with three equal signs (`===` and `!==`) instead of two (`==` and `!=`).

Other conditional test:

* ```x > a```: is x bigger than a?
* ```x < a```: is x less than a?
* ```x <= a```: is x less than or equal to a?
* ```x != a```: is x not a?
* ```x```: does x exist?


---

Add a condition to change the value of `a` to the number 10 if `x` is bigger than 5.

```js
var x = 6;
var a = 0;


```

```js
var x = 6;
var a = 0;

if (x > 5) {
    a = 10;
}
```

```js
assert(a === 10);
```

---
