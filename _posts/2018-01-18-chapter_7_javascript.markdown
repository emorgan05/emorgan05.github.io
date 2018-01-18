---
layout: post
title:      "Chapter 7: JavaScript"
date:       2018-01-18 16:25:39 +0000
permalink:  chapter_7_javascript
---


I went through the lessons on loops, and then found myself tripping over which one to choose when in the next several labs. So I've written a guide for myself on Looping and Filter/Map functions. 

**Looping options **

**for **

With a for loop, you set a counter (which is just a random variable like i that can start at any number, often 0). After setting the counter, you set a condition. It needs to be a condition that is true for the counter at the start. Then you increment the counter.

`for (let i = 0; i < 10; i++)`

With our counter at 0, the condition currently evaluated as true, so the code block will run until the condition is false. 

Example:
```
for (let i = 0; i < 10; i++) {
    console.log(“Hello World!”);
}
// LOG: “Hello World!” 10 times
```

Uses:
Useful for any situation where you want to repeat a block of code multiple times. 
You can use it for iterating through the elements in an array. 


**while**

A while loop is very similar to a for loop. You will execute the code while the condition is true. 

Example:
```
let num = 0;
while (num < 3) {
    console.log(num += 1)
}
// LOG: 1 2 3
```

Uses: 
Again repeat a block of code multiple times. 
Note: With loops, be careful of infinite loops. The condition eventually has to evaluate to true or false depending on which loop you are using. 


**for … of**

This loops over iterable objects -- like strings and arrays. You can set up a variable for each element in an array, and then execute a code block on each element.

Example:
```
let array = [1, 2, 3, 4, 5];
for (let num of array) {
    num += 2;
    console.log(num);
}
// LOG: 3, 4, 5, 6, 7
```


**for … in**

This loops over the enumerable properties of iterable items. Which means it loops over properties. The best use is for objects -- you can use it to get the values from the object. Using it on an array returns the indexes of the array, and is not the best use because of problems with order. If you want to iterate over an array, use for...of or for

Example: 
```
let object1 = { a: 1, b: 2, c: 3 }
for (let property in object1) {
    console.log(object1[property])
}
// LOG: 1, 2, 3
```

**********
**Array methods**

**filter()**

Call filter on an array and pass in a function. The function is the test for each element of the array. Filter will create a new array with each element that passes the test. 

The passed-in function is called a callback function. You can define it outside of the filter call, and then just invoke it by name. 

The callback function can take as many as three arguments -- the element, the index, and the array. 

Example:
```
var words = ['spray', 'limit', 'elite', 'exuberant', 'destruction', 'present'];
const result = words.filter(word => word.length > 6);
console.log(result);
// LOG: [‘exuberant’, ‘destruction’, ‘present’]
```

Note:
`word => word.length > 6`
Is an arrow function. Word is the passed in argument (the element in the array). 
`word.length > 6` is the test
If the result is true, the word will go into the result array

Instead of writing an arrow function, you could write it as 
`const result = words.filter(function (word) { return word.length > 6 });`


**map()**

Like filter, you call map() on an array and pass in a callback function. The callback function is executed once for each element and will do something to each element of the array. Map will create a new array with the results of the callback function. 

Map works the same as filter -- you can define the function outside of the call, and you can set as many as three arguments in the callback function, and map can take an argument for ‘this’.

Example:
```
var array1 = [1, 4, 9, 16];
const map1 = array1.map(x => x * 2);
console.log(map1);
// LOG: Array [2, 8, 18, 32]
```

Note:
Like with filter(), that example is an arrow function. 
If could be written as
`const map1 = array1.map(function(x) { return x * 2 });`

