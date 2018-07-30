title: 利用github和hexo建立个人博客
date: 2017-03-04 16:38:29
categories: 技术
tags: 技术
---



### 利用github建立个人博客
- 总体来说还是比较顺利，没有超过一天时间，在coding和github上都可以访问到博客了，参考的教程网址是[基于Hexo+github+coding](http://ookamiantd.top/2017/build-blog-hexo-base/)
- 主要步骤
1. 安装node.js
2. 安装git
3. 安装hexo
4. 更新一个测试页面
5. 同步上传成功之后就可以访问

- 按照教程按部就班，还是遇到了几个坑，另外查到了别的大牛提供的解决方法：
    - 部署到github（hexo -d）这部时，会报错，而且是很多行很多行的错误，具体错误原因我也没弄清楚，git配置的问题，解决方法是:
        1. git命令行打开博客目录
        2. ` git config --global core.autocrlf false`
        3. ` hexo clean`
        4. ` hexo g`
        5. ` hexo d`

   很可惜其余几个问题现在已经想不到了，下次记录问题要及时一点。。。
