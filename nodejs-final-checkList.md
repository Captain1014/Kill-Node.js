# Final Review CheckList

## JS as a programming language

* arrow function vs normal function
  * `this` ?
- Arrow function
  - don't have their own "this", so inherit "this" from the enclosing scope.
```javascript
  const obj = {
  value: 42,
  getValue: function() {
    return () => this.value;
  }
};

const getVal = obj.getValue();
console.log(getVal()); // Output: 42
```
- Normal function
```javascript
function sayHello() {
  console.log(`Hello, ${this.name}`);
}

const person = { name: 'John' };
sayHello.call(person); // Output: Hello, John

```

  * `.bind()`?
- Arrow function : .bind() has no effect on its this binding. The arrow function retains "this" value from its lexical scope
```js
const obj = {
  name: 'Arrow Example',
  arrowFunc: () => {
    console.log(`Arrow Function: ${this.name}`); // Arrow Example (lexical scoping)
  },
};

const boundArrowFunc = obj.arrowFunc.bind({ name: 'Bound Arrow Example' });
boundArrowFunc(); // Arrow Example (lexical scoping)

```
- Normal function
```js
const person = {
  name: 'John',
  sayHello: function() {
    console.log(`Hello, ${this.name}!`);
  },
};

const greet = person.sayHello.bind(person);

greet(); // Hello, John!

```
  * scope
- Arrow function is lexical scoping, no 'arguments' or 'super' bidning
```js
// super use
class Animal {
  constructor(name) {
    this.name = name;
  }

  speak() {
    console.log(`${this.name} makes a sound.`);
  }
}

class Dog extends Animal {
  constructor(name, breed) {
    super(name); // Calls the constructor of the parent class (Animal)
    this.breed = breed;
  }

  speak() {
    super.speak(); // Calls the speak method of the parent class (Animal)
    console.log(`${this.name} barks!`);
  }
}

const myDog = new Dog('Buddy', 'Golden Retriever');
myDog.speak();
// Output:
// Buddy makes a sound.
// Buddy barks!

```

* commonly used built-in methods
  * Array.map() / Array.filter() / Array.forEach()
  * Array.splice() / Array.indexOf() ...
```js
const numbers = [1, 2, 3];
const doubledNumbers = numbers.map(num => num * 2);
console.log(doubledNumbers); // Output: [2, 4, 6]

const numbers = [1, 2, 3, 4, 5];
const evenNumbers = numbers.filter(num => num % 2 === 0);
console.log(evenNumbers); // Output: [2, 4]

const colors = ['red', 'green', 'blue'];
colors.forEach(color => console.log(color));
// Output:
// red
// green
// blue

const fruits = ['apple', 'banana', 'orange'];
fruits.splice(1, 1, 'grape'); // Remove one element at index 1 and add 'grape'
console.log(fruits); // Output: ['apple', 'grape', 'orange']

const numbers = [1, 2, 3, 4, 5];
const index = numbers.indexOf(3);
console.log(index); // Output: 2

```
```js
// midterm qs 1
// create two higher functions 'negate' and 'partition'. Do not use any regular loops.
// negate(oldFn) - (a decorator) returns a function that calls oldFn (the function passed in), and returns the opposite of oldFn's return value.
// assume that oldFn will return a boolean; no need to validate.
const negate = (oldFn) => {
  return (...args) => !oldFn(...args);
}
// partition(arr, fn) - takes an array of values and partitions it into two Arrays by calling the function, fn, on every element.
// if fn returns true, the element is added to the first array, otherwise it's added to the second.
// both arrays are returned nested in a containing array.
const partition = (arr, fn) => {
  return arr.reduce((result, element) => {
    const index = fn(element) ? 0 : 1;
    result[index].push(element);
    return result;
  }, [[], []]);
}

```
 
* Async
  * callback
  * Promise
  * Async Await  
