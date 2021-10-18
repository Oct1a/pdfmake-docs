!> 本文只针对浏览器客户端使用! 对于服务器端需使用真实的字体文件。.

?> 最低版本: 0.1.72 文件是兼容的。对于旧版本，使用gulp.
## ~~TL;DR(太长了，可以不用看)~~
~~pdfmake使用第二个文件：vfs_fonts.js，用于将字体（和其他文件）嵌入到你生成的PDF中。.~~

~~当你运行命令 `node build-vfs.js "./examples/fonts"` 在pdfmake软件包目录下会创建一个新的 `build/vfs_fonts.js`文件,其中包含本地examples/fonts子目录下所有文件的嵌入式拷贝（在一个键/值对象pdfMake.vfs中）。~~

## 详细说明
要使用自定义字体，需要3个步骤:

## 创建一个新的 `vfs_fonts.js` 文件，其中包含你的字体文件
在你的javascript中指定pdfMake.fonts，然后在你的`doc-definition`中指定字体。

### 1.新建一个 `vfs_fonts.js` 包含你字体的文件
- 安装 pdfmake `npm install pdfmake`
- 进入模块包目录 `./node_modules/pdfmake/`
- 在你的pdfmake代码目录下创建`examples/fonts`子目录（如果子目录不存在的话）.
- 复制你的字体 (以及其他嵌入的文件) 到 `examples/fonts` 子目录
- 运行命令`node build-vfs.js "./examples/fonts"`. 或者运行`node build-vfs.js`显示帮助文档.
- 引用新的`build/vfs_fonts.js`文件到你的代码中 (跟引用pdfmake.js 或者 pdfmake.min.js使用相同的方式).

上述步骤嵌入了`examples/fonts`的所有文件。(pdfMake.vfs将变成一个键/值变量) <br>
不仅可以是字体. 你也可以把图片放在那里，然后运行`node build-vfs.js "./examples/fonts`，并在你的`doc-definition`对象中以文件名引用它们。

你不再需要引用`examples/fonts`中的文件，因为所有文件都被复制到了`vfs_fonts.js`中。.

其他方式:

- 通过shell脚本构建字体文件
- 通过php脚本构建字体文件

### 2. 在你的javascript中指定pdfMake.fonts 
在你代码中调用`pdfMake.createPdf(docDefinition)` 之前设置`pdfMake.fonts` 如下面的例子（注意我们没有指定路径，只有文件名）。

```javascript
pdfMake.fonts = {
  yourFontName: {
    normal: 'fontFile.ttf',
    bold: 'fontFile2.ttf',
    italics: 'fontFile3.ttf',
    bolditalics: 'fontFile4.ttf'
  },
  anotherFontName: {
    (...)
  },

  PingFangSC: {
    normal: ['pingfang.ttc', 'PingFangSC-Regular'],
    bold: ['pingfang.ttc', 'PingFangSC-Semibold'],
  }
}
```

这里定义的键值（key）将在你的文档定义样式中作为字体名称使用。

`font-family` 可以使用4个属性: `normal`, `bold`, `italics`,`bolditalics`

默认情况下，pdfmake使用以下的字体结构。

```javascript
pdfMake.fonts = {
  Roboto: {
    normal: 'Roboto-Regular.ttf',
    bold: 'Roboto-Medium.ttf',
    italics: 'Roboto-Italic.ttf',
    bolditalics: 'Roboto-MediumItalic.ttf'
  }
};
```
或者，你也可以不改变全局值，而是直接将字体对象传递给`createPdf`:

**pdfMake.createPdf(docDefinition, null, fonts)**

```javascript
// createPdf的完整签名是这样的。.
// tableLayouts, fonts and vfs 参数都是可选的
// 错误参数会导致pdfMake.tableLayouts, pdfMake.fonts or pdfMake.vfs被使用
pdfMake.createPdf(docDefinition, tableLayouts, fonts, vfs)
```

### 3. 在您的文档定义中指定字体
pdfMake 使用 ‘Roboto’ 为默认字体, 所以为了使用你的字体，你应该在你的`doc-definition`对象中指定它。.

最简单的方法是在`defaultStyle`中全局设置。

```javascript
var docDefinition = {
  content: (...),
  defaultStyle: {
    font: 'yourFontName'
  }
}
```