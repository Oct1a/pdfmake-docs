## 下载PDF
```javascript
pdfMake.createPdf(docDefinition).download();
```
### 属性：

- defaultFileName (可选) - 文件名
- cb (可选) - 回调函数
- options (可选) - 高级选项查看[选项](/Options)章节

## 在新的窗口打开PDF

```javascript
pdfMake.createPdf(docDefinition).open();
```
### 属性：

- options (可选) - 高级选项查看[选项](/Options)章节
- win (可选) - 当执行异步操作时使用,window.open方法，例如window.open()


名称只能通过使用元数据标题属性来定义（见[文档元数据](Document-definition-object/Document_Metadata)）。

异步的例子:

```javascript
$scope.generatePdf = function() {
  // 在回调之前调用窗口
  var win = window.open('', '_blank');
  $http.post('/someUrl', data).then(function(response) {
    // 赋值win参数
    pdfMake.createPdf(docDefinition).open({}, win);
  });
};
```

在同一窗口打开:

```javascript
pdfMake.createPdf(docDefinition).open({}, window);
```

## PDF打印 

```javascript
pdfMake.createPdf(docDefinition).print();
```
### 属性：

- options (可选) - 高级选项查看[选项](/Options)章节
- win (可选) - 当执行异步操作时使用

异步使用例子:

```javascript
$scope.generatePdf = function() {
  // 在回调之前调用窗口
  var win = window.open('', '_blank');
  $http.post('/someUrl', data).then(function(response) {
    // 赋值win参数
    pdfMake.createPdf(docDefinition).print({}, win);
  });
};
```

## 在同一窗口打印:

```javascript
pdfMake.createPdf(docDefinition).print({}, window);
```

## 把PDF作为URL链接放到你自己的网页上（网页嵌入pdf）

```javascript
const pdfDocGenerator = pdfMake.createPdf(docDefinition);
pdfDocGenerator.getDataUrl((dataUrl) => {
	const targetElement = document.querySelector('#iframeContainer');
	const iframe = document.createElement('iframe');
	iframe.src = dataUrl;
	targetElement.appendChild(iframe);
});
```
### 属性：

- cb - 回调函数
- options (可选) - 高级选项查看[选项](/Options)章节

## 获取PDF的base64数据 

```javascript
const pdfDocGenerator = pdfMake.createPdf(docDefinition);
pdfDocGenerator.getBase64((data) => {
	alert(data);
});
```
### 属性：

- cb - 回调函数
- options (可选) - 高级选项查看[选项](/Options)章节

## 获取PDF的buffer数据 

```javascript
const pdfDocGenerator = pdfMake.createPdf(docDefinition);
pdfDocGenerator.getBuffer((buffer) => {
	// ...
});
```
### 属性：

- cb - 回调函数
- options (可选) - 高级选项查看[选项](/Options)章节

## 获取PDF的Blob数据 

```javascript
const pdfDocGenerator = pdfMake.createPdf(docDefinition);
pdfDocGenerator.getBlob((blob) => {
	// ...
});
```
### 属性：

- cb - 回调函数
- options (可选) - 高级选项查看[选项](/Options)章节

## 以流的形式获取PDFKit文档对象

### 异步调用
>最低版本: 0.1.66
```javascript
const pdfDocGenerator = pdfMake.createPdf(docDefinition);
pdfDocGenerator.getStream((document) => {
	// ...
});
```
### 属性：

- cb - 函数调用
### 同步调用 
>最低版本: 0.1.41
>首选的方式是异步调用
>无法从网址上下载真正的字体文件 (https:// or http://)，需要异步调用.
```javascript
const pdfDocGenerator = pdfMake.createPdf(docDefinition);
var document = pdfDocGenerator.getStream();
```