```js
function fetchData(callback) {
  setTimeout(() => {
    const data = 'Async Data';
    callback(data);
  }, 1000);
}

fetchData(result => console.log(result));
// Output (after 1 second): Async Data


function fetchData() {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      const data = 'Async Data';
      resolve(data);
    }, 1000);
  });
}

fetchData().then(result => console.log(result));
// Output (after 1 second): Async Data


async function fetchData() {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      const data = 'Async Data';
      resolve(data);
    }, 1000);
  });
}

async function fetchDataAndPrint() {
  const result = await fetchData();
  console.log(result);
}

fetchDataAndPrint();
// Output (after 1 second): Async Data


```
## Server-side JS, Express, hbs

### hbs

### Express

=== LIKELY CODING QUESTION ===
- example question: Create a simple Express application that serves an HTML page using Handlebars. The HTML page should display a message with a variable value passed from the server. 
```js
// app.js
const express = require('express');
const exphbs = require('express-handlebars');

const app = express();
// Configure Handlebars
app.engine('hbs', exphbs({ defaultLayout: 'main', extname: '.hbs' }));
app.set('view engine', 'hbs');

app.get('/', (req,res) => {
    const message = "hello, handlebars";
    res.render('index', {message});
});



// Create an Express route that handles a POST request. Parse the incoming JSON data and send a response with the processed data.
app.post('/processData', (req, res) => {
  const jsonData = req.body;
  // Perform processing on jsonData
  const processedData = { result: 'Processed', data: jsonData };
  res.json(processedData);
});

app.listen(3000);

```

```js
// midterm qs
// Adds a new property to the req object, cookiejar, for every incoming request.
// cookiejar contain name and value pairs in an object as the cookies
const myFunction=(req,res,next)=>{
  req.cookieJar ={};
  const s = req.headers.cookie;
  if (s) {
    req.cookieJar = s.split(';').reduce((obj, pair) => {
      const [k,v] = pair.trim().split('=');
      obj[k] = v;
      return obj
    }, {})
  }
 next();
}
app.use(myFunction);
```
```js
// midterm qs 2
// the web app consists of a single path, /home. This path displays a form and a list of links.
// when the form is submitted, a new link is displayed at the bottom of the list of links as an <a> tag.
// the url entered in the form is the href and the description is the link text.
// however, if the url is the same as another url that's already in data:
// the duplicate link is not added to the data array
// instead, a duplicate error message is shown on the page.
// if there's a successful new url added, refreshing the page should not result in a form resubmission.
// if the initial form submission was not successful, it's ok if refreshing the page cause a resubmission.
// write only the route handlers necessary to implement this.
// you must use the home.hbs template below to guide your implementation

// views/home.hbs
{{#if errorMsg}}<div>{{ errorMsg }}</div> {{/if}}

<form method="POST" action="">
  <label>url</label> <input type="text" name="url">
  <label>desc</label> <input type="text" name="description">
  <input type="submit" value="add link">
</form>

<ul>
{{#each links}}
<li>
<a href="{{url}}">{{description}}</a>
</li>
{{/each}}
</ul>
```
```js
//app.js
// assume all imports, middleware, and express set up are already present
const data = [
  {url: 'https://cs.nyu.edu', description: 'nyu'},
   {url: 'https://cs.ucla.edu', description: 'ucla'},

]
// complete this code
// route handler for the home page
app.get('/home', (req,res) => {
  res.render('home', {links: data, errorMsg: req.session ? req.session.errorMsg : null});
});

// route handler for form submission
app.post('/home', (req,res) => {
  const url = req.body.url;
  const description = req.body.description;

  // check for duplicate urls
  const isDuplicate = data.some((link) => link.url === url);

  if(isDuplicate){
    res.render('home', {links: data, errorMsg: 'Duplicate url'});
  } else {
    data.push({url, description});
    req.session.errorMsg = null;
    res.redirect('/home');
  }


});

app.listen(3000);

```


## HTTP/HTTPS Protocal

