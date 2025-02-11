

## Topics covered

- Functions as values
- Intro to anonymous functions
- Function calling vs passing (reference to a function)
- Callback functions and Higher Order functions
  - Why they exist
  - Implementing our own `forEach` and/or our own `filter`
- Arrow Functions (and their common use for callback functions)
- Nested scope and "scope chain"

## Teacher Notes

> #### Danger
> Do NOT talk about asynchronous control flow. 
> Many people conflate callbacks and asynchronous control flow. While callbacks are often used in async functions, they are also needed/used for many sync functions such as `Array.map`. 

Students get into async logic in Week 2 so we can consider it out of scope for now.

#### Functions as callbacks

Talk about callbacks and functions that take callbacks.

An example narrative of taking code that does two things, and splitting it into two single-purpose functions.

```javascript
const array = [1, 2, 3];
for (const item of items) {
  console.log(item);
};

// can be rewritten as:

const logEach = function(items) {
  for (const item of items) {
    console.log(item);
  }
};

// but if we want something more abstract and single-purpose

const forEach = function(items, action) {
  for (const item of items) {
    action(item);
  }
};
```

`forEach` is therefore a Higher-Order function. Talk about how Array has forEach built in which does exactly that.

> #### Instruction
> Mention to students that while it's nice to be able to label things, remembering keywords / buzz words like "Higher-Order Function" is not the most important part.

#### Arrow Functions

Today students get introduced to Arrow functions. Feel free to introduce and use them part way through lecture.

#### Exercise (live-code)

Live code a `forEachInReverse` that does reverse iteration on an array and takes a cb much like forEach would.

```javascript
const forEachInReverse = function(items, func) {
  for (let i = items.length - 1; i >= 0; i--) {
    func(items[i]);
  }
};

forEachInReverse(['hello', 'Lighthouse Labs', 'and', 'world'], (word) => {
  console.log(word);
});
```

Once implemented, add a second parameter to the callback to support index passing (`i`).

```javascript
const forEachInReverse = function(items, func) {
  for (let i = items.length - 1; i >= 0; i--) {
    func(items[i], i);
  }
};

forEachInReverse(['hello', 'lighthouse labs', 'and', 'world'], (word, index) => {
  console.log(`The word at index ${index} is "${word}"`);
});
```

*Important scope review:* talk about the two different `i` vars there. Change one of them to demo how they don't need to be the same variable name.

> #### Question
> Why write Higher-order functions? What's the rationale?

Important to explain and emphasize _Single Responsibility Principle_:

These two functions (the callback vs the higher-order function) now each have a single, more concise responsibility, instead of doing both things. _This is the most important reason for creating HO functions_.

A function should have a sole reason to exist, and delegate other responsibilities to other functions as needed.

#### Scope chain (nested scope)

Technical definition (taken from [this popular resource](http://ryanmorr.com/understanding-scope-and-context-in-javascript/)):

> To put it simply, each time you attempt to access a variable within a function’s execution context, the look-up process will always begin with its own variable object. If the identifier is not found in the variable object, the search continues into the scope chain. It will climb up the scope chain examining the variable object of every execution context looking for a match to the variable name.

The example there is good enough. Roll with it or roll your own.

**TIP:** Tech jargon isn't the main focus here. Most experienced devs don't even know the difference between "Context" (`this`), "Execution Context", and "Variable Object".

#### Out Of Scope

* Closures (this used to be core, but is now stretch for today)
* Asynchronous Control Flow or Functions (like `setTimeout`, etc.)
* Arrow functions and `this` (there is mention of this today, but you don't need to emphasize it now)

