## Contents

- [Concept of Debounce](#Debounce)
- [Concept of Higher Order Function](#Higher-Order-Function)

- [Concept of Memoization](#Memoization)

# Debounce

Suppose, we have a button on our webpage let's say a user accidentally clicked `add to cart` button of one item multiple times, the expected behavior should be the item will be added to the cart for the first time but not added how many times the button is clicked. Here, comes the concept of debounce. Which ensure that if a user clicked on a button rapidly, it will work only for once.

Let's look another use case of debounce, If we want to search something on our ecommerce website, it will make a network request for every typed character which will later ended up with large amount of request to the server. In that case, we can use Debounce.

```js
const button = document.getElementById("button");

// debounce handler
function debounce(fn, delay) {
  let timeoutId;
  return function () {
    if (timeoutId) {
      clearTimeout(timeoutId);
    }

    timeoutId = setTimeout(() => {
      fn();
    }, delay);
  };
}

button.addEventListener(
  "click",
  debounce(function () {
    console.log(`clicked`);
  }, 200)
);
```

**_Note:_** Here, our `debounce` function, we have to return a function since `addEventListener` function accepts a function in it's second parameter.

# Higher-Order-Function

Higher Order Function is a function which

- Recieves another function as a parameter or
- Return a function or
- Receive a function as parameter and also return fucntion

```js
const HOF = (func) => {
  return function () {
    func();
  };
};
```

Full example:

```js
function add(x) {
  return 10 + x;
}

const HOF = (func) => {
  return function (x) {
    const res = func(x);
    return res;
  };
};

const calc = HOF(add);
console.log(calc(2)); // output: 12
```

# Memoization

In times of high calculation or network call which could be cpu or memory hungry, memoization provides a solution. Like in the below example if we didn't use memoization, it will call the `add` function everytime it calls and calculate the result which is not the case when we use memoization, if the result was previously calculated, rather than performing the same operation again it will return the memoized result.

- Used for performance optimization

To get clear idea about `Memoization` we need to first clear the concept of `Higher Order Function (HOF)` and `Closure`.

**_Code Example_**

```js
function add(x) {
  return 10 + x;
}

// higher order function
const memo = (func) => {
  let cache = {}; // concept of closure
  return function (x) {
    if (cache[x]) {
      console.log("result from cache");
      return cache[x];
    } else {
      console.log("calculating result");
      const result = func(x);
      cache[x] = result;
      return result;
    }
  };
};

const calculate = memo(add);

console.log(calculate(12));
console.log(calculate(12));
```

**_Output_**

```
calculating result
22
result from cache
22
```

Now, if we have unlimited number of argument without a single value of `x` like the above example and we want to find the sum of all elements in `x` then the modified code will be like below:

- need to know the `rest` concept

```js
function add(...x) {
  return x.reduce((sum, currentVal) => sum + currentVal);
}

const memo = (func) => {
  let cache = {}; // concept of closure
  return function (...x) {
    console.log("cache status:", cache);
    const key = JSON.stringify(x);
    if (cache[key]) {
      console.log("result from cache");
      return cache[key];
    } else {
      console.log("calculating result");
      const result = func(...x);
      cache[key] = result;
      return result;
    }
  };
};

const calculate = memo(add);

console.log(calculate(10, 20, 30, 40, 50));
console.log(calculate(10, 20, 30, 40, 50));
```

**_Output_**

```
cache status: {}
calculating result
150
cache status: { '[10,20,30,40,50]': 150 }
result from cache
150
```
