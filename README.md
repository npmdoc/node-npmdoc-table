# api documentation for  [table (v4.0.1)](https://github.com/gajus/table#readme)  [![npm package](https://img.shields.io/npm/v/npmdoc-table.svg?style=flat-square)](https://www.npmjs.org/package/npmdoc-table) [![travis-ci.org build-status](https://api.travis-ci.org/npmdoc/node-npmdoc-table.svg)](https://travis-ci.org/npmdoc/node-npmdoc-table)
#### Formats data into a string table.

[![NPM](https://nodei.co/npm/table.png?downloads=true)](https://www.npmjs.com/package/table)

[![apidoc](https://npmdoc.github.io/node-npmdoc-table/build/screenCapture.buildNpmdoc.browser._2Fhome_2Ftravis_2Fbuild_2Fnpmdoc_2Fnode-npmdoc-table_2Ftmp_2Fbuild_2Fapidoc.html.png)](https://npmdoc.github.io/node-npmdoc-table/build/apidoc.html)

![npmPackageListing](https://npmdoc.github.io/node-npmdoc-table/build/screenCapture.npmPackageListing.svg)

![npmPackageDependencyTree](https://npmdoc.github.io/node-npmdoc-table/build/screenCapture.npmPackageDependencyTree.svg)



# package.json

```json

{
    "author": {
        "name": "Gajus Kuizinas",
        "email": "gajus@gajus.com",
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
            "name": "gajus",
            "email": "gk@anuary.com"
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
    "readme": "ERROR: No README data found!",
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
    "version": "4.0.1"
}
```



# <a name="apidoc.tableOfContents"></a>[table of contents](#apidoc.tableOfContents)

#### [module table](#apidoc.module.table)
1.  [function <span class="apidocSignatureSpan"></span>table (data)](#apidoc.element.table.table)
1.  [function <span class="apidocSignatureSpan">table.</span>createStream ()](#apidoc.element.table.createStream)
1.  [function <span class="apidocSignatureSpan">table.</span>getBorderCharacters (name === 'honeywell')](#apidoc.element.table.getBorderCharacters)



# <a name="apidoc.module.table"></a>[module table](#apidoc.module.table)

#### <a name="apidoc.element.table.table"></a>[function <span class="apidocSignatureSpan"></span>table (data)](#apidoc.element.table.table)
- description and source-code
```javascript
table = function (data) {
  let userConfig = arguments.length > 1 && arguments[1] !== undefined ? arguments[1] : {};

  let rows;

  (0, _validateTableData2.default)(data);

  rows = (0, _stringifyTableData2.default)(data);

  const config = (0, _makeConfig2.default)(rows, userConfig);

  rows = (0, _truncateTableData2.default)(data, config);

  const rowHeightIndex = (0, _calculateRowHeightIndex2.default)(rows, config);

  rows = (0, _mapDataUsingRowHeightIndex2.default)(rows, rowHeightIndex, config);
  rows = (0, _alignTableData2.default)(rows, config);
  rows = (0, _padTableData2.default)(rows, config);

  const cellWidthIndex = (0, _calculateCellWidthIndex2.default)(rows[0]);

  return (0, _drawTable2.default)(rows, config.border, cellWidthIndex, rowHeightIndex, config.drawHorizontalLine);
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.table.createStream"></a>[function <span class="apidocSignatureSpan">table.</span>createStream ()](#apidoc.element.table.createStream)
- description and source-code
```javascript
createStream = function () {
  let userConfig = arguments.length > 0 && arguments[0] !== undefined ? arguments[0] : {};

  const config = (0, _makeStreamConfig2.default)(userConfig);

  const columnWidthIndex = _lodash2.default.mapValues(config.columns, column => {
    return column.width + column.paddingLeft + column.paddingRight;
  });

  let empty;

  empty = true;

  return {
<span class="apidocCodeCommentSpan">    /**
     * @param {string[]} row
     * @returns {undefined}
     */
</span>    write: row => {
      if (row.length !== config.columnCount) {
        throw new Error('Row cell count does not match the config.columnCount.');
      }

      if (empty) {
        empty = false;

        return create(row, columnWidthIndex, config);
      } else {
        return append(row, columnWidthIndex, config);
      }
    }
  };
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.table.getBorderCharacters"></a>[function <span class="apidocSignatureSpan">table.</span>getBorderCharacters (name === 'honeywell')](#apidoc.element.table.getBorderCharacters)
- description and source-code
```javascript
name => {
  if (name === 'honeywell') {
    return {
      topBody: '═',
      topJoin: '╤',
      topLeft: '╔',
      topRight: '╗',

      bottomBody: '═',
      bottomJoin: '╧',
      bottomLeft: '╚',
      bottomRight: '╝',

      bodyLeft: '║',
      bodyRight: '║',
      bodyJoin: '│',

      joinBody: '─',
      joinLeft: '╟',
      joinRight: '╢',
      joinJoin: '┼'
    };
  }

  if (name === 'norc') {
    return {
      topBody: '─',
      topJoin: '┬',
      topLeft: '┌',
      topRight: '┐',

      bottomBody: '─',
      bottomJoin: '┴',
      bottomLeft: '└',
      bottomRight: '┘',

      bodyLeft: '│',
      bodyRight: '│',
      bodyJoin: '│',

      joinBody: '─',
      joinLeft: '├',
      joinRight: '┤',
      joinJoin: '┼'
    };
  }

  if (name === 'ramac') {
    return {
      topBody: '-',
      topJoin: '+',
      topLeft: '+',
      topRight: '+',

      bottomBody: '-',
      bottomJoin: '+',
      bottomLeft: '+',
      bottomRight: '+',

      bodyLeft: '|',
      bodyRight: '|',
      bodyJoin: '|',

      joinBody: '-',
      joinLeft: '|',
      joinRight: '|',
      joinJoin: '|'
    };
  }

  if (name === 'void') {
    return {
      topBody: '',
      topJoin: '',
      topLeft: '',
      topRight: '',

      bottomBody: '',
      bottomJoin: '',
      bottomLeft: '',
      bottomRight: '',

      bodyLeft: '',
      bodyRight: '',
      bodyJoin: '',

      joinBody: '',
      joinLeft: '',
      joinRight: '',
      joinJoin: ''
    };
  }

  throw new Error('Unknown border template "' + name + '".');
}
```
- example usage
```shell
n/a
```



# misc
- this document was created with [utility2](https://github.com/kaizhu256/node-utility2)
