#JavaScript cheatsheet

### Variables
#### Old way
```javascript
var name = 'Jeppe';
var age = 10:
```

#### ES6
```javascript
// if value stays constant
const name = 'Jeppe';
// if value can change later
let age = 10;
```

### Functions
#### Really old way (unless you want to add method to class)
```javascript
function myFunction(param1, param2) {
  // do something... 
}
```
#### Old way
```javascript
var myFunction = function(param1, param2) {
  // do something...
}
```
#### ES6
```javascript
const myFunction = (param1, param2) => {
  // do something...
}
```

### Selecting HTML elements
```html
<p id="btn">Click me!</p>
```
```javascript
const element = document.querySelector('#btn');
```

### Event handling
#### Really old way
```html
<p onclick="// do something...">Click me!</p>
```
#### Old way
```javascript
element.onclick = function(evt){
  // do something...
};
```
#### ES6
```javascript
element.addEventListener('click',  (evt) => {
  // do something...
});
```

### AJAX get method
#### Old way
```javascript
const xhr = new XMLHttpRequest();
xhr.open('get', 'someJsonResponseServlet');
xhr.onreadystatechange = function(){
   if (xhr.readyState == 4 && xhr.status == 200) {
         const result = JSON.parse(xhr.responseText);
         console.log(result);
      }
}
xhr.send();
```
#### New way
```javascript
const getFetchData = async (url) => {
   const response = await fetch(url);
   const result = await response.json();
   console.log(result)
}

getFetchData('someJsonResponseServlet');
```

### AJAX post method
#### Old way
```javascript
// data has file(s) (multipart/form-data)
const myForm = document.querySelector('form');
const fData = new FormData(myForm);
const xhr = new XMLHttpRequest();
xhr.open('post', 'someJsonResponseServlet');
xhr.onreadystatechange = function(){
   if (xhr.readyState == 4 && xhr.status == 200) {
         const result = JSON.parse(xhr.responseText);
         console.log(result);
      }
}
xhr.send(fData);
```
#### New way
```javascript
// data has file(s) (multipart/form-data)
const myForm = document.querySelector('form');
const fData = new FormData(myForm);

const postFetchData = async (url, data) => {
   // settings object for fetch 
   const settings = {
     method: 'post',
     body: data
   };
   const response = await fetch(url, settings);
   const result = await response.json();
   console.log(result);
}

getPostData('someJsonResponseServlet', fData);

// send text data as JSON
const someData = {username: 'frank', password: 'qwer1234'};

const postFetchData = async (url, data) => {
   // settings object for fetch 
   const settings = {
     method: 'post',
     headers: {
       'Content-Type': 'application/json'
     },
     body: JSON.stringify(data)
   };
   const response = await fetch(url, settings);
   const result = await response.json();
   console.log(result);
}

getPostData('someJsonResponseServlet', someData);
```
