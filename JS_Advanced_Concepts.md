## Contents

- [Concept of Debounce](#Debounce)
- [Concept of Higher Order Function](#Higher-Order-Function)

- [Concept of Memoization](#Memoization)

# Debounce

Suppose, we have a button on our webpage let's say a user accidentally clicked `add to cart button` of one item multiple times, the expected behavior should be the item will be added to the cart for the first time but not added how many times the button is clicked. Here, comes the concept of debounce. Which ensure that if a user clicked on a button rapidly, it will work only for once.

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

# Memoization

To get clear idea about `Memoization` we need to first clear the concept of `Higher Order Function (HOF)`
