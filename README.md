[![NPM Downloads](https://img.shields.io/npm/dm/logger-express)](https://www.npmjs.com/package/logger-express)

# logger-express

A simple logger for Node and Express.

## Installation

To install the package, execute the following command:

``````
npm install logger-express
``````

## Usage

To use the logger, import the package into your code:

```
import { logger } from "logger-express";
```

```
const loggerOption = {
  logToFile: true, // If you need to log information to a file
  colorize: true, // enable console colors
  infoColor: "magenta", // set a color for information messages
  errorColor: "red", // set a color for error messages:
};
```

Finally, add the logger middleware to your application:

```
app.use(logger(loggerOption));
```

## Options

The logger has the following options:

 🗃️ **logToFile**: Indicates whether information should be logged to a file. The default value is true.


 🌈 **colorize**: Indicates whether console colors should be used. The default value is true.


 💡 **infoColor**: Color for information messages. The default value is magenta.


❌ **errorColor**: Color for error messages. The default value is red.

If no options are provided, the logger will use its default configuration.
## Example

The following example demonstrates how to use the logger to log the request and response information of an application:

```
import express from "express";
const { logger } = require("logger-express");

const app = express();
const loggerOption = {
  logToFile: true, // If you need to log information to a file
  colorize: true, // enable console colors
  infoColor: "magenta", // set a color for information messages
  errorColor: "red", // set a color for error messages:
};

app.use(express.json());
app.use(logger(loggerOption));

app.get("/", (req, res) => {
  res.send("Hello, world.");
});

app.listen(3000, () => {
  console.log("The application is listening on port 3000.");
});

```

When you run the application and visit the route /, the logger will record the following information in the console:

```
Started GET /api/1 for :: ::ffff:127.0.0.1 at Sat Oct 14 2023 17:32:19 GMT-0300 (Chile Summer Time)
Parameters in body: {}
```
🚨 To display the body information, you should use the express.json() middleware before the logger.

If you visit a route and an error occurs, the logger will log the following message in the console with the corresponding error code:
```
Completed: 500 message: Internal Server Error Time response: 10 ms Request ID: [34273466-07c3-470d-8099-146236c93e02]
```
On the other hand, if the query is successful, the following will be displayed:
```
Completed: 200 message:  Time response: 1 ms Request ID: [92d17d54-5a62-4618-815a-18dae2bc7b00]
```
The logger will also log information to a file if the logToFile option is set to true. The log file will be created in the logs folder and will be named with the current date, creating a new file for each day.

- Colors available:
  - black
  - red
  - green
  - yellow
  - blue
  - magenta
  - cyan
  - white
  - blackBright(alias: gray, grey)
  - redBright
  - greenBright
  - yellowBright
  - blueBright
  - magentaBright
  - cyanBright
  - whiteBright