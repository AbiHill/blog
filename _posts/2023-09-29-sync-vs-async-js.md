---
title: "Sync Vs Async JavaScript"
date: 2023-12-09
---

In this article, I will cover off the difference between synchronous (Sync) and asynchronous (Async) programming models, specifically when writing JavaScript. This common JavaScript pattern is a concept that is usually misunderstood and can cause bugs in code, therefore it is really important that we grasp the different concepts and tools available to us to leverage this programming model in our applications.

## What is Synchronous JavaScript?

Synchronous JavaScript is code that executes from top to bottom and in that order. It will execute line by line and will not move on to the next line of code until the current line has been completed. 

### Real Life Example

A real-life example of this type of process could be when you are ticking off your shopping list. If you have a list of items on your shopping list, and you add each item one by one to your basket without skipping to the next - this has been executed in order and synchronously. 

### Code Example

The below code snippet is an example of very simple code that will execute in order from top to bottom (synchronously). 

```jsx
let a = 'apple'
let b = 'banana'

console.log(a)
console.log(b)
```
```jsx
apple
banana
```

## What is Asynchronous Code?

Asynchronous code is similar to synchronous code in the sense that it will execute from top to bottom, however, whilst running it might come across a piece of code (for example a function) that will split off and execute separately and take time. Whilst this part of the code is executing, the next line of code will execute and complete, meaning that the code is executing and completing at different times, thus asynchronously. 

### Real Life Example**

If we go back to our shopping list example above, we can create a real-life asynchronous example too. Let’s say you are adding the items on your shopping list to your basket, however, when you come to the deli counter, you ask the shop assistant for some brie, they advise that they need to cut the brie so ask you to return in 10 minutes. During the 10 minutes, you continue to add the rest of your shopping list into your basket, then you head back to the deli counter to collect your brie. Whilst you’re away the assistant is cutting and wrapping your item. This is an example of two things happening asynchronously for your task of shopping.

### **Code Example**

Similarly to the above shopping example, we can see that JavaScript will run asynchronously at times too. 

```jsx
let itemOne = 'apple'
let itemTwo = 'banana'
let itemThree = 'brie'
let itemFour = 'Soap'

console.log(itemOne)
console.log(itemTwo)

setTimeout(()=> {
	console.log(itemThree)
}, 5000);

console.log(itemFour)
```

```jsx
apple
banana
Soap
undefined
brie
```

As you can see from the above log, the code will execute from top to bottom. However, due to our set timeout, the console.log for item three will log after our console log for item three.

### Callbacks

The above `setTimeout` method is an example of a callback function. This is when you pass a function as an argument into another function to execute. 

## **What does Javascript give us that can help with this?**

### **Promises**

In JavasScript we have an object that’s called a Promise. A Promise is an object that represents the eventual completion or failure of an asynchronous operation. 

### **Real Life Example**

Going back to our shopping example again, we can say that when the deli assistant goes to cut the brie for you, he promises to return with the cut and wrapped brie. On his return, he will either have the brie for you, or he may have a reason as to why he can not give you the brie. This is the same as a promise in JavaScript, it may return with what you are after, or it may return with an error. 

### Promise Object Properties

A JavaScript Promise object can be:

- Pending
- Fulfilled
- Rejected

With Promise Objects in JavaScript, we are given `.then()` and `.catch()` methods. These are super helpful because they allow us to execute the next piece of code depending on if the previous code was successful, or if it had returned an error. 

`.then()` Is called when the task completes and returns the result of the task.

`.catch()` Is called when something goes wrong with our task and will return an error so we can interpret what has gone wrong.

Promises are helpful when we need to call data from an API, but we might have to wait for that data to be returned. 

### **Code Example**

```jsx
const myBriePromise = new Promise((myResolve, myReject) => {
  let x = 0;

  if (x == 0) {
    myResolve("OK");
  } else {
    myReject("Error");
  }
});

myBriePromise
.then((value) => {console.log(value, 'hooray, brie 😆')})
.catch((error) => {console.error(error, 'no brie 😭')});
```

### Fetch

A method that we get with JavaScript that returns a promise is the `fetch` method. This is a method we can use to fetch data via an api. 

### **Code Example**

```jsx
fetch('http://example.com/movies.json')
  .then((response) => response.json())
  .then((data) => console.log(data))
	.catch((err) => console.error(err));
```

## Async / Await

We also have these handy keywords in JavaScript `async` and `await`. These are newer features of JavaScript **ES6** and help us streamline our asynchronous code.

When we add this in front of a function, it makes the function return a promise. Alongside the `async` keyword, we also use the `await` keyword which is used to wait for a promise. This makes our code easier to read. You can only use the await inside functions with the async keyword.

Alongside `async` and `await` we can use the `try` `catch` block in order to catch errors. 

### **Code Example**

```jsx
const fetchData = async () => {
	try {
		const res = await fetch('http://example.com/movies.json');
		const data = await res.json();
	} catch(err) {
		console.log(err);
	} 
};
```

## The Bottomline

JavaScript runs asynchronously, which is super helpful when we need to wait for a piece of code to run. ES6 allowed us to write more readable code with the use of methods such as `async` and `await`, and we have moved away from the use of callbacks to execute asynchronous code. In order to handle any errors it’s also important to use the `try` `catch` block.