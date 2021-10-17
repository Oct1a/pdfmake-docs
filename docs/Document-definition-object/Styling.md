> pdfmake使任何段落或其部分的样式成为可能。

```javascript
var docDefinition = {
  content: [
    // 如果你不需要样式, 你可以用一个简单的字符串来定义一个段落
    '这是一个标准段落，使用默认样式',

    // 使用 { text: '...' } 对象，用于设置属性
    { text: 'This paragraph will have a bigger font', fontSize: 15 },

    // 如果你将文本的值设置为数组而不是字符串，你就能够对任何段落进行单独的样式设计
    {
      text: [
        'This paragraph is defined as an array of elements to make it possible to ',
        { text: 'restyle part of it and make it bigger ', fontSize: 15 },
        'than the rest.'
      ]
    }
  ]
};
```
## 样式字典
也可以定义一个可复用样式的字典：

```javascript
var docDefinition = {
  content: [
    { text: 'This is a header', style: 'header' },
    'No styling here, this is a standard paragraph',
    { text: 'Another text', style: 'anotherStyle' },
    { text: 'Multiple styles applied', style: [ 'header', 'anotherStyle' ] }
  ],

  styles: {
    header: {
      fontSize: 22,
      bold: true
    },
    anotherStyle: {
      italics: true,
      alignment: 'right'
    }
  }
};
```
为了更深入地了解pdfmake中的风格设计、风格继承和局部风格覆盖，请查看pdfmake[例子](http://pdfmake.org/playground.html)中的STYLES1、STYLES2和STYLES3.

## 默认样式
而且还可以定义一个默认的样式：
```javascript
var docDefinition = {
  content: [
    'Text styled by default style'
  ],

  defaultStyle: {
    fontSize: 15,
    bold: true
  }
};
```
## 样式属性
- **font**: 【string】 字体名称
- **fontSize**: 【number】: 字体大小（以pt为单位）
- **fontFeatures**: 【string[]】: TTF字体支持高级阵列排版功能（支持的功能取决于字体文件)
- **lineHeight**: 【number】: 行高 (默认: 1)
- **bold**: 【boolean】: 是否使用粗体 (默认: false)
- **italics**: 【boolean】: 是否使用斜体 (默认: false)
- **alignment**: 【string】: 文本对齐方式：left、center、right、justify
- **characterSpacing**: 【number】: 字体间距大小（以pt为单位）
- **color**: 【string】: 字体颜色(颜色名称:如 'blue'或者十六进制：'#ff5500')
- **background**: 【string 】字体背景颜色
- **markerColor**: 【string】: 列表中项目符号的颜色
- **decoration**: 【string】: 要应用的字体装饰：underline、lineThrough、 overline
- **decorationStyle**: 【string】: 字体装饰风格：dashed、dotted、double、wavy
- **decorationColor**: 【string】: 文字装饰的颜色，参考color属性配置