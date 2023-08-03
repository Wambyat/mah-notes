# Application Development 2

This is a compilation of things that i have learnt that I will be using in the project.

# Index

- [JavaScript](#javascript)
- [Vue](#vue)
- [Redis and SQLite](#redis-and-sqlite)
- [Flask](#flask)

---

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

---

#### Templates/ jQuery

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

#### Functions

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

JS auto-ignores extra arguments and also gives `undefined` to parameters that aren't passed.

`a.test(b)` "compares" a and b. This can be in the form of Regex so `re.test("aabbbaa")`. Returns True or False.

---

#### DOM Stuff

`document.getElementById('<ID HERE>')` This gets the thing from DOM and makes it into an object.

`x.addEventListener('click',<func here>)`

`JSON.stringify()` makes the object into a string notation.

`JSON.parse()` makes an object from a string. This object will be a list type. Need not be whatever the original object might have been.

---

#### Arrays

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

#### Modules and Imports

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

#### "Classes"

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
    'add': function (x,y) {
        return x+y+this.name;
    }
}

console.log(human.na); //Manushya getter
human.na = 'Ningen'; // setter
console.log(human.na); //Ningen
let z = human.add
//we can do z.add alternatively
//z.call(<object>,<params>...) This lets us pass different objects.
z.call(human,"my","name is")
z.apply(human,["my","name is"])
```

`.bind(<params>)` Permanently saves a value to a parameter.

##### Prototypes

This is inheritance. 

```javascript
let y = {__proto__: human, 'leg': 2}
console.log(y) //{ 'leg' : 2}
//Does not print human values but they do exist
```

---

#### Class

This is the new and actual classes.

```javascript
class Animal {
    constructor(name) {
        this.name = name;
    }
    describe() {
        return this.name+"ooga boogga"+this.sound;
    }
}

//inheritence
class Dog extends Animal {
    constructor(name) {
        super(name);
        this.sound = 'Bow';
    }
}
```

---

#### Promises

All `async` functions return a Promise by default. We can use `.then()` To resolve them.

```javascript
async function hell() {
    return "Hell is at KR Puram";
}
console.log("something");
hell.then((val) => console.log(val));
console.log("else");
```

Remember that `.then`  pretty much makes a new thread.

Another stupid shit is this crap.

```javascript
async function hell(){
    return new Promise((resolve,reject) => {
        setTimeout(function(){
            resolve("async bullshit")
        }, 2000);
    });
}
```

This essentially makes it so the Promise auto resolves after 2000 milliseconds.

`await` ensures that the main thread waits for a resolve. This is where this crap is sorta important. We can still do it in the same old way where JS makes it's own promise but idiots do this for some reason.

We can catch the rejects by:

```javascript
hell().then(<some shit here>).catch(e => {<error shit here>})
```

---

## Vue

Here we make an object for each thing. 

```javascript
var app = new Vue({
    el: "<name of the element>",
    data: {"<all the data crap u wanna put goes here>"},
    methods: {"<all the fucntions crap u wanna put goes here>"},
    computed: {"<This holds all variables that should be run on each call like the size of a list or something>"}
})
```

```html
<html lang="en">
<head>
    <script src="https://cdn.jsdelivr.net/npm/vue@2/dist/vue.js"></script>
</head>
<body>
    <div id = "app">
        Before vue's nonsense
        <p>{{ message }}</p>
        <button v-on:click="clickFunc" v-on:mouseover="mouseFunc"> Say Hi 🔫</button>
    </div>
</body>
<script type="text/javascript" src = "application.js"></script>
</html>
```

List of v-on functions:

- click

- mouseover

`v-if, v-else-if, v-else` are if statements.

To get data from the html we use `v-model`

```html
<input type="text" v-model="name">
```

`v-for` is a for loop.

```html
<li v-for="na in names">{{na}}</li>
```

To dynamically add a class to a html tag we can use `v-bind:class="<class name here>"`. This is very useful when we use bootstrap.

#### Components

These are reusable things in Vue. 

```javascript
Vue.component('message-board',{
    props:[<List of things u get from the html>],
    template : `<Jinja esk stuff here>`,
    data: function() {
        return {
            message: "default message"
        }
    },
    methods: {
        <Functions here>
    },
    computed : {
            <Every call functions here>
        }
    }
})
```

`<message-board>` Will call the component.

#### Event Raising

`this.$emit("<event name>")`. See code more more details.

> **CHECK WATCH IN VUE** Written below

#### Local Storage

We can store some amount of variables and data on the client side. This is using `localStorage` .

```javascript
.
.
.
mounted() {
    if(localStorage.name) {
        this.name = localStorage.name;
    }
},
watch : {
    name(newName) {
        localStorage.name = newName;
    }
}
.
.
.
```

#### Forms

We can make a form like so:

```html
<form
  id="app"
  @submit="checkForm"
  action="https://vuejs.org/"
  method="post"
>
    <p v-if="errors.length">
    <b>Please correct the following error(s):</b>
    <ul>
      <li v-for="error in errors">{{ error }}</li>
    </ul>
 </p>
 
 <p>
    <label for="movie">Favorite Movie</label>
    <select
      id="movie"
      v-model="movie"
      name="movie"
    >
      <option>Star Wars</option>
      <option>Vanilla Sky</option>
      <option>Atomic Blonde</option>
    </select>
  </p>

  <p>
    <input
      type="submit"
      value="Submit"
    >
  </p>

</form>
```

`@submit` is the function setting thingy. Usually we do like this:

```javascript
const app = new Vue({
    el :"#app",
    data : {
        movie : null
        errors : []
    },
    methods : {
        checkForm(e) {
            this.errors = [];
            if (!movie) {
                errors.push("Choose a novie ya git");
            }
            else {
                return True;    
            }
            e.preventDefault();
        }
    }
})
```



---

## Redis and SQLite

Redis stuff

---

## Flask

I'm thinking I have to do some listening at port 8000 or something.

---
