---
layout: post
title:  Github Pages + Jekyll 搭建个人博客
date:   2021-07-26 20:14:35 +0300
image:  05.jpg
tags:   blog
---

>记录一下博客搭建的过程

# 一、查找教程

参考：https://sspai.com/post/54608

可以完成远程仓库的建立，及其到本地的克隆，同时会了解如何进行远程仓库的管理。

# 二、环境安装

上面提到的文章是在 Mac 下进行的，而 Windows 系统的安装过程有所不同。

访问 https://rubyinstaller.org/downloads/ 可以下载 Ruby 的安装包，这里建议选择网页上粗体的版本进行下载。

虽然会看到上面建议下载较低版本，但亲身测试，低版本问题更多。

下载安装完毕后，在命令行通过 `ruby - v`，`gem -v` 可以验证是否安装成功。

随后运行 `gem install jekyll bundler` 安装 Jekyll，同样可以通过 `jekyll - v` 验证是否安装成功。

# 三、生成页面

继续按照第一步中的文章做。

进入克隆下来的 Github Pages 项目的路径，执行 `jekyll new . --force` 。

再执行 `bundle exec jekyll serve` 就可以通过访问 `127.0.0.1:4000` 本地查看页面了。

# 四、选择主题

相信绝大多数人还是希望自己的博客能有一个好看的界面的，但是并不是每个人都有能力从零开始写一个精美的页面。所以选择主题就显得尤为重要了。

访问 http://jekyllthemes.org/ 选择自己喜欢的主题，下载解压后将文件复制到本地仓库便可运行 `bundle exec jekyll serve`
来尝试本地访问，没问题就可以直接 push ，然后输入自己的域名在互联网上访问自己的博客了。

# 五、问题

如果一切顺利，搭建一个博客也就不会拖这么长时间了。

在此我列出以上述方法搭建博客中可能遇到的问题：

1. Ruby 版本选择

   前面也提到了，我建议下载网页中粗体标识的版本。一开始我以这个版本进行，中间无差错，直到最后运行 `bundle exec jekyll serve` 才报错，当时受到误导以为是版本问题，结果下载了推荐版本反而问题更多。（体现在所用到的各种包之间版本不兼容等）

2. bundle exec jekyll serve cannot load such file -- webrick (LoadError) 解决

   这就是上文提到的我在最后一步遇到的问题，参考 https://github.com/jekyll/jekyll/issues/8523 ，执行 `bundle add webrick`即可。

3. 主题选择

   没错，主题选择也是个问题。因为它可能不被 Github Pages 支持，它可能与你安装的环境不兼容……所以我们也没办法喜欢哪个主题就用哪个。怎么办呢？多选几个一个一个试。

4. 其他

   在执行 `bundle exec jekyll serve`之前，先执行`bundle install`。

   如果还提示缺少某些包，就用 `gem install ……`进行相应安装即可。

------

就写到这。
