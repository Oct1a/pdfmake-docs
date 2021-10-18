最低版本: **0.1.50**

```js
var docDefinition = {
  userPassword: '123', //用户密码，打开文件时需要输入密码解密
  ownerPassword: '123456', //所有者密码
  permissions: { //权限
    printing: 'highResolution', //'lowResolution' 分辨率设置
    modifying: false, //是否能够修改
    copying: false, //是否能够复制
    annotating: true, //是否能够添加注解
    fillingForms: true,
    contentAccessibility: true,
    documentAssembly: true
  },
  content: [
    '...'
  ]
};
```

PDF文档允许您加密PDF文件，并在打开文件时要求密码，或者设置用户可以使用PDF文件的权限。

要启用加密，请在`userPassword`(字符串值)中设置用户密码。当提供用户密码时，PDF文件将被加密，打开文件时，将提示用户输入密码来解密文件。

要为PDF文件设置访问权限，需要在`ownerPassword`(字符串值)中提供所有者密码，并提供具有权限的对象`permissions`。缺省情况下，不允许任何操作。您需要显式地允许某些操作。

在`permissions`对象中允许以下设置:

- `printing` - 是否允许打印. 指定值为`"lowResolution"`允许低分辨率打印, 或者设置为`"highResolution"`来允许以高分辨率打印
- `modifying` - 是否允许修改文件. 值设为`true`将允许用户修改文档内容
- `copying` - 是否允许复制图像或文本.如果值为`true`将被允许复制
- `annotating` - 是否允许添加注释或填表. 如果值为`true`将被允许复制与填表
- `fillingForms` - 是否允许填写和签署表格. 如果值为 `true`将允许填写表单字段和签名
- `contentAccessibility` -是否允许辅助功能复制文本. 如果值为 `true`将允许被复制
- `documentAssembly` - 是否允许编译文件. 如果值为 `true`将允许被编译

您可以指定用户密码、所有者密码或两者同时指定。根据您提供的密码，行为是不同的:

- 当只提供用户密码时，具有用户密码的用户能够解密文件并具有对文档的完全访问权。
- 当只提供所有者密码时，用户可以在不提供任何密码的情况下解密和打开文档，但访问仅限于明确允许的操作。拥有所有者密码的用户可以完全访问该文档。
- 当提供了两个密码时，具有用户密码的用户能够解密文件，但根据权限设置只能有限地访问文件。拥有所有者密码的用户可以完全访问该文档。

注意PDF文件本身不能强制访问。当文件被解密后，PDF查看器应用程序就可以完全访问文件内容，而查看器应用程序要遵守权限设置。

选择加密方法时，你需要以`version`指定PDF版本。使用了PDF版本的最佳加密方法.

PDF版本仅用于加密方法，所有其他PDF元素均在版本1.3中.

## 可用版本：

- `1.3` - PDF版本1.3(默认)，使用40位RC4
- `1.4` - PDF版本1.4，使用128位RC4
- `1.5` - PDF版本1.5, 使用128位RC4
- `1.6` - PDF版本1.6, 使用128位AES
- `1.7` - PDF版本1.7, 使用128位AES
- `1.7ext3` - PDF版本1.7 ExtensionLevel 3，使用256位AES

当使用PDF版本1.7 ExtensionLevel 3时，密码被截断为其UTF-8表示的127字节。在较早的版本中，密码被截断为32字节，并且只允许使用Latin-1字符