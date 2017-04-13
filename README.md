# eslint v1.10 shareable configs test

[![Greenkeeper badge](https://badges.greenkeeper.io/iamstarkov/eslint-test.svg)](https://greenkeeper.io/)

tldr: it’s working! [issue](https://github.com/eslint/eslint/issues/4263)

* [eslint-config-in](https://github.com/iamstarkov/eslint-config-in)
* [eslint-config-out](https://github.com/iamstarkov/eslint-config-out)
* [eslint-test lint result](https://travis-ci.org/iamstarkov/eslint-test)

```sh
➜  eslint-test git:(master) ✗ cat node_modules/eslint-config-in/package.json | grep dep
  "dependencies": {},
➜  eslint-test git:(master) ✗ cat node_modules/eslint-config-in/.eslintrc.js
module.exports = {
  rules: {
    indent: [2, 2]
  }
}

➜  eslint-test git:(master) ✗ cat node_modules/eslint-config-out/package.json | grep "\"eslint-config-in\":"
    "eslint-config-in": "github:iamstarkov/eslint-config-in"
➜  eslint-test git:(master) ✗ cat node_modules/eslint-config-out/.eslintrc.js
module.exports = {
  extends: 'in',
  rules: {
   quotes: [2, 'single']
  }
}

➜  eslint-test git:(master) ✗ cat package.json | grep eslint-config
    "eslint-config-out": "github:iamstarkov/eslint-config-out"
➜  eslint-test git:(master) ✗ cat .eslintrc.js
module.exports = {
  extends: 'out'
}

➜  eslint-test git:(master) ✗ cat index.js
function test() {
    return "yo";
}

➜  eslint-test git:(master) ✗ ./node_modules/.bin/eslint .
/Users/iamstarkov/projects/eslint-test/index.js
  2:5   error  Expected indentation of 2 space characters but found 4  indent
  2:12  error  Strings must use singlequote                            quotes
✖ 2 problems (2 errors, 0 warnings)
