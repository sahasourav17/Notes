# Express JS

## [Documentation](https://expressjs.com/en/4x/api.html#express)

## Summary:

- Introduced in 2010 and backed by IBM
- A framework of NodeJS
- Provides better maintainability
- Good documentation
- Simple, lightweight, focused on backend

## Important Concepts:

- Middleware

## Raw NodeJS vs ExpressJS:

[NodeJS]

```js
const http = require("http");

const server = http.createServer((req, res) => {
  if (req.url == "/") {
    res.write("Welcome this is your home page");
    res.end();
  } else if (req.url == "/about" && req.method == "GET") {
    res.write("Welcome this is your about page");
    res.end();
  } else {
    res.write("Not found");
    res.end();
  }
});

server.listen(3000);
console.log("Listen on http://localhost:3000");
```

[ExpressJS]

```js
const express = require("express");
const app = express();

app.get("/", (req, res) => {
  res.send("This is home page");
});

app.post("/", (req, res) => {
  res.send("This is home page with post request");
});

app.get("/about", (req, res) => {
  res.send("This is about page");
});

app.listen(3000, () => {
  console.log("Listen on http://localhost:3000");
});
```

# [express() function](https://expressjs.com/en/api.html#express)

- [_express.json()_](https://expressjs.com/en/api.html#express.json)

  ```js
  app.use(express.json());
  ```

  which will return response if the request body is in json format.

  Now, if we post a request to the server

  ```
  http://localhost:3000/
  ```

  and put this json into the body of the request

  ```json
  {
    "name": "Bangladesh"
  }
  ```

  we will get the response on the terminal

  ```bash
  { name: "Bangladesh"}
  ```

- [_express.raw()_](https://expressjs.com/en/api.html#express.raw)

  ```js
  app.use(express.raw());
  ```

  After passing the same request(but in raw format) the response will be returned like this

  output:

  ```bash
  <Buffer 7b 0a 20 20 22 6e 61 6d 65 22 3a 22 42 61 6e 67 6c 61 64 65 73 68 22 0a 7d>
  ```

  Now, if we change the code like this

  ```js
  app.use(express.raw().toString());
  ```

  we will see output like this

  ```bash
  {
    "name": "Bangladesh"
  }
  ```

  This is not a json object, it's just a string

- [_express.text()_](https://expressjs.com/en/api.html#express.text)

  ```js
  app.use(express.text());
  // Content-Type: text/plain
  // pass request as form encoded
  ```

  Output:

  ```bash
  name=sourav
  ```

- [_express.urlencoded()_](https://expressjs.com/en/api.html#express.urlencoded)

- [_express.static()_](https://expressjs.com/en/api.html#express.static)

- [_express.router()_](https://expressjs.com/en/api.html#express.router)

## Tutorial link:

- [Express Js in Bangla](https://youtu.be/nwneGf7vYgY)
