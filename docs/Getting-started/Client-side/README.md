要在浏览器中开始使用默认配置，你应该引入两个文件

- pdfmake.min.js,
- vfs_fonts.js - 默认字体定义 (默认使用Roboto字体，也可以使用自定义字体来代替)

```html
<!doctype html>
<html lang='en'>
<head>
  <meta charset='utf-8'>
  <title>my first pdfmake example</title>
  <script src='build/pdfmake.min.js'></script>
  <script src='build/vfs_fonts.js'></script>
</head>
<body>
```

## 资源包
### cdnjs 
[https://cdnjs.com/libraries/pdfmake](https://cdnjs.com/libraries/pdfmake)

### bower (已被废弃) 
```shell
bower install pdfmake
```
### npm 
```shell
npm install pdfmake
```

客户端引用的文件在这里可以找到:

- require('pdfmake/build/pdfmake.js');
- require('pdfmake/build/vfs_fonts.js');

使用`javascript`框架:

```javascript
var pdfMake = require('pdfmake/build/pdfmake.js');
var pdfFonts = require('pdfmake/build/vfs_fonts.js');
pdfMake.vfs = pdfFonts.pdfMake.vfs;
```

或者

```javascript
import pdfMake from "pdfmake/build/pdfmake";
import pdfFonts from "pdfmake/build/vfs_fonts";
pdfMake.vfs = pdfFonts.pdfMake.vfs;
```

`TypeScript`:


```javascript
import * as pdfMake from "pdfmake/build/pdfmake";
import * as pdfFonts from 'pdfmake/build/vfs_fonts';
(<any>pdfMake).vfs = pdfFonts.pdfMake.vfs;
```
关于Ionic和Angular，查看 [issue](https://github.com/bpampuch/pdfmake/issues/1030).

如果出现 **Cannot read property ‘TYPED_ARRAY_SUPPORT’ of undefined** 无法读取未定义属性错误, 请将此添加到webpack配置中:
```
exclude: [ /node_modules/, /pdfmake.js$/ ]
```
(see [issue](https://github.com/bpampuch/pdfmake/issues/1100#issuecomment-336728521))

如果你在使用rollup,并且在vfs_fonts.js中出现 **Cannot read property ‘pdfMake’ of undefined at vfs_fonts.js** 无法读取未定义的属性'pdfMake'的错误，请在rollup配置中添加以下内容:

```javascript
moduleContext: {
  './node_modules/pdfmake/build/vfs_fonts.js': 'window',
},
```
然后如果控制台输出“outputs a Illegal reassignment to import ‘pdfMake’”不要手动分配vfs，只要像这样导入字体即可:

```javascript
import 'pdfmake/build/vfs_fonts';
```
## 仓库 
你可以从源代码构建它，或者从存储库的构建目录直接复制它们:

- 版本说明 [0.2.x](https://github.com/bpampuch/pdfmake/tree/0.2#building-from-sources-version-02x)
- 版本说明 [0.1.x](https://github.com/bpampuch/pdfmake/tree/0.1#building-from-sources-version-01x)