* http request/response syntax
```html
// midterm qs
// Form
<form method="POST" action="">
<input type="text" name="mystery">
<input type="submit" value="Go!">
</form>
// resulting page
<h1>Egg</h1>
<img src="egg.gif" />
```

* write  2 http requests and 2 responses in the order after the submit button is pressed so that the entire page is rendered by the browser. After this interaction, the browser will have a cookie named 'meal' set to 'breakfast'

// request 1
// the text field is filled with "extra"
```
POST /food HTTP/1.1
Content-Type: x-www-form-urlencoded

mystery=extra 
```
// response 1
```
HTTP/1.1 200 OK
Content-Type: text/html

html as body
```
// request 2
```
GET /egg.gif HTTP/1.1
```
// response 2
```
HTTP/1.1 200 OK
Content-Type: image/gif

image data as body
Set-Cookie: meal=breakfast
```

### Some data transferred via HTTP

* sessions
  - session ids shouldn't be present in the query string of a url
  - they shouldn't be generated sequentially, and adequately long / complex
* cookies
  - text files stored by browser. they can store a session id which links to more data on the server as well as client side data.
* how do they work?
1. server generates a session id for a http request
2. http response tells the browser to store a session id in a cookie (Set-Cookie)
3. browser creates or updates a cookie
4. the cookie contains some identifier (the session id)
5. when browser makes a request to the server, it sends along that identifier
6. the server finds the session associated with that identifier
7. the session store (can be in-memory, file-based or database)
8. In the session store : user's session (auth)

* Q. in express, name all values that are stored on the client if a session variable named 'darkMode' is set to true?
  - a cookie named darkMode set to true 
````
// response that sets a few cookie values
HTTP/1.0 200 OK
Content-type: text/html
Set-Cookie: foo=bar
Set-Cookie: baz=qux 
Set-Cookie: session_id=5d6d473c-a370-44c8-bff0-4f28efd7c92a; HttpOnly; Secure

// request that sends back cookies
GET / HTTP/1.1
Cookie: foo=bar;baz=qux

````

## Database, mongodb and mongosh

=== LIKELY CODING QUESTION ===

### Mongo

### Mongosh commands

* databases
  - show dbs
  - use your_database_name

* collections
  - show collections
  - db.createCollection('your_collection_name')
  - db.your_collection_name.drop()

* CRUD
  - db.your_collection_name.insertOne({ key: 'value' })
  - db.your_collection_name.find()
  - db.your_collection_name.updateOne({ key: 'value' }, { $set: { newKey: 'newValue' } })
  - db.your_collection_name.deleteOne({ key: 'value' })


### Mongoose module

Steps to use mongo database
1. Intall mongoose
2. mongoose.connect
3. create a mongoose schema
4. mongoose.model
5. use the model to perform CRUD

```js
import mongoose from "mongoose';

mongoose.connect('mongodb://localhost/your_database_name', {
  useNewUrlParser: true,
  useUnifiedTopology: true,
});


const userSchema = new mongoose.Schema({
  username: String,
  email: String,
  age: Number,
});

const User = mongoose.model('User', userSchema);

// Create
const newUser = new User({
  username: 'john_doe',
  email: 'john@example.com',
  age: 25,
});

newUser.save()
  .then((result) => {
    console.log('User saved:', result);
  })
  .catch((error) => {
    console.error('Error saving user:', error);
  });

// Read
User.find({ username: 'john_doe' })
  .then((users) => {
    console.log('Found users:', users);
  })
  .catch((error) => {
    console.error('Error finding users:', error);
  });

// Update
User.updateOne({ username: 'john_doe' }, { $set: { age: 26 } })
  .then((result) => {
    console.log('User updated:', result);
  })
  .catch((error) => {
    console.error('Error updating user:', error);
  });

// Delete
User.deleteOne({ username: 'john_doe' })
  .then((result) => {
    console.log('User deleted:', result);
  })
  .catch((error) => {
    console.error('Error deleting user:', error);
  });

```
---

---

## Client-side (HTML, JS, DOM)

### DOM

