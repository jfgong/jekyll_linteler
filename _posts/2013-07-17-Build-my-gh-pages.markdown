---
layout: post 
title: 搭建gh-pages博客
---

<h2>{{ page.title }}</h2>

Github中带有pages功能，用于在github上托管静态网页，所以可以用来搭建个人主页，支持基于jekyll规范的静态网页。
这就省去了：服务器(IP静态)+博客系统(网页文件)，下一步只需要申请域名(网址动态)并绑定即可。

1.建立gh-pages分支
    建立一个项目jekyll_repo，创建gh-pages分支，编辑好本地文件后push到remote端
    此时可以使用http://username.github.com/jekyll_repo/查看

2.去域名注册商DOTtk处申请域名domain.tk，建立域名和服务器之间的绑定
    2.1 在DOTtk中自定义域名解析服务器DNS，如DNSPOD：f1g1ns1.dnspod.net、f1g1ns2.dnspod.net
    2.2 在DNSPOD中为域名domain.tk添加记录，如：www CNAME username.github.com.
    2.3 在jekyll_repo根目录下添加CNAME文件，绑定域名，内容为：www.domain.tk

3.使用www.domain.tk访问网页

备注：

1.之前的Github pages使用username.github.com,现在已经改用username.github.io

2.建立个人页面有两种方式：project pages的gh-pages分支;user pages的master分支
If you are working with a user pages repository, this should be done in the master branch. If you're working with project pages, then it should go in the gh-pages branch of the project repository.

3.jekyll根目录下的_config.yml文件
    3.1 使用www.domain.tk域名时，内容为"baseurl: "
    3.2 使用username.github.com时，内容为"baseurl: /jekyll_repo"

4.设置domain.tk访问时，DNSPOD中添加记录：@ A 204.232.175.78，其中ip地址在Ref3中可以查询，但是CNAME文件不可以直接设置为两个，如果需要添加，参见Ref4


#Reference:#

[搭建一个免费的，无限流量的Blog----github Pages和Jekyll入门](http://www.ruanyifeng.com/blog/2012/08/blogging_with_jekyll.html)

[使用Github Pages建独立博客](http://beiyuu.com/github-pages/)

[My custom domain isn't working](https://help.github.com/articles/my-custom-domain-isn-t-working)

[Setting up a custom domain with Pages](https://help.github.com/articles/setting-up-a-custom-domain-with-pages)

<p>Posted by randombug @ {{ page.date | date_to_string }}</p>
