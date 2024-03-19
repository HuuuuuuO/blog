#  博客搭建：Jekyll + Github Pages

Jekyll就是将纯文本转化为静态博客网站，不需要数据库支持，也没有评论功能，想要评论功能的话可以借助第三方的评论服务。
Jekyll + Github Pages可以让你更加专注于博客内容，而不是如何搭建一个博客平台。

## 1、安装ruby

下载ruby+devkit

https://rubyinstaller.org/downloads/

![image-20240319151436318](博客搭建：Jekyll + Github Pages.assets/image-20240319151436318.png)



这一步出现了很多问题，最后的解决方法是，卸载，重装，==**ruby的默认安装地址不要变**==！

验证：

```
ruby -v

gem -v
```

然后安装 jekyll ：

```
gem sources --add https://gems.ruby-china.com/ --remove https://rubygems.org/
gem sources -l

gem install jekyll
gem install jekyll-paginate
jekyll -v
```

再安装 bundler ：

```
gem install bundler
```