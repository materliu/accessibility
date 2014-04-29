# For Loop

The easiest form of a loop is the for statement. This one has a syntax that is similar to an if statement, but with more options:

```javascript
for(condition; end condition; change){
    // do it, do it now
}
```

Lets for example see how to execute the same code ten-times using a `for` loop:

```
for(var i = 0; i < 10; i = i + 1){
    // do this code ten-times
}
```

>***Note***: `i = i + 1` can be written `i++`.


---

Using a for-loop, create a variable named `message` that equals the concatenation of integers (0, 1, 2, ...) from 0 to 99.

```js
var message = "";
```

```js
var message = "";

for(var i = 0; i < 100; i++){
    message = message + i;
}
```

```js
var message2 = ""

for(var i = 0; i < 100; i++){
    message2 = message2 + i;
}
assert(message === message2);
```

---
