简单的目录示例:

```js
var docDefinition = {
  content: [
    {
      toc: {
        title: {text: 'INDEX', style: 'header'}
      }
    },
    {
      text: 'This is a header',
      style: 'header',
      tocItem: true
    }
  ]
}
```

如果`toc`中使用`id`,那`tocItem`就可以引用到该ID上:

```js
var docDefinition = {
  content: [
    {
      toc: {
        id: 'mainToc',
        title: {text: 'INDEX', style: 'header'}
      }
    },
    {
      text: 'This is a header',
      style: 'header',
      tocItem: 'mainToc'
    }
  ]
}
```

如果使用多个目录, `tocItem`可以使用数组形式放入`toc`:

```js
var docDefinition = {
  content: [
    {
      toc: {
        id: 'mainToc',
        title: {text: 'INDEX', style: 'header'}
      },
      toc: {
        id: 'subToc',
        title: {text: 'SUB INDEX', style: 'header'}
      }
    },
    {
      text: 'This is a header',
      style: 'header',
      tocItem: ['mainToc', 'subToc']
    }
  ]
}
```