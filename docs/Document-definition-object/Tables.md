从概念上讲，表格类似于[列](/Document-definition-object/Lists)。但不同的是表格可以有标题、边框和横跨多列/行的单元格。

```js
var docDefinition = {
  content: [
    {
      layout: 'lightHorizontalLines', // optional
      table: {
        // 如果表格横跨多个页面，标题会自动重复。
        // 你可以声明有多少行应该被作为标题处理
        headerRows: 1,
        widths: [ '*', 'auto', 100, '*' ],

        body: [
          [ 'First', 'Second', 'Third', 'The last one' ],
          [ 'Value 1', 'Value 2', 'Value 3', 'Value 4' ],
          [ { text: 'Bold value', bold: true }, 'Val 2', 'Val 3', 'Val 4' ]
        ]
      }
    }
  ]
};
```

##### 单元格属性 

- `fillColor: string`: 表格单元格的背景色
- `fillOpacity: string`: 表格单元格的背景不透明度

##### 表格布局

可以使用 `layout` 设置表格布局.

可用的表格布局属性:

- `noBorders`
- `headerLineOnly`
- `lightHorizontalLines`

##### 自定义表格布局

在调用`pdfMake.createPdf(docDefinition)`函数前需先定义设表格布局设置.

```js
pdfMake.tableLayouts = {
  exampleLayout: {
    hLineWidth: function (i, node) {
      if (i === 0 || i === node.table.body.length) {
        return 0;
      }
      return (i === node.table.headerRows) ? 2 : 1;
    },
    vLineWidth: function (i) {
      return 0;
    },
    hLineColor: function (i) {
      return i === 1 ? 'black' : '#aaa';
    },
    paddingLeft: function (i) {
      return i === 0 ? 0 : 8;
    },
    paddingRight: function (i, node) {
      return (i === node.table.widths.length - 1) ? 0 : 8;
    }
  }
};

// 下载PDF
pdfMake.createPdf(docDefinition).download();
```

另外，你可以直接将`tableLayouts`传递给`createPdf`，而不改变全局变量。

- 在客户端:

```js
pdfMake.createPdf(docDefinition, tableLayouts).download();

//createPdf完整参数
//pdfMake.createPdf(docDefinition, tableLayouts, fonts, vfs)
```

- 在服务端:

```js
var PdfPrinter = require('pdfmake');
var printer = new PdfPrinter(fonts);

// 声明布局
var myTableLayouts = {
    exampleLayout: {
        /*
        Your layout here.
        */
    }
};

// 构建PDF
var pdfDoc = printer.createPdfKitDocument(docDefinition, {tableLayouts: myTableLayouts});

// 写入到磁盘
pdfDoc.pipe(fs.createWriteStream('document.pdf'));
pdfDoc.end();
```

可以查看与表相关的所有[例子](http://pdfmake.org/playground.html).