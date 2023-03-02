# TypeScript

## Why we need TypeScript?

As javascript is a dynamic typed language, it has no built-in data types. For this we can assign multiple data types to the same variable which further arises problems. That's why we need TypeScript. TypeScript allows us to use data types in javascript. In TypeScript once you assign a value to a variable of any type, you can't assign a value of any other data type to that variable.

```typescript
let counter: number = 9;
counter = "Hello World";
```

This will throw an error like this:
`Type 'string' is not assignable to type 'number'.`

## Installation

```bash
npm install typescript --save-dev
npx tsc --init
npx tsc
```

## Contents:

<details open>
<summary>TypeScript Basics</summary>
<br>
<ul>
    <li> Basic types </li>
    <li> Tuple and enum </li>
    <li> Function </li>
    <li> Class </li>
    <li> Common Error </li>
</ul>
</details>

<details open>
<summary>TypeScript Advanced</summary>
<br>
<ul>
    <li> Interface </li>
    <li> Namespace </li>
    <li> Module </li>
    <li> Decorators </li>
    <li> Generics </li>
</ul>
</details>

### TypeScript Data Type

As TypeScript is a superset of JavaScript, it inherits all the built in data of JavaScript and also includes some additional data types. They can be divided into:

<details open>
<summary> Primitive types </summary>
<br>
<ul>
  <li> Boolean </li>
  <li> Number </li>
  <li> String </li>
  <li> Null </li>
  <li> Undefined </li>
  <li> Void </li>
  <li> Any </li>
</ul>
</details>

<details open>
<summary> Non-Primitive types </summary>
<br>
<ul>
  <li> Array </li>
  <li> Class </li>
  <li> Function </li>
  <li> Tuple </li>
  <li> Interface </li>
  <li> Enum </li>
  <li> Generic </li>
  <li> Decorators </li>
</ul>
</details>
