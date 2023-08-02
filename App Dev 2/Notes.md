# Application Development 2

This is a compilation of things that i have learnt that I will be using in the project.

# Index

- [JavaScript](#javascript)
- [Vue](#vue)
- [Redis and SQLite](#redis-and-sqlite)
- [Flask](#flask)

---

Please let me know if you need more specific information about any of these topics!
Feel free to copy the entire index or specific sections as needed. Let me know if there's anything else I can assist you with!

## JavaScript

```javascript
var x1 = 10
{
    console.log(x1);
    var x2 = 30;
}
```

That is a block not a function. It is a change in scope type thing.

`let` is scope specific, `var` is not. Better to use `let`.

Strings can be treated as arrays like in python. JS will attempt to coerce variables into any type it can to avoid errors.

Use `===` wherever you can.

##### Templates/ jQuery

```javascript
let s = "Hello"
console.log(`${s} world`)
```

This is like `f'{}'` in python. 

If, else, for, while, break, continue, yield, switch is like C/Java. However we can also make it *pythonic*

```javascript
const v = [1,2,3,4]
for (const x in v) {
    console.log(v[x])
}
```

**WARNING**: This is not purely pythonic. const x gets index of values in v **not** the value of v.

```javascript
const v = [1,2,3,4]
for (const x of v) {
    console.log(x)
}
```

This will actually return the values of v. This is pythonic. `in` and `of` skips any `undefined` values.

---

##### Functions

```javascript
//3 types of declaration
function add(x,y) {
    return x+y;
}

let add = fucntion(x,y) {
    return x+y;
}

let add = (x,y) => x+y;

//This creates an anonymous functiona nd immediatly calls it.
(function (x,y) {return x+y} (2,3))
```

These are all functionally the same.

---

##### DOM Stuff

`document.getElementById('<ID HERE>')` This gets the thing from DOM and makes it into an object.

`x.addEventListener('click',<func here>)`

---

##### Arrays

Mian thing to remember in JS is the all arrays are Objects. Arrays are like in python. Do whatever u want lmao.

**Functions**: `list.keys(), list.entries()`.

map, filter, find are also here `:(` . We can dynamically change the size of an array by `a.length = <some other value>`

We can have what are basically dicts as an object like so:

```javascript
let a = {'a':1,'b':'another one'}
//a,b are indexes and 1,'another one' are values.
```

`in` can directly iterate over these. `of` cannot. Instead we will have to use Object.entries(a), which in turns returns a key-value pair.

`...x` 'unwraps' a list

```javascript
x = [1,2,3];
b = new Array(5);
b = [4,...x,5]
//b is [4,1,2,3,5]
```

...x also makes it so that the values are a copy and not a pointer. By default JS makes pointers not copies.

---

##### Modules and Imports

If we want to use import in HTML call then we have to `<script type='module' src = 'thingy.js'>` regular script definition will not work.

If we want something to be imported in another JS file then we need to add `export` tag to it.

Alternatively we can have a explicit export block at the end.

```javascript
export {
    speed as c;
    useful_func as dummy_func;
}
```

`import {c, dummy_func} from './thng.js'` This will import c and dummy_func from thng.js

If we export a `default` thing then it will be wrapped into the first thing it can in the importer.

` export default function(){return "sadness";}`

`import {happy} from './thng.js'`

We can't change the value of imported variables as the scope remains in the original file. TO modify we should do it in the original file.

---

##### "Classes"

This is just a fancy list tbh.

```javascript
let human = {
    name: 'Manushya',
    get na(){
        return this.name;
    },
    set na(n){
    this.name = n;
    }
}

console.log(human.na); //Manushya
human.na = 'Ningen'
console.log(human.na); //Ningen
```

---

## Vue

Vue stuff

---

## Redis and SQLite

Redis stuff

---

## Flask

I'm thinking I have to do some listening at port 8000 or something.

---
