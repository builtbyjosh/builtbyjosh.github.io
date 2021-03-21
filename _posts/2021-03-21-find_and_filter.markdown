---
layout: post
title:      "Find & Filter"
date:       2021-03-21 05:07:12 +0000
permalink:  find_and_filter
---



In my most recent project at Flatiron School, I had to create a single page application that use HTML, CSS, and JavaScript for the front end, and a Rails API backend. One of the challenges I faced was translating what I knew how to do in Ruby, to JavaScript. Mostly logical operators. The two operators that I used in my SPA, were .find() and .filter(). Both are fairly easy to accomplish in Ruby, using many different methods, such as find, find_by, select. JavaScript has methods to accomplish this as well.

MDN defines .filter() as:
> The filter() method creates a new array with all elements that pass the test implemented by the provided function.

This means that you can iterate through an array and pull out any data that returns a truthy value to the parameters you program. Which is great for returning multiple values. The example that is given in the learnco curriculum is:

```
let even = arr.filter(n => {
  return n % 2 === 0;
});
```
This will iterate through an array called arr and return every number that is even in an array called even. Fairly straightforward. But this can also take in more information as well as iterate over objects. In my project, I created a function that would iterate over a Cigar collection and return all cigars whose style matched the html element that was clicked.
```
const findStyleCigars = function(obj){
    const list =  Cigar.all_items.filter ( i => i.styleName() == obj.textContent)
    renderStyleList(list, obj)
}
```

This allowed me to generate a list of cigars that matched a certain style. And with event listeners, I was able to implement this on each of the intended HTML elements. So on the style page, a user could click any style and see a list of cigars that had that same style. Within the function, I passed in the object that was clicked, ie an LI element. From there, I returned all cigars that had a style that matched the text of the LI element. 

The other logical operator I used was the .find() method. It is very common in many different programming languages. MDN defines .find() as:
>The find() method returns the value of the first element in the provided array that satisfies the provided testing function. If no values satisfy the testing function, undefined is returned.

 I used it in my app to find the saved details of each cigar. I would iterate over the saved collections of cigar objects and return the single object I was searching for.  I created a similar function to the .filter() method, but with .find() it will only return one value.

```
const findCigar = function(obj){
    return Cigar.all_items.find( function(s) { return s.name === obj.innerText })       
}
```

And just like the .filter() operator, the object that was clicked was passed in and the inner text was used to compare to the value of the name key within the object.

Logical operators like find, filter, map, and reduce are very useful methods for distilling down or finding specific information. 

