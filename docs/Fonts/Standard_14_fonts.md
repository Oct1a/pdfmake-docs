# PDF包含14种标准字体

> 注意! 该字体仅支持ANSI代码页（仅支持英文字符）!

## 在服务器端的pdfmake中使用
使用示例:
```javascript
var fonts = {
  Courier: {
    normal: 'Courier',
    bold: 'Courier-Bold',
    italics: 'Courier-Oblique',
    bolditalics: 'Courier-BoldOblique'
  },
  Helvetica: {
    normal: 'Helvetica',
    bold: 'Helvetica-Bold',
    italics: 'Helvetica-Oblique',
    bolditalics: 'Helvetica-BoldOblique'
  },
  Times: {
    normal: 'Times-Roman',
    bold: 'Times-Bold',
    italics: 'Times-Italic',
    bolditalics: 'Times-BoldItalic'
  },
  Symbol: {
    normal: 'Symbol'
  },
  ZapfDingbats: {
    normal: 'ZapfDingbats'
  }
};

var PdfPrinter = require('pdfmake');
var printer = new PdfPrinter(fonts);
var fs = require('fs');

var docDefinition = {
  content: [
    'First paragraph',
    'Another paragraph, this time a little bit longer to make sure, this line will be divided into at least two lines',
  ],
  defaultStyle: {
    font: 'Helvetica'
  }
};

var pdfDoc = printer.createPdfKitDocument(docDefinition);
pdfDoc.pipe(fs.createWriteStream('document.pdf'));
pdfDoc.end();
```

## 在客户端的pdfmake中使用
默认情况下不支持，因为这会增加pdfmake库文件的大小，大约700 kB。

如果你真的需要它，你可以通过gulp buildWithStandardFonts命令使用标准字体进行构建。

用资源的标准字体进行构建:

```shell
git clone --branch 0.2 https://github.com/bpampuch/pdfmake.git
cd pdfmake
npm install
npm run build:browser-standard-fonts
```

或针对版本 0.1.x:

```shell
git clone --branch 0.1 https://github.com/bpampuch/pdfmake.git
cd pdfmake
npm install
gulp buildWithStandardFonts
```

使用示例:

```javascript

pdfMake.fonts = {
  Courier: {
    normal: 'Courier',
    bold: 'Courier-Bold',
    italics: 'Courier-Oblique',
    bolditalics: 'Courier-BoldOblique'
  },
  Helvetica: {
    normal: 'Helvetica',
    bold: 'Helvetica-Bold',
    italics: 'Helvetica-Oblique',
    bolditalics: 'Helvetica-BoldOblique'
  },
  Times: {
    normal: 'Times-Roman',
    bold: 'Times-Bold',
    italics: 'Times-Italic',
    bolditalics: 'Times-BoldItalic'
  },
  Symbol: {
    normal: 'Symbol'
  },
  ZapfDingbats: {
    normal: 'ZapfDingbats'
  }
};

var docDefinition = {
  content: [
    'First paragraph',
    'Another paragraph, this time a little bit longer to make sure, this line will be divided into at least two lines',
  ],
  defaultStyle: {
    font: 'Helvetica'
  }
};

pdfMake.createPdf(docDefinition).download('document.pdf');
```