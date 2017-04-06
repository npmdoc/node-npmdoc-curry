# api documentation for  [curry (v1.2.0)](https://github.com/dominictarr/curry)  [![npm package](https://img.shields.io/npm/v/npmdoc-curry.svg?style=flat-square)](https://www.npmjs.org/package/npmdoc-curry) [![travis-ci.org build-status](https://api.travis-ci.org/npmdoc/node-npmdoc-curry.svg)](https://travis-ci.org/npmdoc/node-npmdoc-curry)
#### flexible but simple curry function

[![NPM](https://nodei.co/npm/curry.png?downloads=true)](https://www.npmjs.com/package/curry)

[![apidoc](https://npmdoc.github.io/node-npmdoc-curry/build/screenCapture.buildNpmdoc.browser._2Fhome_2Ftravis_2Fbuild_2Fnpmdoc_2Fnode-npmdoc-curry_2Ftmp_2Fbuild_2Fapidoc.html.png)](https://npmdoc.github.io/node-npmdoc-curry/build/apidoc.html)

![npmPackageListing](https://npmdoc.github.io/node-npmdoc-curry/build/screenCapture.npmPackageListing.svg)

![npmPackageDependencyTree](https://npmdoc.github.io/node-npmdoc-curry/build/screenCapture.npmPackageDependencyTree.svg)



# package.json

```json

{
    "author": {
        "name": "Dominic Tarr",
        "email": "dominic.tarr@gmail.com"
    },
    "bugs": {
        "url": "https://github.com/dominictarr/curry/issues"
    },
    "contributors": [
        {
            "name": "Hugh FD Jackson",
            "email": "hughfdjackson@googlemail.com"
        }
    ],
    "dependencies": {},
    "description": "flexible but simple curry function",
    "devDependencies": {
        "browserify": "2.17.2",
        "delve": "0.3.2",
        "lodash": "2.1.0",
        "mocha": "1.8.1",
        "uglify-js": "2.3.6"
    },
    "directories": {},
    "dist": {
        "shasum": "9e6dd289548dba7e653d5ae3fe903fe7dfb33af2",
        "tarball": "https://registry.npmjs.org/curry/-/curry-1.2.0.tgz"
    },
    "homepage": "https://github.com/dominictarr/curry",
    "main": "./curry",
    "maintainers": [
        {
            "name": "dominictarr",
            "email": "dominic.tarr@gmail.com"
        },
        {
            "name": "hughfdjackson",
            "email": "hughfdjackson@googlemail.com"
        }
    ],
    "name": "curry",
    "optionalDependencies": {},
    "readme": "ERROR: No README data found!",
    "repository": {
        "type": "git",
        "url": "git://github.com/dominictarr/curry.git"
    },
    "scripts": {
        "prepublish": "./node_modules/browserify/bin/cmd.js --standalone curry -e curry.js | ./node_modules/uglify-js/bin/uglifyjs > curry.min.js",
        "test": "./node_modules/mocha/bin/mocha test"
    },
    "testling": {
        "files": "test/*-test.js",
        "browsers": [
            "iexplore/6.0",
            "iexplore/7.0",
            "iexplore/8.0",
            "iexplore/9.0",
            "iexplore/10.0",
            "chrome/4.0",
            "chrome/23.0",
            "firefox/3.0",
            "firefox/17.0",
            "safari/5.0.5",
            "safari/5.1"
        ],
        "harness": "mocha"
    },
    "version": "1.2.0"
}
```



# <a name="apidoc.tableOfContents"></a>[table of contents](#apidoc.tableOfContents)

#### [module curry](#apidoc.module.curry)
1.  [function <span class="apidocSignatureSpan">curry.</span>adapt (fn)](#apidoc.element.curry.adapt)
1.  [function <span class="apidocSignatureSpan">curry.</span>adaptTo (a, b)](#apidoc.element.curry.adaptTo)
1.  [function <span class="apidocSignatureSpan">curry.</span>to (a, b)](#apidoc.element.curry.to)



# <a name="apidoc.module.curry"></a>[module curry](#apidoc.module.curry)

#### <a name="apidoc.element.curry.adapt"></a>[function <span class="apidocSignatureSpan">curry.</span>adapt (fn)](#apidoc.element.curry.adapt)
- description and source-code
```javascript
adapt = function (fn){
    return curry.adaptTo(fn.length, fn)
}
```
- example usage
```shell
...
It's a (sad?) fact that JavaScript functions are often written to take the 'context' object as the first argument.

With curried functions, of course, we want it to be the last object.  'curry.adapt' shifts the context to the last argument,
to give us a hand with this:

'''javascript
var delve = require('delve');
var delveC = curry.adapt(delve);

var getDataFromResponse = delveC('response.body.data');
getDataFromResponse({ response: { body: { data: { x: 2 }} } }); //= { x: 2 }
'''

### curry.adaptTo
...
```

#### <a name="apidoc.element.curry.adaptTo"></a>[function <span class="apidocSignatureSpan">curry.</span>adaptTo (a, b)](#apidoc.element.curry.adaptTo)
- description and source-code
```javascript
adaptTo = function (a, b){ return processInvocation(fn, concatArgs(args, arguments), totalArity) }
```
- example usage
```shell
...

### curry.adaptTo

Like 'curry.adapt', but the arity explicitly provided:

'''javascript
var _ = require('lodash');
var map = curry.adaptTo(2, _.map);
var mapInc = map(function(a){ return a + 1 })

mapInc([1, 2, 3]) //= [2, 3, 4]
'''

# installation
...
```

#### <a name="apidoc.element.curry.to"></a>[function <span class="apidocSignatureSpan">curry.</span>to (a, b)](#apidoc.element.curry.to)
- description and source-code
```javascript
to = function (a, b){ return processInvocation(fn, concatArgs(args, arguments), totalArity) }
```
- example usage
```shell
...

'''javascript
var sum = function(){
	var nums = [].slice.call(arguments);
	return nums.reduce(function(a, b){ return a + b });
}

var sum3 = curry.to(3, sum);
var sum4 = curry.to(4, sum);

sum3(1, 2)(3) //= 6
sum4(1)(2)(3, 4) //= 10
'''

### curry.adapt
...
```



# misc
- this document was created with [utility2](https://github.com/kaizhu256/node-utility2)
