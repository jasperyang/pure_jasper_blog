---
layout: post_layout
title: Jekyll入门与进阶
time: 2016年05月22日 星期日
location: 兰州大学
published: true 
excerpt_separator: "#" 
category: Git
---

说点废话

Jekyll + GitHub Pages 用来写博客是一个在我看来很方便很牛的选择（原谅我的愚昧无知~）。像我这种程序小白猿最喜欢的就是找一个能够稍微改改就能拿来给自己用的看上去很不错的东西，今天我就来教教大家搭建一个属于自己的技术博客（简直不能更简单）。

###开始前，看看你的配置是不是符合要求~

__[配置]__

* Ruby（including development headers, Jekyll 2 需要 v1.9.3 及以上版本，Jekyll 3 需要 v2 及以上版本）
* RubyGems
* Linux, Un ix, or Mac OS X
* NodeJS, 或其他 JavaScript 运行环境（Jekyll 2 或更早版本需要 CoffeeScript 支持）。
* Python 2.7（Jekyll 2 或更早版本）

如果你不符合要求，就快去装吧，安装起来都很简单的。自己去[google](www.google.com)吧

###安装 Jekyll
很简单，只需要在终端中输入

	$ gem install jekyll

	
以上的更详细过程大家可以点入 >> [传送门](http://jekyllcn.com/docs/installation/)

###Jekyll 模板
我想大家应该和我一样对于html5+css3有惯性头大偏移症，所以你需要一个简洁漂亮的模板（说不要的你可以走了）

[Jekyll Themes](http://jekyllthemes.org/)去这儿你可以看到很多高大上的你想要的，怎么用~？先别急，往下看。

我选择了一个简洁明亮的模板叫做[easy_pure_blog](http://jekyllthemes.org/themes/easy-pure-blog/)，下面我就这个模板开始讲解~

##-->进入正题啦（jekyll + easy_pure_blog + GitHub Pages 完成一个博客搭建）


1. 下载模板

	在你的电脑里开辟一个用来实验的文件空间

	```
	$ mkdir pure_jasperyang_blog
	```
	
	```
	$ cd pure_jasperyang_blog
	```
	
	```
	$ git clone https://github.com/liungkejin/liungkejin.github.io.git
	```
	
	第一步完成了，也许你会问https://github.com/liungkejin/liungkejin.github.io.git从哪里得到的，其实就是这个作者的库，在[Jekyll Themes](http://jekyllthemes.org/)里面的模板页中有个Homepage，点进去你就可以找到（需要你懂一点点Git）。
	
2. 修改模板
	
	我们需要知道我们想要修改的工程的目录细节，所以先看看目录结构，我在目录树中附上了该文件的作用解释。
	你想要得到下图效果，你的终端应安装了tree。
	
	```
	$ brew install tree
	```
	
	```
	$ tree pure_jasper_blog
	```
	


		pure_jasper_blog/
		
		├── CNAME（别名映射文件，暂时不用管）
		├── Gemfile（ruby工程的依赖文件，暂时不用管）
		├── Gemfile.lock
		├── LICENSE.md
		├── README.md
		├── _assets（放一些图片等）
		│   ├── mobile1.png
		│   ├── mobile2.png
		│   └── normal.jpg
		├── _config.yml（Jekyll最关键的配置文件，里面有一系列的定义）
		├── _data（里面的yml文件和_config.yml类似，定义了工作经历，学历等，可以被下面的html文件使用）
		│   ├── author.yml
		│   └── blog.yml
		├── _drafts
		│   └── PageController.md
		├── _includes（博文以及作者简介的页面的各个组成部分，会被自动组装）
		│   ├── author_header.html
		│   ├── blog_header.html
		│   ├── footer.html
		│   ├── googleanalytics.html
		│   ├── head.html
		│   └── post_footer.html
		├── _layouts（定义了如何组装各种类型的页面）
		│   ├── author_layout.html
		│   ├── blog_layout.html
		│   └── post_layout.html
		├── _posts（这里都是你写的博文，markdown格式）
		│   ├── 2016-03-04-Getting-Started.md
		│   ├── 2016-03-26-Android-Test-Getting-Start.md
		│   ├── 2016-03-27-Publish-AAR-jcenter.md
		│   ├── 2016-04-03-jekyll-syntax-highlight.md
		│   ├── 2016-04-04-ExRecyclerView-Usage.md
		│   ├── 2016-04-06-Developing-Android-With-Kotlin.md
		│   ├── 2016-04-10-Custom-NavigationView-Problems.md
		│   ├── 2016-04-12-Publish-Kotlin-Lib-To-Jcenter.md
		│   └── 2016-05-22-start-to-build-a-blog.md
		├── _site（这里的文件都是利用上面的配置以及文件自动生成的，用于挂在服务器上）
		│   ├── 2016
		│   │   ├── 03
		│   │   │   ├── 04
		│   │   │   │   └── Getting-Started.html
		│   │   │   ├── 26
		│   │   │   │   └── Android-Test-Getting-Start.html
		│   │   │   └── 27
		│   │   │       └── Publish-AAR-jcenter.html
		│   │   ├── 04
		│   │   │   ├── 03
		│   │   │   │   └── jekyll-syntax-highlight.html
		│   │   │   ├── 04
		│   │   │   │   └── ExRecyclerView-Usage.html
		│   │   │   ├── 06
		│   │   │   │   └── Developing-Android-With-Kotlin.html
		│   │   │   ├── 10
		│   │   │   │   └── Custom-NavigationView-Problems.html
		│   │   │   └── 12
		│   │   │       └── Publish-Kotlin-Lib-To-Jcenter.html
		│   │   └── 05
		│   │       └── 22
		│   │           └── start-to-build-a-blog.html
		│   ├── CNAME
		│   ├── Gemfile
		│   ├── Gemfile.lock
		│   ├── LICENSE.md
		│   ├── README.md
		│   ├── about.html
		│   ├── assets
		│   │   ├── css
		│   │   │   ├── blog.css
		│   │   │   ├── bootstrap-theme.css
		│   │   │   ├── bootstrap-theme.css.map
		│   │   │   ├── bootstrap-theme.min.css
		│   │   │   ├── bootstrap.css
		│   │   │   ├── bootstrap.css.map
		│   │   │   ├── bootstrap.min.css
		│   │   │   ├── font-awesome.min.css
		│   │   │   ├── highlight.css
		│   │   │   ├── icard_resume.css
		│   │   │   └── syntax.css
		│   │   ├── demo
		│   │   │   └── exrecyclerview-demo.gif
		│   │   ├── files
		│   │   │   ├── dokka-fatjar.jar
		│   │   │   └── tools.jar
		│   │   ├── fonts
		│   │   │   ├── FontAwesome.otf
		│   │   │   ├── fontawesome-webfont.eot
		│   │   │   ├── fontawesome-webfont.svg
		│   │   │   ├── fontawesome-webfont.ttf
		│   │   │   ├── fontawesome-webfont.woff
		│   │   │   ├── fontawesome-webfont.woff2
		│   │   │   ├── glyphicons-halflings-regular.eot
		│   │   │   ├── glyphicons-halflings-regular.svg
		│   │   │   ├── glyphicons-halflings-regular.ttf
		│   │   │   ├── glyphicons-halflings-regular.woff
		│   │   │   └── glyphicons-halflings-regular.woff2
		│   │   ├── img
		│   │   │   ├── avatar.JPG
		│   │   │   ├── bewithyou.jpg
		│   │   │   ├── bg-top.jpg
		│   │   │   ├── bg.jpg
		│   │   │   ├── blog.png
		│   │   │   ├── easy-pure-blog.png
		│   │   │   ├── kejin.png
		│   │   │   ├── navigation-standard.png
		│   │   │   ├── navigation_custom_1.png
		│   │   │   ├── navigation_custom_2.png
		│   │   │   └── zoro.jpeg
		│   │   └── js
		│   │       ├── bootstrap.js
		│   │       ├── bootstrap.min.js
		│   │       ├── html5shiv.min.js
		│   │       ├── jquery.min.js
		│   │       ├── npm.js
		│   │       └── respond.min.js
		│   ├── index.html
		│   └── menu.html
		├── about.html（作者介绍）
		├── assets（各种资源，和android里的res文件一样）
		│   ├── css
		│   │   ├── blog.css
		│   │   ├── bootstrap-theme.css
		│   │   ├── bootstrap-theme.css.map
		│   │   ├── bootstrap-theme.min.css
		│   │   ├── bootstrap.css
		│   │   ├── bootstrap.css.map
		│   │   ├── bootstrap.min.css
		│   │   ├── font-awesome.min.css
		│   │   ├── highlight.css
		│   │   ├── icard_resume.css
		│   │   └── syntax.css
		│   ├── demo
		│   │   └── exrecyclerview-demo.gif
		│   ├── files
		│   │   ├── dokka-fatjar.jar
		│   │   └── tools.jar
		│   ├── fonts
		│   │   ├── FontAwesome.otf
		│   │   ├── fontawesome-webfont.eot
		│   │   ├── fontawesome-webfont.svg
		│   │   ├── fontawesome-webfont.ttf
		│   │   ├── fontawesome-webfont.woff
		│   │   ├── fontawesome-webfont.woff2
		│   │   ├── glyphicons-halflings-regular.eot
		│   │   ├── glyphicons-halflings-regular.svg
		│   │   ├── glyphicons-halflings-regular.ttf
		│   │   ├── glyphicons-halflings-regular.woff
		│   │   └── glyphicons-halflings-regular.woff2
		│   ├── img
		│   │   ├── avatar.JPG
		│   │   ├── bewithyou.jpg
		│   │   ├── bg-top.jpg
		│   │   ├── bg.jpg
		│   │   ├── blog.png
		│   │   ├── easy-pure-blog.png
		│   │   ├── kejin.png
		│   │   ├── navigation-standard.png
		│   │   ├── navigation_custom_1.png
		│   │   ├── navigation_custom_2.png
		│   │   └── zoro.jpeg
		│   └── js
		│       ├── bootstrap.js
		│       ├── bootstrap.min.js
		│       ├── html5shiv.min.js
		│       ├── jquery.min.js
		│       ├── npm.js
		│       └── respond.min.js
		├── index.html（主页）
		└── menu.html（文章页面）
	
	以上，大部分文件中的数据调用都是使用了[Liquid](https://github.com/jasperyang/liquid)语法，简洁方便。如果你很熟悉html，那么你很快就能改好。如果不是你可以先看我下面怎么改，再去慢慢熟悉。
	
	*  config.yml 以及  _data 文件夹内的 author.yml,blog.yml 内的内容显而易见，config.yml 中的 url 属性暂时先不要改，不然本机运行会出问题。
	* 然后就是在 _include 文件中修改，自己看，你会明白的。
	* 其余的修改就是看你自己喜好了，甚至你可以去修改css文件。
	
3. 本机运行
	在 pure_jasper_blog 目录下，终端输入
	
		$ jekyll server
	
	ok，现在你用浏览器登录 `localhost:4000`就可以看到你的博客了，到此为止，你已经完成了80%，剩下的就是将它放到你的`Git`上
	
4. 放到 Git
	* 在你的 Git repo 里 new 一个 pure_jasper_blog
	* 在终端中输入
	
			$ cd pure_jasper_blog
			$ git init
			$ git checkout --orphan gh-pages
			$ git add .
			$ git commit -a -m "first"
			$ git remote add  origin https://github.com/***/pure_jasper_blog.git			$ git push -u origin gh-pages
	
	以上命令都键入后，你可以登录`https://***.github.com/pure_jasper_blog`，和你本地一模一样，大功告成！（***是你的 Git 用户名）
	
###PS:
大家还可以去看看大牛阮一峰的博文。
另外我发现了一个叫on_1y的大牛写的十分详细，大家可以去看看--->[使用 GitHub, Jekyll 打造自己的免费独立博客](http://blog.csdn.net/on_1y/article/details/19259435)
[阮一峰的网络日志](http://www.ruanyifeng.com/blog/2012/08/blogging_with_jekyll.html)
