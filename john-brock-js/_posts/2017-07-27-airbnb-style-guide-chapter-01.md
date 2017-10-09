---
layout: post
blog: john-brock-js
title: "ELI50: Airbnb JavaScript Style Guide Chapter 1: Types"
permalink: "/john-brock-js/airbnb-styleguide-chapter-1"
comments: true
---
[Airbnb][airbnb], the online marketplace for housing rentals, has a high quality and 'mostly reasonable' style guide for JavaScript, a programming language that adds dynamic behaviors to web browsers. Some of the topics in the guide are a bit advanced for beginners. This "Explain Like I'm 50" (ELI50) series will act as a plain English companion-guide to the [Airbnb style guide][style guide], because good design principles shouldn't be out of anyone's reach.

Each post will cover a chapter of the style guide and will explain terminology, techniques and the reason behind the rules.

> # What the heck is ESLint and JSCS?
Periodically in the guide you'll see links labeled with either ESLint and JSCS. These are two popular **linting programs**, which check your for errors, style mistakes, and bad practices in your code. I go deeper into them in a soon to be released john-brock.js post but suffice it to say that if you're doing anything more than trivial programming you should be using a linter. For JavaScript I would recommend [ESLint][eslint].

<br>
## Chapter 1: Types
### [1.1][1.1] **Primitives**: When you access a primitive type you work directly on its value.

In JavaScript a data type is a way of storing information. A primitive type is the most basic form of this.
* **`string:`** Essentially text. Some other languages have a **data type** for individual characters and then another type for **strings** of characters. JavaScript forgoes this and just has strings.
* **`number:`** Many other languages have different data types for numbers to handle integers, large numbers, or numbers with decimals. JavaScript has only one type of number, the 64 bit floating point number. To learn more about it read this [w3schools][js numbers] guide on JavaScript Numbers.
* **`boolean:`** A boolean can only hold a value of either **True** or **False**.
* **`undefined:`** When you **declare** a variable without an initial value it is given a temporary placeholder value of **undefined**.
* **`null:`** When you declare a **pointer** without pointing it anywhere it's given the value **null** as a temporary placeholder.
* **`symbol:`** A new primitive that was added in the latest release of JavaScript (ES6) which you can read more about from this [Keith Cirkel article][symbols].

> # What the heck is a pointer?
Think of a pointer like a house address. Instead of building an all new house, which can be expensive, I give you the address to the original. Now if you want to use the kitchen, read the books in the study, or use other functions of the house you can. However, if someone makes a change, then everyone who has that address will see them. If we make a copy of the house instead (with a different address) we could change one without the other being affected.


### [1.2][1.2] **Complex**: When you access a complex type you work on a reference to its value.
># What the heck is a reference?
When you work with any of the following types you are working with reference to their values. This is often indistinguishable from working with their values directly but trouble can arises when you try to make a copies. Remember the house analogy from earlier? If you try to make a copy like this:
```javascript
let copyHouse = myHouse;
```
you aren't creating a whole new house like you might expect. Instead you are just giving the 'address' from before another name. Now, if you try to add a room to `copyHouse` it will be in `myHouse` too because they're the same house.


* **`object:`** An object is a data type that contains information and **methods** for accessing that information. 
* **`array:`** An array is a numbered list. In JavaScript, as well as most other languages, arrays are 0 **indexed** meaning that the first object in an array has the number 0 instead of the number 1. 
* **`function:`** A function is a way of storing instructions for the computer.

<br>
### Why Should I Care?
It's important to have a clear understanding of how you access values with primitive and complex types. Say I have two variables and I set one equal to the other. If they are both **primitives** and I later change one of them then the other doesn't change. The two variables aren't linked in any way.

On the other hand if the first variable was an **array**, a complex type, and I set my second variable equal to the first, JavaScript doesn't make a copy of the array. Instead it uses a **pointer** as we discussed earlier to point to the place in **memory** that the array exists in. Now if I change the value in one of the variables, since they are both looking at the same place in memory, they both will have their values changed.

This is an important concept to grasp because it's often the cause of **strange behavior** in complex programs.

<br>
### Next Up: References

Next Saturday I'll explain why you should avoid using `var` to declare variables.

If you enjoyed this post, have a criticism or just want to say hi, leave a post in the comments section.



[style guide]: https://github.com/airbnb/javascript#types--primitives
[airbnb]: https://www.airbnb.com/
[eslint]: http://eslint.org/

[1.1]: https://github.com/airbnb/javascript#types--primitives
[1.2]: https://github.com/airbnb/javascript#types--complex

[js numbers]: https://www.w3schools.com/js/js_numbers.asp
[symbols]: https://www.keithcirkel.co.uk/metaprogramming-in-es6-symbols/