```js
var docDefinition = {
  content: [
    // 基本使用
    { qr: 'text in QR' },

    // 给二维码增加颜色
    { qr: 'text in QR', foreground: 'red', background: 'yellow' },

    // 调整大小
    { qr: 'text in QR', fit: '500' },
  ]
}
```

## 属性:

- `qr`: `string` - 二维码文本

- `foreground`: `string` (可选, 默认黑色) - 前景颜色

- `background`: `string` (可选, 默认白色) - 背景颜色

- `fit`: `integer` (可选) - 设定图像大小

- `version`: `integer` (可选) - QR版本范围为1 ~ 40 (查看详情[wikipedia.org](https://en.wikipedia.org/wiki/QR_code#Storage)
- `eccLevel`:`string` (可选, 默认 L) - 容错率(纠错能力) (查看详情 [wikipedia.org](https://en.wikipedia.org/wiki/QR_code#Error_correction)), 可选值:
  - *L* - Level L (Low), 大约 7% 的码字可以恢复
  - *M* - Level M (Medium), 大约 15% 的码字可以恢复
  - *Q* - Level Q (Quartile), 大约 25% 的码字可以恢复
  - *H* - Level H (High), 大约 30% 的码字可以恢复
- `mode`: `string` (可选) - 编码模式，可能的值: *numeric*, *alphanumeric, octet* (查看详情 [wikipedia.org](https://en.wikipedia.org/wiki/QR_code#Storage))

- `mask`: `integer` (可选) - 掩膜版, 范围从0到7 (查看详情 [wikipedia.org](https://en.wikipedia.org/wiki/QR_code#Encoding))