* What is DOM, how it is mananged
  - DOM is a programming interface for interacting with html objects.
* get/insert/change DOM Nodes
  
* add events

```js
// Getting DOM Nodes
document.getElementById("myID");
document.getElementsByClassName("myClass");
document.getElementsByTagName("div");

// Inserting and changing
document.createElement("div");
parentElement.appendChild(newElement);
element.innerHTML = "New content";

```
```html
// Add events
<button id="myButton">Click me</button>

<script>
    var button = document.getElementById("myButton");

    button.addEventListener("click", function() {
        alert("Button clicked!");
    });
</script>


```

### AJAX

* how to handle Promise
  - Promises are used to handle "asynchronous" operations.
```js
// creating a promise
const myPromise = new Promise((resolve, reject) => {
    // Asynchronous operation or task

    if (/* operation successful */) {
        resolve("Success!"); // Resolve with a value
    } else {
        reject("Error!"); // Reject with an error message
    }
});

// handling promises
myPromise
    .then((result) => {
        console.log("Promise resolved:", result);
    })
    .catch((error) => {
        console.error("Promise rejected:", error);
    })
    .finally(() => {
        console.log("Finally block, regardless of success or failure.");
    });

```
* `fetch()`
  - a modern alternative to "XMLHttpRequest" for making http requests. It returns a Promise that resolves to the http response.
```js
fetch('https://api.example.com/data')
    .then(response => {
        if (!response.ok) {
            throw new Error('Network response was not ok');
        }
        return response.json();
    })
    .then(data => {
        console.log('Data:', data);
    })
    .catch(error => {
        console.error('Fetch Error:', error);
    });

```

 
## Websocket & socket.io

=== LIKELY CODING QUESTION ===

Websocket is a protocal that transfer data between host and device in real time; Socket.io is a module for Websocket.

Difference between HTTP protocals:

* light-weighted, less data is transferred
* real-time
* stateful -- http is stateless
* looks like a json, but no header

Compose of 2 parts, Client-side and Server-side

Client-side:

```html
<script src="link/to/socket.io.js"></script>
<script>
    // instantiate 
    const socket = io();
    // listen for lessage from the server, log the message
    socket.on("message_name", (msg)=>{
      console.log(msg)
    
   // Display the received message on the page
    const messageElement = document.createElement('p');
    messageElement.textContent = msg;
    document.body.appendChild(messageElement);
    });
    // when client sent message to server
    document.getElementById("btn").addEventListener("onClick", ()=>{
        // send {"message_name": "content"} to server
        socket.emit("message_name", "content");
    });
</script>
```

Server-Side:

```js
import {createServer} from "http";
import {Server} from "socket.io";

const app = express();
const io = new Server(createServer(app));
// when server get connection from new client
io.on('connection', (socket)=>{
    // welcome message
    socket.emit('greeting', {msg: 'hello'});
    // when server receive message, do something
    socket.on('message_name', (msg)=>{
      console.log(msg);
    });
    // when server boardcasting message (e.g. the winning message from lab)
    io.emit("message_name", "msg");

    // when server disconnect from new client
    socket.on("disconnet", ()=>{});
});
```

## Security

### Authentication

* Hash
* Salt
```js
const bcrypt = require('bcrypt');
const plaintextPassword = 'user_password';

// Generating a salt and hashing
bcrypt.genSalt(10)
  .then((salt) => {
    return bcrypt.hash(plaintextPassword, salt);
  })
  .then((hash) => {
    console.log('Hash:', hash);
  })
  .catch((error) => {
    console.error('Error hashing password with salt:', error);
  });

```
### Possible attacks, mechanisms and prevention
* CSRF Attack (Cross-Site Request Forgery):
CSRF attacks involve an attacker making unauthorized requests on behalf of a user who is already authenticated. To prevent CSRF attacks:

  - Use anti-CSRF tokens in forms.
  - Validate the origin of requests using the Origin or Referer header.

