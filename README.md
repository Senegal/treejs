# treejs

a lightweight tree widget, compatible with originaljs/react/vue, 9.6kb size for tree.min.js&tree.min.css without gzip.

# Install

`npm i -S @widgetjs/tree`

# Usage

### react/vue usage

```js
import Tree from '@widgetjs/tree';
import '@widgetjs/tree/dist/tree.min.css';
```

### originaljs usage

```html
<link rel="stylesheet" href="${your-asset-src-path}/@widgetjs/tree/dist/tree.min.css">
<script src="${your-asset-src-path}/@widgetjs/tree/dist/tree.min.js"></script>
```

# Example

```js
// format
{"id":"unique_ID","text":"node-0","attributes":{},"children":[],"check":true/false}
```

```js
let treeData = [{"id":"0","text":"node-0","children":[{"id":"0-0","text":"node-0-0","children":[{"id":"0-0-0","text":"node-0-0-0"},{"id":"0-0-1","text":"node-0-0-1"},{"id":"0-0-2","text":"node-0-0-2"}]},{"id":"0-1","text":"node-0-1"}]},{"id":"1","text":"node-1","children":[{"id":"1-0","text":"node-1-0"},{"id":"1-1","text":"node-1-1"}]}];

new Tree('#container', {
  data: treeData
});

new Tree('#container', {
  data: treeData,
  values: ['1', '2', '3']
});

new Tree('#container', {
  url: '/api/treeJson',
  values: ['1', '2', '3']
});

new Tree('#container', {
  url: '/api/rawData',
  beforeLoad: rawdata => {
    let formatedData = rawdata; // do some format
    return formatedData;
  },
  values: ['1', '2', '3'],
});

new Tree('#container', {
  url: '/api/treeJson',
  loaded: () => {
    // to something or setValues() after Tree loaded callback
    let treeJson = [];
    this.values = treeJson;
  },
});

new Tree('#container', {
    url: '/api/treeWithCheckedStatusJson',
});

let tree = new Tree({
  data: treeData
  values: ['1', '2', '3']
});
// get values of selected leaves
let values = tree.values;
// get all selected nodes with individual data you send
let selectedNodes = tree.selectedNodes;
```