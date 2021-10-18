pdfmake支持数字和项目符号列表:

```javascript
var docDefinition = {
  content: [
    'Bulleted list example:',
    {
      // 要把一个段落当作一个列表，在ul键下设置一个项目数组
      ul: [
        'Item 1',
        'Item 2',
        'Item 3',
        { text: 'Item 4', bold: true },
      ]
    },

    'Numbered list example:',
    {
      // 对于编号的列表，设置ol键
      ol: [
        'Item 1',
        'Item 2',
        'Item 3'
      ]
    }
  ]
};
```