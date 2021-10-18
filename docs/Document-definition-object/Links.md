要添加外部或内部链接，请使用以下语法：

```javascript
{ text: 'google', link: 'http://google.com' }
{ text: 'Go to page 2', linkToPage: 2 }
{ text: 'Go to Header', linkToDestination: 'header' },
{ text: 'Header content', id: 'header' },
```

## 属性
- link 【string】 - 外部网站的URL

- linkToPage 【number】 - 链接到页码

- linkToDestination 【string】 - 链接到文件目的地