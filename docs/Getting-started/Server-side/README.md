在服务器端，你可以直接通过npm安装：

```npm install pdfmake```

## 用法示例: 

```javascript
// 定义字体文件
var fonts = {
  Roboto: {
    normal: 'fonts/Roboto-Regular.ttf',
    bold: 'fonts/Roboto-Medium.ttf',
    italics: 'fonts/Roboto-Italic.ttf',
    bolditalics: 'fonts/Roboto-MediumItalic.ttf'
  }
};

var PdfPrinter = require('pdfmake');
var printer = new PdfPrinter(fonts);
var fs = require('fs');

var docDefinition = {
  // ...
};

var options = {
  // ...
}

var pdfDoc = printer.createPdfKitDocument(docDefinition, options);
pdfDoc.pipe(fs.createWriteStream('document.pdf'));
pdfDoc.end();
```

### createPdfKitDocument参数:

- docDefinition - 具有文件定义的对象
- options - 高级选项见选项章节