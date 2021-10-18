#### Properties 

- `text` - 水印文本
- `color` - 字体颜色
- `opacity` - 字体透明度
- `bold` - 是否加粗
- `italics` - 斜体样式
- `fontSize` - 字体大小 (自动计算出理想尺寸) (**最低版本: 0.1.60**)
- `angle` - 文本旋转角度 (**最低版本: 0.1.60**)

#### 示例

简单的基本用法的例子:

```js
var docDefinition = {
  watermark: 'test watermark',
  content: [
    '...'
  ]
};
```

字体样式使用示例:

```js
var docDefinition = {
  watermark: { text: 'test watermark', color: 'blue', opacity: 0.3, bold: true, italics: false },
  content: [
    '...'
  ]
};
```

使用自定义字体大小示例:


```js
var docDefinition = {
  watermark: { text: 'test watermark', fontSize: 20 },
  content: [
    '...'
  ]
};
```

文本旋转角度示例:

```js
var docDefinition = {
  watermark: { text: 'test watermark', angle: 70 },
  content: [
    '...'
  ]
};
```