# Getting Started

## Installation

Install from the NPM repository using yarn or npm:

```bash
$ npm i -S node-powershell
```

```bash
$ yarn add node-powershell
```


## Importing

### ES6

```javascript
import Shell from 'node-powershell'
```

### ES5 (CommonJS)

```javascript
const Shell = require('node-powershell')
```


## Quick start

```javascript
const shell = require('node-powershell');

let ps = new shell({
  executionPolicy: 'Bypass',
  noProfile: true
});

ps.addCommand('echo node-powershell')
ps.invoke()
.then(output => {
  console.log(output);
})
.catch(err => {
  console.log(err);
  ps.dispose();
});
```
## NOTE
node-powershell uses [child_process.spawn()](https://nodejs.org/api/child_process.html#child_process_child_process_spawn_command_args_options) to launch powershell. This function is not available client side, so when using node-powershell in a client-side library (Vue, Angular etc.), you will receive the following error:
```
TypeError: spawn is not a function
```
You must use node-powershell either in electron or on your server-side code.
