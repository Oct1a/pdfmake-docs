> 最低版本: 0.1.66
> 该功能仅在客户端浏览器中可用。

要使用自定义字体，需要2个步骤。:

1. 指定pdfMake.fonts为你的字体文件，可通过javascript中的url地址访问。
2. 在你的文档定义中指定字体。
## 1. 在你的JavaScript中指定pdfMake.fonts为你的字体文件 

字体文件必须可以通过URL地址（https:// 或 http:// 协议）访问。在你的代码调用pdfMake.createPdf(docDefinition)之前，需设置pdfMake.fonts，如下例所示:

```javascript
pdfMake.fonts = {
   yourFontName: {
     normal: 'https://example.com/fonts/fontFile.ttf',
     bold: 'https://example.com/fonts/fontFile2.ttf',
     italics: 'https://example.com/fonts/fontFile3.ttf',
     bolditalics: 'https://example.com/fonts/fontFile4.ttf'
   },
   anotherFontName: {
     (...)
   },

   //  从cdnjs.com下载默认 Roboto字体
   Roboto: {
     normal: 'https://cdnjs.cloudflare.com/ajax/libs/pdfmake/0.1.66/fonts/Roboto/Roboto-Regular.ttf',
     bold: 'https://cdnjs.cloudflare.com/ajax/libs/pdfmake/0.1.66/fonts/Roboto/Roboto-Medium.ttf',
     italics: 'https://cdnjs.cloudflare.com/ajax/libs/pdfmake/0.1.66/fonts/Roboto/Roboto-Italic.ttf',
     bolditalics: 'https://cdnjs.cloudflare.com/ajax/libs/pdfmake/0.1.66/fonts/Roboto/Roboto-MediumItalic.ttf'
   },

   // 集合中使用字体的示例
   PingFangSC: {
     normal: ['https://example.com/fonts/pingfang.ttc', 'PingFangSC-Regular'],
     bold: ['https://example.com/fonts/pingfang.ttc', 'PingFangSC-Semibold'],
   }
}
```
或者，你可以不改变全局值，而是直接将字体对象传递给createPdf。

```javascript
pdfMake.createPdf(docDefinition, null, fonts)
```

## 2. 在你的文档定义中指定字体 
pdfMake使用 "Roboto "作为默认字体，所以为了使用你的字体，你应该在你的doc-definition对象中指定它。

最简单的方法是在defaultStyle中全局设置它

```javascript
var docDefinition = {
  content: (...),
  defaultStyle: {
    font: 'yourFontName'
  }
}
```