# Javascript Snippets

## DOM Manipulation Events


### DOM Exploration

``` Javascript

document.all; // gives the collections of all the element
document.all[0];
document.all.length;
document.head;
document.body;
document.doctype;
document.domain;
document.URL;
document.characterSet;
document.contentType;

// Select element without the selector

document.forms; // html collection
document.forms[0]; // access the first form
document.forms[0].id;
document.forms[0].method;
document.forms[0].action;

document.links;
document.links[0];
document.links[0].id;
document.links[0].className;
document.links[0].classList;
document.links[0].classList[0];

document.images;

document.scripts;
document.scripts[2].getAttribute('src');

// convert html collection into javascript array

let scripts = document.scripts;

let scriptsArr = Array.from(scripts)

scriptsArr.forEach(function(script){
  console.log(script);
})

```

### DOM Selectors (Single element and multiple elements selectors)

DOM Selectors For Single Elements

``` Javascript

// document.getElementById()

console.log(document.getElementById('task-title)');

// Get things from the element
console.log(document.getElementById('task-title').id);
console.log(document.getElementById('task-title').className);


// Change styling
document.getElementById('task-title').style.background = '#333'; 
document.getElementById('task-title').style.color = '#fff'; 
document.getElementById('task-title').style.padding = '5px'; 
document.getElementById('task-title').style.display = 'none'; // will make this element disappear

// Change content
document.getElementById('task-title').textContent = 'task List';
document.getElementById('task-title').innerText = 'My List';
document.getElementById('task-title').innerHTML = '<span style="color:red"> Task List</span>';

const taskTitle = document.getElementById('task-title');


// document.querySelector()  much powerful than getElementById()

console.log(document.querySelector('#task-title'));
console.log(document.querySelector('.card-title'));
console.log(document.querySelector('h5')); //This will only get the first h5 element if there are more h5 elements

document.querySelector('li').style.color = 'red'; // Only get the first 'li' element, because this is a single selector
document.querySelector('ul li').style.color = 'blue';

// use the CSS psudo class to select the last element
document.querySelector('li:last-child').style.color = 'blue';
document.querySelector('li:nth-child(3)').style.color = 'yellow';
document.querySelector('li:nth-child(4)').textContent = 'Hello World';
document.querySelector('li:nth-child(odd)').style.background = '#ccc'; // it is not going to do all the odd, because this is the single element selector

```


DOM Selectors For Multiple Elements

``` Javascript
// document.getElementsByClassName

const items = document.getElementsByClassName('collection-item'); // html collection
console.log(items);
console.log(items[0]);
items[0].style.color = 'red';
items[0].textContent = 'Hello';

const listItems = document.querySelector('ul').getElementsByClassName('collection-item');
console.log(listItems);

// document.getElementsByTagName
let lis = document.getElementsByTagName('li'); // html collection
console.log(lis);
console.log(lis[0]);
lis[0].style.color = 'red';
liss[3].textContent = 'Hello';

// Convert HTML Collection into array

lis = Array.from(lis);

lis.reverse();

lis.forEach(function(li, index){
  console.log(li.className);
  li.textContent = `${index}: Hello`;
});


// document.querySelectorAll

const items = document.querySelectorAll('ul.collection li.collection-item');

console.log(items); // NodeList

items.forEach(function(item, index){
  item.textContent = `${index}: Hello`;
});

const liOdd = document.querySelectorAll('li:nth-child(odd)');
const liEven = document.querySelectorAll('li:nth-child(even)');

liOdd.forEach(function(li, index){
  li.style.background = '#ccc';
});

for(let i = 0; i < liEven.length, i++>){
  liEven[i].style.background = '#f4f4f4';
} // this function can be used in HTML Collection

```

### DOM Traverse 

