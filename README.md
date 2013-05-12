An experiment in creating an HTML rendering system based on JSON notation.
Need to render a table? Write:
```javascript
var tbl = {
  "table": [
    {
      "thead": {
        "tr": [
          {"th": "column A"},
          {"th": "column B"},
          {"th": "column C"},
          {"th": "column D"}
        ]
      }
    }, {
      "tbody": [
        {
          "tr": [
            {"td": "value 1"},
            {"td": "value 2"},
            {"td": "value 3"},
            {"td": "value 4"}
          ]
        }, {
          "tr": [
            {"td": "value 5"},
            {"td": "value 6"},
            {"td": "value 7"},
            {"td": "value 8"}
          ]
        }, {
          "tr": [
            {"td": "value 9"},
            {"td": "value 10"},
            {"td": "value 11"},
            {"td": "value 12"}
          ]
        }, {
          "tr": [
            {"td": "value 13"},
            {"td": "value 14"},
            {"td": "value 15"},
            {"td": "value 16"}
          ]
        }
      ]
    }
  ]
};
```

Convert the JSON to HTML:
```javascript
document.body.innerHTML = JHTMLparse(tbl);
```

Fill an unordered list:
```javascript
var listValues = [
  'list item 1',
  'list item 2',
  'list item 3',
  'list item 4',
  'list item 5',
  'list item 6'
];

var listMarkup = {
  'ul#list': []
};

for (var i=0, len=listValues.length; i<len; i++){
  listMarkup['ul#list'][i] = {'li': {'a[href="#"]': {'span': listValues[i]}}};
}

document.body.innerHTML = JHTMLparse(listMarkup);
```

You can specify attributes with jQuery like selector syntax:
```javascript
var link = {'a#my_link.my-link1.my-link2[href="http://google.com"][target="_blank"]': 'Click me!'};
document.body.innerHTML = JHTMLparse(link);
```

outputs:
```html
<a id="my_link" class="my-link1 my-link2" href="http://google.com" target="_blank">Click me!</a>
```