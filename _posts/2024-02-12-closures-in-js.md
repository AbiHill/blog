---
title: "JavaScript Closures"
date: 2024-02-12
---

Javascript powers much of what we see on the web. Among its many features, Closures stand out as one of its most powerful concepts. Closures are like secret weapons that help us understand some important coding tricks and best practices in JavaScript. They're building blocks for creating strong, secure and reliable code. In this article I will discuss what a closure is, when they are used and what to consider.

## What is a Closure?

A closure is a combination of functions. To understand closures in the most simplistic format you can imagine you have a small function inside another function. As part of that setup, the (inner) function can remember and access its lexical scope even when that function is executing outside of that scope. 

So, what is Lexical Scope? Lexical scope is when a function can reach out and access variables from its surrounding or parent scope.

### Closure Example

```jsx
const firstImpressions = () => {
	let name = 'Dave'
	let age = 35

	const sayHello = () => {
		console.log('Hello ' + name)
	}

	return {
		sayHello
	}
}

const bePolite = firstImpressions()

bePolite.sayHello()
```

```jsx
HelloDave // log
```

## When are closures used?

Closures are used to achieve encapsulation in JavaScript. Encapsulation in JavaScript is like putting your code in a safety circle, to protect it from unintentional external amends and prevent naming clashes. Usually, an object is used to bundle data and methods together. 

## Things to Consider

Something to consider whilst working with Closures is that due to their ability to hold the memory of the parent scope, this means that some unused variables never get cleaned up and memory leaks can occur. To avoid this you should consider if they are truly necessary and use them sparingly.

## In Summary

Once you wrap your head around Closures and how to use them, you'll unleash the full potential of JavaScript and create code that's super easy to maintain. But be sure to be careful when working with closures to steer clear of any memory leaks.
