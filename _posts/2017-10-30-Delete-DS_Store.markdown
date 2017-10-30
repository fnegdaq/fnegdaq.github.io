---
layout: post
title:  "Git使用中 .DS_Store 冲突问题"
date: 2017-10-30 11:20:53 +0800
categories: jekyll update
---
在Mac的使用中，系统会自动在每个目录中生成一个隐藏的 .DS_Store 文件。

在最近的一次使用 git pull 的时候，因为这个文件而产生冲突导致无法拉取，删除解决问题，但是这样每次去单个删除也是一件麻烦的事情。

如果你的项目中还没有自动生成的 .DS_Store 文件，那么直接将 .DS_Store 加入到 .gitignore 文件就可以了。如果你的项目中已经存在 .DS_Store 文件，那就需要先从项目中将其删除，再将它加入到 .gitignore。

#### 删除项目中的所有.DS_Store
{% highlight ruby %}
1.find . -name .DS_Store -print0 | xargs -0 git rm -f --ignore-unmatch
{% endhighlight %}
#### 将 .DS_Store 加入到 .gitignore
{% highlight ruby %}
2.echo .DS_Store >> ~/.gitignore
{% endhighlight %}
#### 更新项目
{% highlight ruby %}
3.git add .
4.git commit -m 'Delete all .DS_Store'
{% endhighlight %}
