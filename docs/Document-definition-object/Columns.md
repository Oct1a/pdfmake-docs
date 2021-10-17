默认情况下，段落被渲染成一个垂直堆叠的元素（一个在另一个下面）,还有可能会将可用文档划分为几列。

```javascript
var docDefinition = {
  content: [
    '因为没有其他列，这段落占满了整个宽度, 下面的内容将被分三栏显示',
    {
      columns: [
        {
          // 自动尺寸的列，其宽度基于其内容撑开
          width: 'auto',
          text: 'First column'
        },
        {
          //宽度设置为'*'分栏将填满剩余空间
          // 如果有一个以上宽度设置为'*'，可用的宽度将被平均分配。
          width: '*',
          text: 'Second column'
        },
        {
          // 固定宽度
          width: 100,
          text: 'Third column'
        },
        {
          // 百分比宽度
          width: '20%',
          text: 'Fourth column'
        }
      ],
      // 列间距
      columnGap: 10
    },
    '这段文字也是内容，会在分栏底部撑满宽度显示'
  ]
};
```
列的内容不限于简单的文本。它实际上可以包含任何有效的pdfmake元素。请务必看一下[案例][http://pdfmake.org/playground.html]上的COLUMNS例子。

## 属性
columnGap: 【number】列与列之间的间距