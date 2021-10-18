从例子中你现在可能已经明白了，如果你把内容键设置为一个数组，文档就会变成一叠段落。

你经常会在一个嵌套的元素中重复使用这个结构，就像下面的例子一样:

```javascript
var docDefinition = {
  content: [
    'paragraph 1',
    'paragraph 2',
    {
      columns: [
        'first column is a simple text',
        [
          // 第二栏由段落构成
          'paragraph A',
          'paragraph B',
          'these paragraphs will be rendered one below another inside the column'
        ]
      ]
    }
  ]
};
```

数组有个问题是，你不能向它添加样式属性（例如，改变字体大小）。

不过数组只是pdfMake中{ stack: [] }，所以如果你想重新设计整个堆栈，你可以用扩展的定义来做。

```javascript
var docDefinition = {
  content: [
    'paragraph 1',
    'paragraph 2',
    {
      columns: [
        'first column is a simple text',
        {
          stack: [
            // 第二栏由段落构成
            'paragraph A',
            'paragraph B',
            'these paragraphs will be rendered one below another inside the column'
          ],
          fontSize: 15
        }
      ]
    }
  ]
};
```