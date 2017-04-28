---
title: Sublime配置
date: 2014-09-27 17:40:45
tags: sublime package config
---

说一下我们常用的Sublime编辑器的基本配置，和一些常用的插件。

不废话，先上我们的基本配置文件内容：

```json
{
	"bold_folder_labels": true,
	"caret_extra_bottom": 2,
	"caret_extra_top": 2,
	"caret_extra_width": 3,
	"caret_style": "phase",
	"debug": true,
	"fade_fold_buttons": false,
	"font_face": "Office Code pro",
	"font_size": 26,
	"highlight_line": true,
	"highlight_modified_tabs": true,
	"ignored_packages":
	[
		"Vintage"
	],
	"indent_guide_options":
	[
		"draw_normal",
		"draw_active"
	],
	"jslint":
	[
		"nodejs",
		"~/.config/sublime-text-2/Packages/JSLint/linter.js"
	],
	"line_padding_bottom": 1,
	"line_padding_top": 1,
	"margin": 4,
	"theme": "ayu-dark2.sublime-theme",
	"translate_tabs_to_spaces": true,
	"update_check": false,
	"wide_caret": true,
	"word_separators": "./\\()\"':,.;<>~!@#$%^&*|+=[]{}`~?",
	"word_wrap": true
}
```

<!--more-->

配置里面没有写配色，这个根据自己的喜好自行设置，字体也需要自己去配置，这里我推荐的是[Office Code pro](https://github.com/nathco/Office-Code-Pro)自行下载。


## Package Install

在国内安装sublime的插件经常会出现安装的情况，这个情况很正常，我们不需要做任何处理，在不同的时间多去尝试几次就可以了。安装插件我们需要先安装`Package Control`，这个安装教程网上很多，我这里也就不多解释了，直接贴代码。




sublime2与sublime3的安装有区别，我们根据自己的版本执行对应的命令即可。

从菜单 View - Show Console 或者 ctrl + ~ 快捷键，调出 console。将以下 Python 代码粘贴进去并 enter 执行，不出意外即完成安装。以下提供 ST3 和 ST2 的安装代码：

### Sublime2
```py
import urllib2,os; pf='Package Control.sublime-package'; ipp = sublime.installed_packages_path(); os.makedirs( ipp ) if not os.path.exists(ipp) else None; urllib2.install_opener( urllib2.build_opener( urllib2.ProxyHandler( ))); open( os.path.join( ipp, pf), 'wb' ).write( urllib2.urlopen( 'http://sublime.wbond.net/' +pf.replace( ' ','%20' )).read()); print( 'Please restart Sublime Text to finish installation')
```

### Sublime3
```py
import urllib.request,os; pf = 'Package Control.sublime-package'; ipp = sublime.installed_packages_path(); urllib.request.install_opener( urllib.request.build_opener( urllib.request.ProxyHandler()) ); open(os.path.join(ipp, pf), 'wb').write(urllib.request.urlopen( 'http://sublime.wbond.net/' + pf.replace(' ','%20')).read())
```

重启Sublime Text

快捷键 Ctrl+Shift+P（菜单 – Tools – Command Paletter），输入 install 选中Install Package并回车，输入或选择你需要的插件回车就安装了（注意左下角的小文字变化，会提示安装成功）。

## Package List

[官方插件列表](https://packagecontrol.io/)

* All Autocomplete (补全可以跨文件补全)
* AutoFileName(自动补全文件名)
* ayu(一个很漂亮的配色主题)
* BracketHighlighter(可以高亮代码块)
* Color Highlighter (可以将代码中的所有变量高亮)
* Colorcoder (可以高亮代码中的颜色)
* CSScomb(css排序)
* DocBlockr(js注释文档) 
* Emmet(htmlcss代码补全)
* File History(本地文件会生成版本，可以回滚代码)
* Git(git的所有功能)
* Gitignore(可以自动创建一些常用的git过滤文件)
* HTML-CSS-JS Prettify(htmlcssjs的代码格式化)
* JavaScript Completions(原生js的代码补全)
* JavaScriptNext - ES6 Syntax (ES6代码语法高亮)
* Nodejs(nodejs代码补全)
* SublimeCodeIntel(很强打的一个提示跳转工具)
* SVN(svn)
* Terminality(翻译工具)
* SublimeLinter(语法检测工具)
* SublimeLinter-csslint(css语法检测)
* SublimeLinter-jscs(js语法检测)

以上插件都是一些基本插件，你可以根据自己的工作需要继续添加你所需要的插件。

