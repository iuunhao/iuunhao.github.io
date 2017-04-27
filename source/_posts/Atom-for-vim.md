---
title: Atom配置（VIM党）
date: 2016-03-26 11:48:40
tags: vim emacs atom spacemacs
---

为什么说是Vim党呢？首先我是一个深度的Vim用户，自己的电脑上基本上可以兼容Vim的插件都有，所有浏览器，所有编辑器都是Vim的操作方式，当然包括我现在书写的markdown的软件[EME](https://github.com/egoist/eme)也是兼容的Vim的操作。

自从4年前，一次偶尔的机会接触到了Vim这款编辑器，就深深的被吸引了。

从刚开始实用别人的配置文件，直到最后自己用了2年的时间打磨出了自己的配置文件，我曾经用了1个月的时间翻遍了[VimAwesome](http://vimawesome.com/)的所有插件，从当初100+的插件配置到现在插件也就是10+配置文件也从当初3000+行到现在400+行，开始喜欢修改快捷键，喜欢什么都用插件来代替，到现在全部原生快捷键，能用`VimScript`实现的功能都不会去用插件来代替。

也许我们对一个事物的追求到了一定程度的时候，我就回到起点，感觉一切都是最原始的是最好的。

我写这篇文章呢？

不管是vim 还是Gvim 还是spacemacs 他们都做的很好，也许是自己对UI要求过高吧，Atom的界面做的很棒。

sublime VScode 等等的编辑器，虽然也都有vim的插件支持，但是目前我发现的只有atom的这个插件做的是好的，速度也是相当快的。基本可以平移。
<!--more-->
这里借用作者的一幅图
![](https://camo.githubusercontent.com/8d45d7e4100511d56103b8b8b022ce86deb4b9cc/687474703a2f2f692e696d6775722e636f6d2f556d786a6f63442e676966)

快捷键基本也是通用的(space 代替空格)

### 常用快捷键(也可以自定义)
* SPACE f :显示所有快捷键
* SPACE f f :显示文件列表
* SPACE b b :显示当前buffer
* SAPCE l :移动当前工作区的位置到右侧
* SAPCE k :移动当前工作区的位置到上侧
* SAPCE h :移动当前工作区的位置到左侧
* SAPCE j :移动当前工作区的位置到下侧


这篇文章里面的配置，也许不适合所有人，有几个前提如果你经历过这个过程，也许会对你有帮助，否则，此文也许对你没有任何的帮助。

---

## 基本要求

  * 你使用过vim，曾经用过也可以，最起码这些东西对你而言不是问题[Vim基本快捷键](https://vim.rtorr.com/lang/zh_cn/)
  * 你用过[Spacemacs](http://spacemacs.org/)
  
 如果以上两条你都没问题，那么接下来的内容你也许会感兴趣。
 
## 软件安装
 Atom的安装这里省略。[官网](https://atom.io/)
 
## 基本插件
 下载完成先安装一个插件
 [proton-mode](https://atom.io/packages/proton-mode)
 [Github地址](https://github.com/dvcrn/proton-bin)
 
 安装完成在你的西贡根目录会有个`.proton`的配置文件，Atom的所有配置都需要在这里修改，如果直接在软件内部修改，每次重新启动atom所有的设置都会被重置。
 
```
{
  ;; 层的设置(spacemacs层的概念包含了一系列插件)
  :layers
  [
    :core
    :tools/git
    :tools/linter
    :tools/minimap
    :lang/javascript
  ]
  ;; 自定义添加插件(如果需要安装插件必须在这里添加)
  :additional-packages
  [
    :atom-ternjs
    :tag
    :autocomplete-modules
    :csslint
    :htmlhint
    :pigments
    :atom-beautify
    :open-in-browser
    :tree-view-copy-relative-path
    :pristine-ui
    :duotone-dark-space-syntax
    :emmet
    :docblockr
    :autocomplete-plus
    :auto-id-class
    :glowing-cursor
    :tree-view-tautoresize
    :jumpy
    :stylus
    :atom-pug
    :atom-pug
  ]
  ;; 禁用插件
  :disabled-packages [
    :autoupdate-packages
    :about
    :welcome
    :status-bar
    :zentabs
    :file-icons
    :easy-motion-redux
    :relative-numbers
    :encoding-selector
  ]
  ;; 编辑器的配置
  :configuration
  [
    ["editor.fontFamily" "Office Code pro"]
    ["editor.fontSize" 18]
    ["editor.preferredLineLength" "900"]
    ["editor.tabLength" 4]
    ["editor.tabType" "auto"]
    ["editor.atomicSoftTabs" false]
    ["editor.nonWordCharacters" "./\\()\"':,.;<>~!@#$%^&*|+=[]{}`~?"]
    ["core.themes" ["pristine-ui" "duotone-dark-space-syntax"]]
    ["proton.core.showTabBar" true]
    ["proton.core.relativeLineNumbers" false]
    ["proton.core.inputProvider" :vim-mode-plus]
  ]
  ;; 快捷键设置
  :keybindings {}
  :keymaps [{:selector ".tree-view" :keymap [["escape" "tree-view:toggle"]]}
            {:selector "atom-text-editor.vim-mode-plus:not(.normal-mode)" :keymap [["f d" "vim-mode-plus:activate-normal-mode"]]}
  ]
}
```

我们只需要备份好这个配置文件，就可以，每次启动atom的时候它都会加载这个配置文件，对插件和配置进行重置。

### 在这里我顺便推荐几个资源：
* [EME](https://github.com/egoist/eme) mac下编辑markdown很方便，是我目前发现最好用的一款markdown编辑器
* [VimAwesome](http://vimawesome.com/) 如果你执意用vim的这个网站你必须知道的。vim插件网站
* [Spacemacs](http://spacemacs.org/) 如果你没有用过spacemacs的建议你去看看。
* [Vim基本快捷键](https://vim.rtorr.com/lang/zh_cn/) Vim的基本快捷键，多语言的。