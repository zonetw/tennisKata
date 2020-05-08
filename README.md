# tennisKata
## setup
use jest follow this introduction: https://jestjs.io/docs/en/getting-started
### install jest
```
yarn add --dev jest
jest init
```
### install babel
```
yarn add --dev babel-jest @babel/core @babel/preset-env
```
### lesson learned
#### Jest will set process.env.NODE_ENV to 'test'
if it's not set to something else. You can use that in your configuration to conditionally setup only the compilation needed for Jest, e.g.
```
// babel.config.js
module.exports = api => {
  const isTest = api.env('test');
  // You can use isTest to determine what presets and plugins to use.

  return {
    // ...
  };
};
```
#### babel-jest is automatically installed when installing Jest 
and will automatically transform files if a babel configuration exists in your project. To avoid this behavior, you can explicitly reset the transform configuration option:
```
// jest.config.js
module.exports = {
transform: {},
};
```

#### babel/preset-env
https://babeljs.io/docs/en/babel-preset-env

Q: Why need babel/preset-env ?
help distinguish which part need to be transformed according to the target env

Q: How to setup node as target ?

targets.node
string | "current" | true.
If you want to compile against the current node version, you can specify "node": true or "node": "current", which would be the same as "node": process.versions.node.
