---
layout: post
title:  "Git使用中 .DS_Store 冲突问题"
date: 2017-10-30
categories: jekyll update
---
在Mac的使用中，系统会自动在每个目录中生成一个隐藏的 .DS_Store 文件。

在最近的一次使用 git pull 的时候，因为这个文件而产生冲突导致无法拉取，删除解决问题，但是这样每次去单个删除也是一件麻烦的事情。

# 删除所有 .DS_Store 文件

{% highlight ruby %}
删除项目中的所有.DS_Store。这会跳过不在项目中的 .DS_Store
1.find . -name .DS_Store -print0 | xargs -0 git rm -f --ignore-unmatch
将 .DS_Store 加入到 .gitignore
2.echo .DS_Store >> ~/.gitignore
更新项目
3.git add .
4.git commit -m 'Delete all .DS_Store'
{% endhighlight %}
