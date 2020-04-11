# hexo-search-plugin-snippets

[文档介绍](http://www.barretlee.com/blog/2017/06/04/hexo-search-insite/)

一些辅助 `hexo-generator-search` 插件的代码片段，使用它可以实现如下效果：

![效果图](./preview.png)

### 初始化

```js
// 移动设备侦测
var isMobile = {
  Android: function () {
    return navigator.userAgent.match(/Android/i);
  },
  BlackBerry: function () {
    return navigator.userAgent.match(/BlackBerry/i);
  },
  iOS: function () {
    return navigator.userAgent.match(/iPhone|iPad|iPod/i);
  },
  Opera: function () {
    return navigator.userAgent.match(/Opera Mini/i);
  },
  Windows: function () {
    return navigator.userAgent.match(/IEMobile/i);
  },
  any: function () {
    return (isMobile.Android() || isMobile.BlackBerry() || isMobile.iOS() || isMobile.Opera() || isMobile.Windows());
  }
};
```

建议在移动端不初始化，其实 `/search.xml` 文件还挺大的，

```js
if ($('.local-search').size() && !isMobile.any()) {
  $.getScript('path/to/search.js', function() {
    searchFunc("/search.xml", 'local-search-input', 'local-search-result');
  });
}
```