* XSS Attack (Cross-Site Scripting):
XSS attacks involve injecting malicious scripts into web pages that are viewed by other users. To prevent XSS attacks:

  - Sanitize user inputs before rendering them on the page.
  - Use Content Security Policy (CSP) headers to restrict the sources of scripts.
## CSS

=== LIKELY CODING QUESTION ===

### Selector, some attributes & values

Selectors have priority difference; if there is conflict, higher priority will apply.

e.g. `#id` > `.class` > `html name`

```css
a{
    /** select by tag name */
}
.class{
    /** select by class name */
}
#id{
    /** select by id */
}
div.class{
    /** select all <div class="class"> */
}
div .class{
    /** 
    select all element with class="class" that is inside div
    <div>
        <a class="name">This is selected</a>
        <span>
            <a class="name">This is selected</a>
        </span>
    </div>
    */
}
div > .class{
    /** 
    select all element with class="class" that is DIRECT child of <div> 
    <div>
        <a class="name">This is selected</a>
        <span>
            <a class="name">This is NOT selected</a>
        </span>
    </div>
    */
}
a:hover{
    /** specify style when event is triggered, e.g. when your cursor is put on <a> */
}
```

Attributes:

```css
div {
    display : block/inline/inline-block/none/flex(not required?);
    position : relative/absolute/fixed;
    width/height: 1px/10%/0;
    z-index: 1; /** whether it is above or below */
    margin: 1px; /** space around */
}
```

KeyFrame:

```css
@keyframes animationname{
    0% : {left: 0px};
    100% : {left: 100px}
}
.box{
    animate: animationname 1px;
}
```

## React

=== LIKELY CODING QUESTION ===

### class Component (taught in previous years)

### function Component
- function component returns a react element. 
1. useState : Once state changes, component re-renders.
2. useRef : does not cause a re-render. allows reference to DOM element.
3. useEffect : calls function on event
- useEffect(f, depArray)
  - no array: call on render
  - if '[]': call on mount
  - if [val]: call when van changes and on mount

Simple use case with `useState()` and `useEffect()`

```js
import React, {useState, useEffect, useRef} from "react";

const Component = (prop) => {
    const [bar, setBar] = useState("initial value");
    const [url, setUrl] = useState("foo");

    // passing no params into the callback, the callback function will
    // trigger when the Component is Mounted or Update
    useEffect(()=>{
        console.log("hello");
    }, []);
    // the callback function will trigger when url is Updated
    useEffect(()=>{
      let cancel = false;
        async function fetchAPI() {
          // fetch api here
          const res = await fetch(url)
          const data = await res.json()
          if(!cancel){
            setData(url);
          }
        }

          if(url!==null){
            fetchAPI()
          }
          return () => {
            cancel = true
            }
    }, [url]); // useEffect gets triggered whenever url changes

    const onClick = () => {
        setBar("New Value"); // when state bar changes, the element will re-render
    }   

    return <div>
        <SubComponent foo={bar} onClick={()=>{onClick()}}/>
    </div>
}
const SubComponent = (prop) => {
    return <div onClick={prop.onClick}> {prop.foo} </div>
}

// useRef
function App() {
  const [name, setName] = useState('') // once submit name, show up below
  const nameInput = useRef(null) // useRef is a Hook that provides a mutable object called ref which has a current property.

  return (
    <>
    your name <input ref={nameInput} type="text" />
    <button onClick={evt => setName(nameInput.current.value)}>submit</button>
    <h1>hello {name}</h1>
    </>
  )
}
```
- When do we use prop:
  - to deliver data to the child component. Include 'props' in the child component. 
```js
// ParentComponent.js
import React from "react";
import ChildComponent from "./ChildComponent";

const ParentComponent = () => {
  const message = "Hello from ParentComponent";

  return <ChildComponent message={message} />;
};

export default ParentComponent;

// ChildComponent.js
import React from "react";

const ChildComponent = (props) => {
  return <div>{props.message}</div>;
};

export default ChildComponent;

```