``` Javascript

let val;

const list = document.querySelector('ul.collection');
const listItem = document.querySelector('li.collection-item:first-child');

val = listItem;
val = list;

// Get child nodes
val = list.childNodes; // Node list
val = list.childNodes[0];
val = list.childNodes[0].nodeName;
val = list.childNodes[0].nodeType;

// 1 - Element
// 2 - Atribute (deprecated)
// 3 - Text node
// 8 - Comment
// 9 - Document itself
// 10 - Doctype


// Get children element nodes
val = list.children; // HTML Collection
val = list.children[0];
val = list.children[1].textContent = 'Hello';

// Children of children 
list.children[3].childre[0].id = 'test-link';
val = list.children[3].children[0];

// First child
val = list.firstChild; // give first node 
val = list.firstElementChild; // give the first element

// Last child
val = list.lastChild;
val = list.lastElementChild;

// Count child elements
val = list.childElementCount;

// Get parent node
val = listItem.parentNode;
val = listItem.parentElement;
val = listItem.parentElement.parentElement;

// Get next sibling
val = listItem.nextSibling;
val = listItem.nextElementSibling;
val = listItem.nextElementSibling.nextElementSibling;

// Get prev sibling
val = listItem.previousSibling;
val = listItem.previousElementSibling;

console.log(val);

```

### Create elements

``` Javascript
// Create element

const li = document.createElement('li');

// Add class
li.class.Name = 'collection-item';

// Add id
li.id = 'new-item';

// Add atribute
li.setAttribute('title', 'New Item');

// Create text node and append
li.appendChild(document.createTextNode('Hello World')); 

// Create new link element
const link =  document.createElement('a');
// Add classes
link.className = 'delete-item secondary-content';
// Add icon html
link.innerHTML = '<i class="fa fa-remove"></i>;

// Append link into li
li.appendChild(link);


// Append li as child to ul
document.querySelector('ul.collection').appendChild(li);

console.log(li)

```

### Removing and Replacing Elements

``` Javascript
// REPLACE ELEMENT

// Create Element

cosnt newHeading = document.createElement('h2');
// Add id
newHeading.id = 'task-title';
// New text node
newHeading.appendChild(document.createTextNode('Task List'));

// Get the old heading
const oldHeading = document.getElementByid('task-title');
// Parent
const cardAction = document.querySelector('.card-action');

//Replace
cardAction.replaceChild(newHeading,oldHeading);

// REMOVE ELEMENT

const lis = document.querySelectorAll('li');
const list = document.querySelector('ul');

// Remove list item
lis[0].remove();

// Remove child element
list.removeChild(lis[2]);

// CLASS & ATTR
const firstLi = document.querySelector('li:first-child');
const link = first.children[0];

let val;

// Classes
val = link.className;
val = link.classList; // DOME Token list
val = link.classList[0];
link.classList.add('test');
link.classList.remove('test');
val = link

// Atribute
val = link.GetAttribute('href');
val = link.setAttribute('href','http://google.com');
val = link.hasAttribute('href');
link.setAttribute('title', 'Google');
link.removeAttribute('title');

console.log(val);

console.log(newHeading);

``` 

### Event Listeners & The Event Object

``` Javascript
document.querySelector('.clear-tasks').addEventListener('click',function(e){
  console.log('Hello World');

  e.preventDefault(); // prevent the link default behavior
})

// pass a function 
document.querySelector('.clear-tasks').addEventListener('click',onClick);
function onClick(e){
  console.log('Clicked');

  let val;
  val = e;

  // Event target element
  val = e.target;
  val = e.target.id;
  val = e.target.className;
  val = e.target.classList;

  e.target.innerText = 'Hello';

  // Event type
  val = e.type;


  // Timestamp 
  val = e.timeStamp


  // Coordinate event relative to the window
  val = e.clientY;
  val = e.clientX;

  // Coordinate event relative to the element
  val = e.offsetY;
  val = e.offsetX;

  console.log(val);
}

```

### Mouse Event

