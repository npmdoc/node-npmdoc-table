# npmdoc-table

#### basic api documentation for  [table (v4.0.1)](https://github.com/gajus/table#readme)  [![npm package](https://img.shields.io/npm/v/npmdoc-table.svg?style=flat-square)](https://www.npmjs.org/package/npmdoc-table) [![travis-ci.org build-status](https://api.travis-ci.org/npmdoc/node-npmdoc-table.svg)](https://travis-ci.org/npmdoc/node-npmdoc-table)

#### Formats data into a string table.

[![NPM](https://nodei.co/npm/table.png?downloads=true&downloadRank=true&stars=true)](https://www.npmjs.com/package/table)

- [https://npmdoc.github.io/node-npmdoc-table/build/apidoc.html](https://npmdoc.github.io/node-npmdoc-table/build/apidoc.html)

[![apidoc](https://npmdoc.github.io/node-npmdoc-table/build/screenCapture.buildCi.browser.%252Ftmp%252Fbuild%252Fapidoc.html.png)](https://npmdoc.github.io/node-npmdoc-table/build/apidoc.html)

![npmPackageListing](https://npmdoc.github.io/node-npmdoc-table/build/screenCapture.npmPackageListing.svg)

![npmPackageDependencyTree](https://npmdoc.github.io/node-npmdoc-table/build/screenCapture.npmPackageDependencyTree.svg)



# package.json

```json

{
    "author": {
        "name": "Gajus Kuizinas",
        "url": "http://gajus.com"
    },
    "bugs": {
        "url": "https://github.com/gajus/table/issues"
    },
    "dependencies": {
        "ajv": "^4.7.0",
        "ajv-keywords": "^1.0.0",
        "chalk": "^1.1.1",
        "lodash": "^4.0.0",
        "slice-ansi": "0.0.4",
        "string-width": "^2.0.0"
    },
    "description": "Formats data into a string table.",
    "devDependencies": {
        "ajv-cli": "^1.1.0",
        "babel": "^6.5.2",
        "babel-cli": "^6.14.0",
        "babel-core": "^6.14.0",
        "babel-plugin-istanbul": "^2.0.3",
        "babel-preset-es2015-node4": "^2.1.0",
        "babel-register": "^6.14.0",
        "chai": "^3.4.1",
        "eslint": "^3.5.0",
        "eslint-config-canonical": "^1.8.6",
        "gitdown": "^2.4.0",
        "husky": "^0.11.7",
        "mocha": "^3.0.2",
        "nyc": "^8.3.1",
        "sinon": "^1.17.2"
    },
    "directories": {},
    "dist": {
        "shasum": "a8116c133fac2c61f4a420ab6cdf5c4d61f0e435",
        "tarball": "https://registry.npmjs.org/table/-/table-4.0.1.tgz"
    },
    "gitHead": "e55ef35ac3afbe42f789f666bc98cf05a97ae941",
    "homepage": "https://github.com/gajus/table#readme",
    "keywords": [
        "ascii",
        "text",
        "table",
        "align",
        "ansi"
    ],
    "license": "BSD-3-Clause",
    "main": "./dist/index.js",
    "maintainers": [
        {
            "name": "gajus"
        }
    ],
    "name": "table",
    "nyc": {
        "include": [
            "src/*.js"
        ],
        "instrument": false,
        "lines": 70,
        "require": [
            "babel-register"
        ],
        "sourceMap": false
    },
    "optionalDependencies": {},
    "repository": {
        "type": "git",
        "url": "git+https://github.com/gajus/table.git"
    },
    "scripts": {
        "build": "rm -fr ./dist && NODE_ENV=production babel --copy-files ./src --out-dir ./dist && npm run make-validators",
        "lint": "npm run build && eslint ./src ./tests",
        "make-readme": "gitdown ./.README/README.md --output-file ./README.md",
        "make-validators": "ajv compile --all-errors --inline-refs=false -s src/schemas/config -c ajv-keywords/keywords/typeof -o dist/validateConfig.js && ajv compile --all-errors --inline-refs=false -s src/schemas/streamConfig -c ajv-keywords/keywords/typeof -o dist/validateStreamConfig.js",
        "precommit": "npm run lint && npm run test",
        "prepublish": "NODE_ENV=production npm run build",
        "test": "npm run build && nyc --check-coverage mocha"
    },
    "version": "4.0.1",
    "bin": {}
}
```



# misc
- this document was created with [utility2](https://github.com/kaizhu256/node-utility2)
