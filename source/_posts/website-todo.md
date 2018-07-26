---
title: 网站更新记录
date: 2017-07-29 17:27:37
tags: website
---


### 更新记录
- 2018.7.20 根据要求网站底部加上备案号
- 2018.5.22 移到个人腾讯云服务器，新域名 www.mafeifan.com
- 2018.2.08 修改avatar，添加about页面
- 2017.9.01 升级为https
- 2017.8.18 加入 CNZZ 统计
- 2017.8.09 安装 https://github.com/hexojs/hexo-generator-sitemap 插件

<!--more-->

### 已处理问题

- /tags打开报404，没有生成index.html
答：运行`hexo new page tags`, 然后打开`\source\tags\index.md`添加一行`type: tags`
- more查看全文的使用
答：使用`<!--more-->`就可以了
- 如何添加next主题的自定义样式
答：修改`\themes\next\source\css\_custom\custom.styl`
- RSS支持
答：/sitemap.xml

### 网站待处理的问题

- 顶置功能
- 文章封面图(看来需要换个主题了)
- blog版本对比
- 提速，合并JS
- 头像等细节
- 仿 分成技术和生活两大板块

### 在其他电脑上写blog的方法
* git checkout master分支
* npm install
* hexo g -d 编译并部署
* 因为源码是部署在gitee, 支持markdown预览，直接在上面修改保存提交即可


### 网站主题
http://theme-next.iissnan.com/getting-started.html