``` Javascript
const clearBtn = document.querySelector('.clear-tasks');
const card = document.querySelector('.card');
const heading = document.querySelector('h5');

// Click
clearBtn.addEventListener('click', runEvent);

// Doubleclick
clearBtn.addEventListener('dblclick',runEvent);

// Mousedown
clearBtn.addEventListener('mousedown',runEvent); // click the mouse and hold

// Mouseup
clearBtn.addEventListener('mouseup',runEvent);

// Mouseenter
card.addEventListener('mouseenter',runEvent);

// Mouseleave
card.addEventListener('mouseleave',runEvent);


//Mouseover
card.addEventListener('mouseover',runEvent);

//Mouseout
card.addEventListener('mouseout',runEvent);

// Mousemove
card.addEventListener('mousemove',runEvent);





// Event Handler 

function runEvent(e){
  console.log(`EVENT TYPE: ${e.type}`)

  heading.textContent = `MouseX: ${e.offsetX} MouseY: ${e.offsetY}`;

  document.body.style.backgroundColor = `rgb(${e.offsetX},${e.offsetY},40)`;
}

```

### Keyboard event

``` Javascript
const form = document.querySelector('form');
const taskInput = document.getElementById('task');
const heading = document.querySelector('h5');
const select = document.querySelector('select');

// Clear input
taskInput.value = ' '; 

form.addEventListener('submit', runEvent);

// keydown
taskInput.addEventListener('keydown', runEvent);

// keyup
taskInput.addEventListener('keyup', runEvent);

// keypress
taskInput.addEventListener('keypress', runEvent);

//Focus
taskInput.addEventListener('focus', runEvent);

// Blur, opposite of Focus
taskInput.addEventListener('focus', runEvent);

// Cut
taskInput.addEventListener('cut', runEvent);

// Paste
taskInput.addEventListener('paste', runEvent);

// Input
taskInput.addEventListener('input', runEvent);

// Change, for select
select.addEventListener('change', runEvent);






function runEvent(e){
  console.log(`EVENT TYPE: ${e.type}`);


  console.log(e.target.value);
  heading.innerText = e.target.value;

  // Get input value
  console.log(taskInput.value);

  e.preventDefault(); // Stop redirecting
}

``` 

### Event Bubbling & Delegation

``` Javascript
// EVENT BUBBLING

document.querySelector('.card-title')addEventListener('click',
function(){
  console.log('card title');
});


document.querySelector('.card-content')addEventListener('click',
function(){
  console.log('card content');
});

document.querySelector('.card')addEventListener('click',
function(){
  console.log('card');
});

document.querySelector('.col')addEventListener('click',
function(){
  console.log('col');
});


// EVENT DELGATION

// const delItem = document.querySelector('.delete-item');

// delItem.addEventListener('click', deleteItem);

document.body.addEventListener('click',deleteItem);


// function deleteItem(e){
//   console.log(e.target);
//   if(e.target.parentElement.className === 'delete-item secondary-content'){
//     console.log('delete item');
//   }
// }


function deleteItem(e){
  console.log(e.target);
  if(e.target.parentElement.className.contains('delete-item')){
    console.log('delete item');
    e.target.parentElement.parentElement.remove();
  }
}


```


### Local & Session Storage

``` Javascript

// set local storage item

localStorage.setItem('name','John');

// set session storage item, data will be cleared out once the browswer is closed. 
sessionStorage.setItem('name','Beth');

// remove from storage 
localStorage.removeItem('name');

// get from storage 
const name = localStorage.getItem('name');
console.log(name);

// clear local storage
localStorage.clear();

// add the input from form into the local storage

document.querySelector('form').addEventListener('submit',
function(e){
  const task = document.getElementById('task').value;

  let tasks;
  if(localStorage.getItem('tasks') === null){
    tasks = [];
  } else {
    tasks = JSON.parse(localStorage.getItem('tasks'));
  }

  tasks.push(task);

  localStorage.setItem('tasks',JSON.stringify(tasks));
  alert('Task saved');
  e.preventDefault();
})

const tasks = JSON.parse(localStorage.getItem('tasks'));

tasks.forEach(function(task){
  console.log(task);
})


```

## DOM Project

