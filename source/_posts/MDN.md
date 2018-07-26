---
title: 看MDN的学到的总结
date: 2017-08-02 22:03:10
tags: javascript
---



通过 https://developer.mozilla.org 能学到不少web知识。现总结如下，不定期更新

### HTMLElement.dataset属性

html元素有一个全局属性。dataset。通过`data-yourCustom`的方式给DOM元素设置属性，然后通过
`dataset.yourCustom` 读取或设置属性值

看下面的例子中以`data-`开头的属性


<!--more-->

```
<div id="user" data-id="1234567890" data-user="johndoe" data-date-of-birth>John Doe</div>
```


``` javascript
var el = document.querySelector('#user');

// el.id == 'user'
// el.dataset.id === '1234567890'
// el.dataset.user === 'johndoe'
// el.dataset.dateOfBirth === ''

el.dataset.dateOfBirth = '1960-10-03'; // set the DOB.

// 'someDataAttr' in el.dataset === false

el.dataset.someDataAttr = 'mydata';
```


### [内容安全策略（CSP）](https://developer.mozilla.org/zh-CN/docs/Web/Security/CSP/Using_Content_Security_Policy)

CSP是一个出色的 WEB 安全方案

简而言之，内容安全策略（Content Security Policy，简称 CSP）是一种以可信白名单作机制，来限制网站中是否可以包含某来源的资源。资源类型细分为 Script、Style、Image、Font、Connect、Media、Object、Frame 等，可分别配置其来源。默认配置下不允许执行内联脚本和内联样式，也禁止执行 eval。

实现方式也非常简单

比如我在html的header中定义

```
<meta http-equiv="Content-Security-Policy" content="default-src 'self'; img-src https://*; child-src 'none';">
```

这里就限制了所有图片只能通过https方式访问

[CSP 规则生成器](http://cspisawesome.com/)
[浏览器安全策略 CSP 部署：Teambition 实战](https://www.teambition.com/en/developer/blog/article?p=developer-blog&s=&_id=5438e83ee903ca681810f174)