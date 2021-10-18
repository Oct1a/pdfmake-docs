使用很简单。只要使用`{ image: '...' } `创建图像节点即可

支持JPEG和PNG格式.

```javascript
var docDefinition = {
  content: [
    {
      // 如果你通常在浏览器端使用base64（dataUrl）图像的话
      // 如果没有提供宽度/高度/尺寸，将使用原始尺寸。
      image: 'data:image/jpeg;base64,...encodedContent...'
    },
    {
      // 如果你指定宽度，图像将按比例缩放。
      image: 'data:image/jpeg;base64,...encodedContent...',
      width: 150
    },
    {
      // 如果你同时指定宽度和高度--图像将被拉长
      image: 'data:image/jpeg;base64,...encodedContent...',
      width: 150,
      height: 150
    },
    {
      // 你也可以把图像放在一个矩形内
      image: 'data:image/jpeg;base64,...encodedContent...',
      fit: [100, 100]
    },
    {
      // 如果你在多个节点中重复使用同一个图像,
      // 你应该把它放到图像字典Array里面，并按名称来引用它。
      image: 'mySuperImage'
    },
    {
      // 在NodeJS下（或者在你使用pdfmake提供的虚拟文件系统的情况下）。
      // 你也可以在这里传递文件名
      image: 'myImageDictionary/image1.jpg'
    },
    {
      // 在浏览器中，支持通过图片中的名称引用的url加载外部图片。
      image: 'snow'
    },
  ],

  images: {
    mySuperImage: 'data:image/jpeg;base64,...content...',

    // 在浏览器中支持通过url（https或http协议）加载图像（最低版本：0.1.67）。
    snow: 'https://picsum.photos/seed/picsum/200/300'
  }
};
```