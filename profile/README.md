# Node Lambdas

![Node Lambdas](https://avatars0.githubusercontent.com/u/69599650?s=100&v=4)

## Introduction

`node-lambdas` is a collection of tiny Node.JS servers that implement common NPM modules or HTTP services as API's for convenience.

**Why?**

Quite often I need to do simple tasks, like formatting a JSON file or decoding a base64 string.
Sometimes I need that on my phone or in a restricted environment.

## Example

This is the simplest cloud function:
```js
export default prependWithHello(input, output) {
  input.on('data', data => output.write('Hello, ' + data));
  input.on('end', output.end());
}
```

This is an example of a cloud function with different input and output:
```js
export default {
  input: 'text',
  output: 'json',
  handler: function(input, output) {
    // input.body is a string
    // output.send() should be called with an object
  }
};
```

This cloud function has different actions
```js
import { encode, decode } from './base64.js';
export default {
  version: 2,
  actions: {
    encode: {
      input: 'text',
      output: 'text',
      handler: function toBase64(input, output) {
        output.send(encode(input.body));
      }
    },
    decode: {
      input: 'text',
      output: 'text',
      handler: function toBase64(input, output) {
        output.send(decode(input.body));
      }
    },
  }
};
```

See the full [API documentation here](https://github.com/node-lambdas/core#function-configurations).

## Using with @node-lambdas/cli

`@node-lambdas/cli` is a terminal script that pipes the input/output of your CLI commands to an HTTP server.
See the full documentation here

## Available Node.js micro services

Use `fn discover` to get a list of available services.

> Missing a function? Open an issue and [request a new one](https://github.com/node-lambdas/discover/issues).

