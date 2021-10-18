PDF文档可以有各种与之相关的元数据，如文档的标题，或作者。你可以通过将这些信息添加到文档定义中去

```js
var docDefinition = {
  info: {
	title: 'awesome Document',
	author: 'john doe',
	subject: 'subject of document',
	keywords: 'keywords for document',
  },
  content:  'This is an sample PDF printed with pdfMake'
}
```

## 标准属性:

- `title` - 文档标题
- `author` - 作者名称
- `subject` - 文件主题
- `keywords` - 关键词
- `creator` - 该文件的创建者 (默认是`pdfmake`)
- `producer` - 该文件的制作者 (默认是`pdfmake`)
- `creationDate` - 该文件的创建日期 (由pdfmake自动添加)
- `modDate` - 该文件最后一次被修改的日期
- `trapped` - 在PDF文件中被捕获的标志表明该文件是否已被“捕获”，即修正了轻微的颜色错误配准

## 自定义属性:

你可以添加自定义属性。属性的关键不包含空格。