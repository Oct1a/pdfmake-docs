背景层将被添加到每个页面上。

```javascript
var docDefinition = {
  background: 'simple text',

  content: (...)
};
```

它可以包含其他对象(`images`, `tables`, …) 或者动态生成:

```javascript
var docDefinition = {
  background: function(currentPage, pageSize) {
    return `page ${currentPage} with size ${pageSize.width} x ${pageSize.height}`
  },

  content: (...)
};
```