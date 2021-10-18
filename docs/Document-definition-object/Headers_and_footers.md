pdfmake中的页眉和页脚可以是：静态或动态生成。

它们使用相同的语法:

```javascript
var docDefinition = {
  header: 'simple text',

  footer: {
    columns: [
      'Left part',
      { text: 'Right part', alignment: 'right' }
    ]
  },

  content: (...)
};
```

对于动态生成的内容（包括页码、页数和页面大小），你可以向页眉或页脚传递一个函数。

```javascript
var docDefinition = {
  footer: function(currentPage, pageCount) { return currentPage.toString() + ' of ' + pageCount; },
  header: function(currentPage, pageCount, pageSize) {
    // 你可以应用任何逻辑并返回任何有效的pdfmake元素

    return [
      { text: 'simple text', alignment: (currentPage % 2) ? 'left' : 'right' },
      { canvas: [ { type: 'rect', x: 170, y: 32, w: pageSize.width - 170, h: 40 } ] }
    ]
  },
  (...)
};
```