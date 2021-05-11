# JavaScript versions

JavaScript was first released in Netscape Navigator, and quickly became a game changer. Competing browsers all came up with their own version of JavaScript. Microsoft for example, created their own implementation of JavaScript, JScript, for Internet Explorer. The differences between JavaScript and JScript made it difficult for designers and developers to make a website work well in multiple browsers. JavaScript got a reputation for blocking growth.

In 1996 Netscape decided to standardise JavaScript and submitted it to the standards organisation ECMA international for consideration as an industry standard. ECMAScript (ES) became the new name used to refer to versions of the language and the technical committee standardising it was known as [TC39](https://www.ecma-international.org/technical-committees/tc39/).
The TC39 Committee was (and is) made up of delegates from different companies including major browser vendors and big corporations like Netflix, Facebook, and PayPal. Its delegates represent their companies' interests for creating, approving, or denying language proposals. And in such a profit oriented and competitive market, you do not even have to wait for the shit to happen.

The first edition of ECMAScript was released in 1997. 2 and 3 soon followed. When it came time to work on ECMAScript 4 the TC39 committee could not agree on its feature set. TC39 broke up until late 2008 when it continued work and released ECMAScript 3.1, which was later renamed to ES5. After the release of ES6, alias ES2015, the TC39 Committee decided to iterate more often and consistently. It does so yearly. 

- Ronan warned it will be like "aiming for a moving target" (a constantly moving target just beyond the current snapshot specification), while learning somewhere in the middle of the trunk, so I am listing the features of the vanilla versions and some non-vanilla flavours below.
- Raphael passed on the link to a book which is very helpful. The book: https://b-ok.cc/book/855629/41fca3 (awesome book, love it)

:::info
This list is for checking off which features the project uses (coloured) so that we can focus on learning about those instead of everything everywhere, and to check it off when we think we have understood. A work in progress ...
:::

## ES5
  - [x] <span style="color:purple">Support for JSON.</span>
  - [x] <span style="color:purple">Getters and Setters and objects.</span>
  - [x] <span style="color:purple">Array methods like Filter, forEach, and map.</span>

## ES2015

  - [x] <span style="color:purple">Let and Const</span> to help avoid variable hoisting respectively rebinding, `const` remains writable. Writability can be controlled using `Object.defineProperty()`and `Object.freeze()`,   and have nothing to do with the binding.
  - [x] <span style="color:purple">Arrow functions and lexical this</span> for declaring closures and anonymous functions.  Arrow functions behave differently with `this`, `arguments`, `super`, and `new.target` because they inherit the values from the enclosing function.
  - [x] <span style="color:purple">Classes</span>. Prototype based OOP does not implement objects in the spirit of Simula 67, but in the spirit of Self. Classes in ES2015 are syntactic sugar for modeling classes on top of prototypes, see https://tc39.es/ecma262/#sec-runtime-semantics-classdefinitionevaluation .  In Simula's approach, classes provide a certain archetype for object instances. With prototypes, an instance fills in the gaps of a new instance by providing its own behavior. If a prototype needs more or other variables or functions for a new object, it can simply be cloned and modified without affecting all other child instances. Really nice, this.
  - [x] <span style="color:purple">Object-literal improvements</span> aid in readability and keeps blocks of code that should belong together as close as possible.
  - [x] <span style="color:purple">Template string literals</span> allow for string concatenations like with C's `sprintf`, but with a "perfect" correlation between the format string and the values passed. Remove an argument from the call and it is a bug. `String.raw` for escape sequences and quoting characters. Tag functions can transform string literals in arbitrary ways and can be abused in ways that impair readability.
  - [x] <span style="color:purple">Promises</span> for preventing creating unmanageable code using events and callback functions.
    - A Promise has four states: 
      - fulfilled: Action related to the promise succeeded
      - rejected: Action related to the promise failed
      - pending: Promise is still pending i.e not fulfilled or rejected yet
      - settled: Promise has fulfilled or rejected
    - A promise can be created using Promise constructor
      - Promises can be chained inside the promise constructor

```javascript
const p = new Promise((resolve, reject) => {
    try {
        const result = action(data);
        resolve(result);
    } catch(e) {
        logger.error(e.toString());
        reject(e);
    }
});
```

Chaining two HTTP requests together into a single promise. Data resulting from the first request is processed and then used to construct the second request. All errors are handled internally by the promise logic:
    
```javascript
const p = new Promise((resolve, reject) => {
    try {
        const result = action(data);
        resolve(result);
    } catch(e) {
        logger.error(e.toString());
        reject(e);
    }
});
```
    
  - [x] <span style="color:purple">Generators, iterators, iterables and for...of</span>
  
Generators were added to make it easier to bring the concept of iterators into the language.  JavaScript generators are like coroutines.

```javascript
function* counter() {
    let i = 0;
    while(true) {
        yield i++;
    }
}
```
The asterisk right beside the `function` declares a generator. Use of the `yield` keyword signals the interpreter to temporarily halt the execution of the generator and return the value passed to it. In this case, `yield` will return whatever value is in `i`. Repeated calls to the generator will resume execution from the point of the last yield, preserving all states.

Iterators in JavaScript are nothing more than a protocol, that is, an API for creating objects that can be used to iterate over iterables. 

```javascript
function arrayIterator(array) {
    var i = 0;
    return {
        next: function() {
            return i < array.length ? {
                value: array[i++],
                done: false
            } : {
                done: true
            };
        }
    }
}
```

The `arrayIterator` function describes the protocol required by JavaScript iterators.

  - An iterator is an object that:
    - Contains a `next` function taking no arguments.
    - The `next` function returns an object containing either one or two members. If the member `done` is true, then no other member is present. `done` flags whether iteration has completed. The other member shall be `value` and represent the current iteration value.
    
Using `yield` the code becomes simpler, and much easier to read and understand:

```javascript
function* arrayIterator(array) {
    for(let i = 0; i < array.length; ++i) {
        yield array[i];
    }
}
```

Usually collections are iterated over. Iterables are objects that provide an interface to construct iterators with. Iterables are objects that provide a key:

```javascript
const infiniteSequence = {
    value: 0
    [Symbol.iterator]: function* () {
        while(true) {
            yield value++; 
        }
    }
};
```

  -  Symbols are a way to create unique identifiers (symbols) that can be used to index other objects.
  - `[Symbol.iterator]` is used inside an object literal to set its key. 
  - Making iterables objects that provide a `Symbol.iterator` key whose value is a generator function.
  

All iterable objects can be easily iterated over with the use of the `for..of` loop:


```javascript
const array = [1, 2, 3, 4];
const map = new Map([['key1', 1], 
                     ['key2', 2], 
                     ['key3', 3]]);

for(let element of array) {
    console.log(element);
}

for(let [key, value] of map) {
    console.log(`${key}: ${value}`);
}
```

The use of `let [key, value]` in the last `for..of` loop is called destructuring.


  - [x] <span style="color:purple">Functions: Default Arguments and the Rest Operator</span>
  - [x] <span style="color:purple">Spread Syntax</span>
  - [x] <span style="color:purple">Destructuring</span>
  - [x] <span style="color:purple">Modules (see https://javascript.info/modules-intro)</span>
  - [x] <span style="color:purple">Collections</span>
  - [x] <span style="color:purple">Object Proxies</span>
  - [x] <span style="color:purple">Reflection</span>
  - [x] <span style="color:purple">Symbols</span>
  - [x] <span style="color:purple">Typed Arrays</span>
  - [x] <span style="color:purple">And a whole bunch of minor features such as Subclassing Built-ins, Guaranteed Tail-call Optimization, Unicode and Binary and octal literals.</span>

## ES2016
  - Array.prototype.includes
  - The exponentiation operator

## ES2017
  - Object.values/Object.entries
  - String padding
  - Object.getOwnPropertyDescriptors
  - Trailing commas in function parameter lists and calls
  - Async functions
  - Shared memory and atomics

## ES2018
  - Lifting template literal restriction.
  - s (dotAll) flag for regular expressions.
  - Regexp named capture groups.
  - Rest/spread properties.
  - Regexp lookbehind assertions.
  - Regexp Unicode property escapes.
  - Promise.prototype.finally.
  - Asynchronous iteration.

## ES2019
  - Array#{flat,flatMap}.
  - Object.fromEntries.
  - String#{trimStart,trimEnd}.
  - Symbol#description.
  - try { } catch {}. // optional binding
  - JSON ⊂ ECMAScript.
  - well-formed JSON.stringify.
  - stable Array#sort.
  - revised Function#toString.
  - BigInt primitive type (stage 3).
  - Dynamic import (stage 3).
  - Standardized globalThis object (stage 3).

## ES2020
  - String.prototype.matchAll
  - import()
  - BigInt
  - Promise.allSettled
  - globalThis
  - for-in mechanics
  - Optional Chaining
  - Nullish coalescing Operator

## ES2021
  - String.prototype.replaceAll
  - Promise.any
  - WeakRef
  - Logical Assignment Operators
  - Numeric separators

## ESNext

Not yet released standard. A dynamic name that refers to whatever the next version is at time of writing. Proposals to the next ECMAScript standard are organised in stages. Stages 1–3 are an incubator of new features, and features reaching Stage 4 are finalised as part of the new standard: https://github.com/tc39/proposals/blob/master/finished-proposals.md


## Non-vanilla branches

- TypeScript (Microsoft), a layer around JavaScript that contains extra features and syntax https://www.typescriptlang.org/
- Flow (Facebook), an open source type checking library https://flow.org/
- CoffeeScript https://coffeescript.org/
- Dart https://dart.dev/
- WebAssembly (Wasm) https://webassembly.org/

