---
title: hexo部署到主机
date: 2018-05-24 22:17:01
tags:
---

目前博客是用的github pages，访问速度有点慢。于是想着换到自己的主机上面。
还要实现添加新文章后自动编译。
说干就干，过程也非常简单。

首先个人云主机上部署博客网站
```shell
cd /var/www/www.mafeifan.com
git clone git@gitee.com:finley/hexo.git
npm install -g hexo-cli
npm install
```

还需要跑一个node express程序，主机上本来就有，添加一个接口。用于web hook调用。
代码大致如下:

```javascript
async function execShell(scriptPath) {
  const execFile = require('util').promisify(require('child_process').execFile);
  return await execFile('sh', [scriptPath]);
}

app.post('/hexo', (req, res) => {
  const { stdout, stderr } = execShell('scripts/hexo.sh');
  if (stderr) {
    res.send('error');
  }
  res.send('success');
});
```
当调用这个接口比如地址是 (http://xx.xx/hexo) 执行服务器上一个shell脚本
scripts/hexo.sh 脚本的内容

```shell
#!/bin/bash
cd /var/www/www.mafeifan.com
git pull > /dev/null
npm install > /dev/null
hexo g > /dev/null

echo 0

```

然后，将调用地址加入到代码托管商的web hook中
![param](https://hexo-blog.pek3b.qingstor.com/20180524/webhook.png)

总结：
1. 不用非得使用node，也可以使用PHP，Python等可以执行shell的服务端语言
2. 编译后的文件在public目录，nginx要指向这里
3. 本地开发测试建议使用 ngrok 能节约不少时间
4. 修改博客内容直接在gitee上进行，还可以预览markdown挺方便的
