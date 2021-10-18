!> 最低版本: 0.1.59

SVG很像[图像](Document-definition-object/Images)，只是目前还不能通过文件或从字典中引入SVG.

SVG-to-PDFKit库用于将SVG转换为PDF文档。

```javascript
var docDefinition = {
  content: [
    {
      // 如果没有使用宽度/高度/尺寸，那么就使用svg元素的尺寸。.
      svg: '<svg width="300" height="200" viewBox="0 0 300 200">...</svg>'
    },
    {
      // 如果你指定了宽度，svg将按比例缩放。
      svg: '<svg width="300" height="200" viewBox="0 0 300 200">...</svg>',
      width: 150
    },
    {
      // 如果你同时指定宽度和高度--svg将被拉伸
      svg: '<svg width="300" height="200" viewBox="0 0 300 200">...</svg>',
      width: 600,
      height: 400
    },
    {
      // 你也可以把svg放在一个矩形里面
      svg: '<svg width="300" height="200" viewBox="0 0 300 200">...</svg>',
      fit: [150, 100]
    }
};
```