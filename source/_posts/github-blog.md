title: 利用github和hexo建立个人博客
date: 2017-03-04 16:38:29
update: 2022-08-01 18:30:00
categories: 技术
abstract: 利用github pages建立个人博客
tags: 技术
---



### 利用github建立个人博客
- 总体来说还是比较顺利，没有超过一天时间，在coding和github上都可以访问到博客了，参考网上hexo github pages 教程
- 主要步骤
    1. 安装node.js
    2. 安装git
    3. 安装hexo
    4. 选一个喜欢的主题
    5. 更新一个测试页面
    6. 同步上传成功之后就可以访问

- 按照教程按部就班：
    - 部署到github这步时，报错，如果报错信息能看出问题，就解决，看不出问题，就删除`.deploy_git`目录，然后
        1. ` git config --global core.autocrlf false` // 解决不同操作系统维护博客的问题
        2. ` hexo clean`
        3. ` hexo g`
        4. ` hexo d`
- 维护进阶
    - 在更换电脑之后发现博客无法推送和正常更新了，那是因为我们的master分支只有博客内容，并没有hexo博客的配置信息，所以以上初始化博客的过程又来了一遍，在重新初始化一遍博客以后
        1. 新建hexo分支
        2. 修改.gitingnore文件
             ![alt](/img/ignore.png)
        3. 推送hexo分支
    > 这样以后我们在客户端就只用在hexo分支更新操作就可以了，就算换了电脑环境，也只用同步hexo分支代码


* 2022更新，coding被收购以后pages服务没有了，等有时间会换成码云，因为github访问速度太慢了

