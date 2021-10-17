在http://fontello.com/ 或其他地方制作一个字体，并下载它

从字体文件(例如 .ttf后缀文件) 创建 vfs_fonts.js 文件 (查看[如何使用自定义字体](Fonts/Custom-fonts/README))

在js中定义字体 (只要定义normal就足够了):

```javascript
pdfMake.fonts = {
    Fontello: {
        normal: 'fontello.ttf',
        bold: 'fontello.ttf',
        italics: 'fontello.ttf',
        bolditalics: 'fontello.ttf'
    }
}
```
- 为图标添加一个样式: ```icon: { font: 'Fontello' }```

- 编写一段文字: ```{ text: '', style: 'icon' }```,

- 作为你从fontello-codes.css的注释中复制的文本（不是转义的值）。

如果你需要文本中加入图标, 你需要嵌套文本对象:

    text: [
        { text: '', style: 'icon' },
        " my present"
    ]