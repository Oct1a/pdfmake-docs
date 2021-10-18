```js
var docDefinition = {
  // 一个字符串值或者自定义宽高 { width: number, height: number }
  pageSize: 'A5',

  // 默认情况下，我们使用竖屏（`portrait`），如果你愿意，你也可以将它改为横屏（`landscape`）
  pageOrientation: 'landscape',

  // [left, top, right, bottom] 或者 [horizontal, vertical] 或者只是一个等边距的数字
  pageMargins: [ 40, 60, 40, 60 ],
};
```

如果你设置`pageSize`为字符串, 您可以使用以下值之一:

- `'4A0'`, `'2A0'`, `'A0'`, `'A1'`, `'A2'`, `'A3'`, `'A4'`, `'A5'`, `'A6'`, `'A7'`, `'A8'`, `'A9'`, `'A10'`,
- `'B0'`, `'B1'`, `'B2'`, `'B3'`, `'B4'`, `'B5'`, `'B6'`, `'B7'`, `'B8'`, `'B9'`, `'B10'`,
- `'C0'`, `'C1'`, `'C2'`, `'C3'`, `'C4'`, `'C5'`, `'C6'`, `'C7'`, `'C8'`, `'C9'`, `'C10'`,
- `'RA0'`, `'RA1'`, `'RA2'`, `'RA3'`, `'RA4'`,
- `'SRA0'`, `'SRA1'`, `'SRA2'`, `'SRA3'`, `'SRA4'`,
- `'EXECUTIVE'`, `'FOLIO'`, `'LEGAL'`, `'LETTER'`, `'TABLOID'`

若要更改文档中的页面方向，请使用新页面方向添加分页符。

```js
{
  pageOrientation: 'portrait',
  content: [
    {text: 'Text on Portrait'},
    {text: 'Text on Landscape', pageOrientation: 'landscape', pageBreak: 'before'},
    {text: 'Text on Landscape 2', pageOrientation: 'portrait', pageBreak: 'after'},
    {text: 'Text on Portrait 2'},
  ]
}
```

自动页面高度:

```js
var dd = {
  pageSize: {
    width: 595.28,
    height: 'auto'
  },
  content: [
    // ...
  ]
}
```

####  为了避免孤儿，可以使用动态控制分页符

可以指定`pageBreakBefore`函数，该函数可以确定是否应该在节点之前插入分页符。要实现“no orphan child”规则，可以使用这样的定义:

```javascript
var dd = {
    content: [
       {text: '1 Headline', headlineLevel: 1},
       'Some long text of variable length ...',
       {text: '2 Headline', headlineLevel: 1},
       'Some long text of variable length ...',
       {text: '3 Headline', headlineLevel: 1},
       'Some long text of variable length ...',
    ],
  pageBreakBefore: function(currentNode, followingNodesOnPage, nodesOnNextPage, previousNodesOnPage) {
     return currentNode.headlineLevel === 1 && followingNodesOnPage.length === 0;
  }
}
```

如果`pageBreakBefore`函数返回`true`,`currentNode`的前面将添加一个分页符. 当前节点已附上以下信息:

```javascript
{
   id: '<如文件定义所述>',
   headlineLevel: '<如文件定义所述>',
   text: '<如文件定义所述>',
   ul: '<如文件定义所述>',
   ol: '<如文件定义所述>',
   table: '<如文件定义所述>',
   image: '<如文件定义所述>',
   qr: '<如文件定义所述>',
   canvas: '<如文件定义所述>',
   columns: '<如文件定义所述>',
   style: '<如文件定义所述>',
   pageOrientation '<如文件定义所述>',
   pageNumbers: [2, 3], // 该元素所在的页面(例如，多行文本可以出现在多个页面上)
   pages: 6, // 本文档的总页数
   stack: false, // 如果这是一个封装了多个子对象的元素
   startPosition: {
     pageNumber: 2, // 该节点开始的页面
     pageOrientation: 'landscape', // 页面的方向
     left: 60, // 左边的位置
     right: 60, // 右边的位置
     verticalRatio: 0.2, // 本文档中垂直使用的空间比例(不包括边距)
     horizontalRatio: 0.0  // 在本文档中水平使用的空间比例(不包括边距)
   }
}
```