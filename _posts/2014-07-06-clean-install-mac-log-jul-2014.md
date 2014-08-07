---
layout: post
title: "Clean Install Mac Log Jul 2014"
description: "又名简平快的中二的折腾：系统重装"
category: Mac
tags: [App]
comments: true
share: true
---

## Contents
{:.no_toc}

* 
{:toc}

<!--more-->

2014-07-19 18:27:31

- KM = Keyboard Maestro
- 或 != aka (“或”不是“又名”的意思，而是逻辑运算符“逻辑或”)
- 或者说 = aka = 又名
- -> = 触发
- A OR B TO C OR D; 为什么就不能像 AppleScript 那样写 `set {A, B} to {C, D}` 或者像 Python 那样写 `a, b = c, d`？

## Notes

1. 版权所有，未经允许，不得转载；之前都是英文，所以没有这个问题；不过这篇全是情绪化的东西，没人会转
2. 凡是一句自然语言能“描述”的事情绝对打死也不说两句
3. 把话说彻底，把命令说干净，方便我或其他人像机器人一样地执行，不要藏，机器人也不会猜；就当主体与客体存在于乌托邦中，没有 power structure 好了
4. 无限扩张，不求死的系统性，但求一种生命力；但假设可穷举，那么务必一个不漏，笨地恐怖地完成
5. 2和3是强化机械性，4是给予机械生物本体论
6. 以下 GUI 操作将来要不 KM 化，要不去 google 对应的终端命令
7. 本来是想全中文的，但是系统界面语言是英文，所以就不方便临时译成中文给别人看。算了吧，系统界面语言通通换成英文吧，这样可以拿英文的菜单项目名称和出现的英文的错误提示去谷歌，换成中文的话，绝对事倍功半。
8. 无耻地先放下路线图，能否实现看现实条件了；搜“希望学”
9. 本地是露骨的民哲 (但我未入门吧康德都没看过) 风
10. 这篇之后有后续
	- LaTeX 命令的笔记
	- 一本微积分的书的笔记 (无人帮助下的自学)
	- Stata 命令的笔记 (之所以不说计量经济的笔记是因为我自知是学渣而且这门科挂了, 而且害得我最近心神不定)
11. 自从目睹那位西班牙人不会从零开始教学生计量经济之后，我就用自己的行动, e.g. 建和写这个博客, 来报复此类行为; 我恨老师有“关我屁事”属性的所谓的“自觉找老师问问题”和老外的当遇到困境时表现出很愿意帮助你的无更多行动的“怜悯”, 也许是我被举国填鸭体制填惯的原因吧 (不要以资源不够时间不够为借口, 系统性缺陷就是理念存在物的不完美!) 或者个人实在情商太低智商太低的关系吧以至于研究生快结束时还不能习惯普世的大学制度; 那位高三时唯一实践“自觉找老师问问题”的老师警告我说还这样到了大学会完蛋, 嗯, 我真的完蛋了; 像我这样自恋的人真的挣扎地要逃离无意义且费力的与别人的 talk.
12. 这篇还会更新的。我会打时间戳作为标记的。

## Steps

### Install and Update System

**For first-time users:** 插入安装盘，开机，按住⌥不放 > 选安装盘 > 菜单栏 disk utility > 点左栏第一个 > Erase > type in "Macintosh SSD" > Erase button > 离开 disk utility 开始安装系统 > 等17分钟 > 开始设置桌面，用时3分钟 > 进入桌面，共用时20分钟 > appstore update sys (to 10.9.4); 15分钟下载; 重启后8分钟安装后进入桌面。全部加起来，用时43分钟。

### Fuck Animation

It's hatred so I'm not ashamed.

{% highlight bash %}
defaults write com.apple.finder AnimateSnapToGrid -bool false && defaults write com.apple.finder DisableAllAnimations -bool true && defaults write com.apple.finder ZoomRects -bool false && defaults write com.apple.finder AnimateInfoPanes -bool false && defaults write com.apple.finder QLEnableSlowMotion -bool false && defaults write com.apple.finder PathBarRootAtHome -bool true && defaults write com.apple.dock springboard-show-duration -float 0.1 && defaults write com.apple.dock springboard-hide-duration -float 0 && defaults write com.apple.dock expose-animation-duration -float 0 && defaults write com.apple.dock workspaces-edge-delay -float 0 && defaults write NSGlobalDomain NSWindowResizeTime -float 0.1 && defaults write NSGlobalDomain NSAutomaticWindowAnimationsEnabled -bool false && defaults write NSGlobalDomain AppleShowAllExtensions -bool true && defaults write com.apple.dashboard mcx-disabled -boolean YES && defaults write com.apple.dock persistent-apps -array-add “{tile-data={}; tile-type=‘spacer-tile’;}” && killall Dock
{% endhighlight %}

**For first-time users:** meanings see [Appendix 1](#Fuck_Animation_Commands), the last third one is to disable dashboard and the last second one is to add a spacer to divide "kept in Dock" apps and non-"kept in Dock" apps.

### System Preferences

- `F2` x4; `F5` till 0
- line 2 `Trackpad` > tab1 v `Tap to click`, `Three finger drag`; tab 3 v App Expose
- *Oh, why cannot Apple do the following for me?*

#### Line 1

- General
	- `Appearance` > `Graphite`
	- `Highlight color` > `Graphite`
	- `Sidebar icon size` > `Small`
- Dock
	- `Minimize windows using` > `Scale effect`
	- v `Double-click a window’s title bar to minimize`
	- v `Minimize windows into application icon`
	- x `Animate opening applications`
- Mission Control
	- x `Automatically rearrange Spaces based on most recent use`
	- `Hot Corners` > choose any one for `Put Display to Sleep`
- Security & Privacy
	- `General` > `Allow apps downloaded from` > `Anywhere`

#### Line 2

- Keyboard
	- `keyboard` > `Modiﬁer Keys…` > `Caps Lock Key` > `No Action` *so I can remap Caps Lock key next*
	- `Input Sources` > Add `Chinese (Simpliﬁed)` > `Pinyin - Simpliﬁed`
- Sound
	- x `Show volume in menu bar`

#### Line 4

- Date & Time
	- choose `Apple Europe (time.euro.apple.com.)`
	- `Clock` > `Show date`
- Time Machine
	- x `Show Time Machine in menu bar`

### Finder

*Oh, why cannot Apple do the following for me?*

- `⌘,`
	- tab 1
		- x `External disks & CDs, DVDs, and iPods`
		- `All My Files` > `Documents`
	- tab 3
		- x `All My Files`
		- x `AirDrop`
		- x `Back to My Mac`
		- x `Connected servers`
		- x `Bonjour computers`
	- tab 4
		- v `Show all filename extensions`
		- x `Show warning before changing an extension`
		- `When performing a search:` > `Search the Current Folder`
- `⌥⌘P`; `⌘/`

### Browser

You can 1) use Safari to download app (normally .zip and will be automatically opened or unzippped) 2) use Chrome instead and unzip .zip manually 3) use Chrome > install Hazel > import Hazel rules > let Hazel automatically move .app to Application folder and move .zip to Trash

This time I did in the 2nd way.

- install MAS 1Password > create a new vault > import .1pif > x `Lock after computer is idle for 5 minutes`, `Use rich icons`
- install Chrome <https://www.google.com/chrome/browser/> > log in Google account > input sync passcode > `Advanced sync settings` > x `Apps`, `Autofill`, `Themes`, `Passwords`

**For first-time users:**

- Manage search engines
	- 的确是好多人不知道事半功倍地搜索 see [Appendix 2](#Custom_Search_URLs); *我是百度搜索无脑黑；虽然身在国外，但是强烈抗议国内封杀谷歌搜索的行为*
- Privacy
	- `Content settings…` > do not allow `Location`, `Notifications`, `Mouse cursor`, `Media`, `Unsandboxed plug-in access`, `Automatic Downloads`
- Passwords and forms
	- x all
- Languages
	- Add `Chinese (Simplified Han)`, `Chinese`, `Chinese (Traditional Han)` *so that Wikipedia can display Simplified Chinese by default instead of Traditional Chinese; 在这里抗议“繁体字的使用”的道德绑架（“民主”、“自由”的道德绑架同理，“左”就来骂我吧），在网上积极推广繁体字使用且把繁体字和有文化素养划等号的但其生活环境被简体字环绕的人就来骂我反智吧，我的原则就是简平快*
- Extensions
	- 1Password 安装 1Password 后打开 Chrome 自动装的
	- Adblck Plus 如果中文的广告都像 V2EX 那样懂得保护用户体验而不像 YYeTs 那样狰狞，我就不用装 Adblck Plus 了
		- tap on its icon in the line of address bar > x `Show number in icon`
	- Don't track me Google 安装后能复制没有转向的谷歌搜索结果的 URL
	- Dracula Theme for DevTools
	- Evernote Web Clipper
	- Vanilla Cookie Manager 定时清除白名单外的 cookies
		- 添加一些网址到白名单
	- Vimium
	- 删除 Google Docs

### Apps From MAS

- [Install MAS Apps](#Install_MAS_Apps)
- [Essential MAS Apps](#Essential_MAS_Apps)
- [Non-Essential MAS Apps](#Non-Essential_MAS_Apps)
- additional MAS apps see [Appendix 3](#Additional_MAS_Apps)

*举个d3的例子，不同的职业技能设计，build 考虑的方面也不一样；part 6 和 7 仅仅是我，既不是程序员也不是设计师也不是学霸但目前近乎是学渣 (最近好狼狈, 唉不说了) 的我的 build*

Install all apps first and then change settings.

#### Install MAS Apps

##### I

1. 1Password
2. BetterSnapTool
3. Command-C
4. Eudic
5. Keynote, Numbers, Pages
6. Moom
7. SnappyApp

##### II

1. 1Checker
2. BetterZip
3. Gemini
4. MindNode Pro
5. Movist
6. Picatext
7. Pixelmator
8. RapidClick
9. Reeder 2
10. Sketch 3
11. Skitch
12. Tweetbot
13. Unibox
14. WeiboX
15. Xcode

#### Essential MAS Apps

1. 1Password
	- 跟密码或序列号有关的*一切*在这里
	- `⌘,`
		- tab 1: x `Show mini app icon in the menu bar`
		- tab 2: x `Lock on sleep`
		- tab 4: x `Animate form filling`
2. BetterSnapTool
	- 窗口管理
	- `⌘,`
		- tab 1: v `Start BetterSnapTool everytime your Mac starts up`
		- tab 2: x `Animated`, `Use rounded corners`
		- tab 3 (here `⌘` OR `⇧` TO `right ⌘` OR `right ⇧`)
			- `maximize` `⌘/`
			- `left half` `⌘←`
			- `right half` `⌘→`
			- `top half` `⌘↑`
			- `bottom half` `⌘↓`
			- `center` `⇧\`
			- `top left quarter` `⇧↑`
			- `top right quarter` `⇧→`
			- `bottom left quarter` `⇧←`
			- `bottom right quarter` `⇧→`
			- `left third` `⌘[`
			- `middle third` `⌘\`
			- `right third` `⌘]`
			- `move to top left, without resizing` `⇧[`
			- `move to top right, without resizing` `⇧]`
			- `restore old window position` `⇧⌫`
		- tab 5: `Move windows` `fn`, `Resize windows` `fn^`
3. Command-C
	- 从 Mac 的 1Password 发密码给 iOS 设备 (或另一个 Mac)，在正在用 Mac 的情况下*绝对*比拿起 iOS 设备打开 1Password for iOS 再复制密码*快*; 从 Mac 发图片给 iOS 设备 (或另一个 Mac); 不得不说几个月后我用上 Yosemite 正式版时这个 app 的命运或者说存在会变
	- `⌘,`
		- tab 1: v `Launch Command-C at login`
	- On iPhone, add Mac device
4. Eudic
	- light peek 是 killer feature (不时怎么现在触发 light peek, 自动查剪贴板内容，目前感觉甚好，几天后就不一定了)
	- `⌘,`
		- tab 1: x `启动时显示在线新闻以及英语资源`
		- tab 2: x all
		- tab 5: `激活 Light Peek`, `right ⌘`; delete/cancel '翻译选中的内容'的'⇧⌘2'
5. iWork: Keynote, Numbers, Pages
	- 仅仅是重要文件的不重要的打开方式 (打开仅仅是看)，甚至连编辑的功能也不需要
6. Moom
	- 用来统一窗口大小帮助 KM 不“因为窗口大小不一样而出错”
	- `⌘,`
		- tab 1: v `Launch automatically on login`; x `Show settings on launch`; set to `Run as menu bar application`
		- tab 2: v Enable Move & Zoom grid with 6 x 4 cells
7. SnappyApp
	- 如果说你置顶窗口只是为了看不活动的文字或图像，那么不要用 Afloat 这个 SIMBL app (谷歌搜索说 SIMBL 改了系统，对系统稳定性不好，暂且这么理解吧) 用 SnappyApp 吧

#### Non-Essential MAS Apps

Non-essential MAS apps are not in my workflows.

1. 1Checker 找语法错误
2. BetterZip 能预览压缩包内容；能用空格触发 quick look 预览压缩包内容；插件见 **Other Non-Essential Apps** > BetterZipQL
3. Gemini 找重复文件
4. MindNode Pro 直观简洁的思维导图
5. Movist 视频播放器
	- `⌘,`
		- last tab > tab 2 > add `Downloads` and `Desktop` folders
6. Picatext 可以把不能选中的文字 (比如菜单、按钮、图片、PDF、网页里的 flash 图像、视频字幕) 弄到剪贴板上；OCR 识别率挺高的；格式乱 (英文断词出现类似"wor- d"中的多余的"- "、一个句子断在两行) 的问题可以靠 KM 的 replace clipboard 解决 (很多人不知道断行符的存在，更别提断行符可以用空字符替代后变两行为一行)，太简单了不值一提
7. Pixelmator 希望学
8. RapidClick 跟命令汗界面 (CLI) 相比，一些不为用户考虑的图形界面 (GUI) 真的很让人忧伤，比如一连串的数量超过十个的没有提供全部打勾或全部取消打勾的勾选框，比如 Fancy 网站的设置，幸运的是，你能拿 RapidClick 解忧
9. Reeder 2 信息源之一
	- add my accounts
10. Sketch 3 希望学
11. Skitch 注释得更容易看见
12. Tweetbot 非社交地收集信息来说，目前因为没有系统性地 channel，所以没用，哪天有构建阴谋论的社科功底后再来 channel 会更有用，但那时应该用自己写的 app 了
	- add my account
13. Unibox 收邮件
	- add my accounts
14. WeiboX 非社交地收集信息来说，目前因为没有系统性地 channel，所以没用，哪天有构建阴谋论的社科功底后再来 channel 会更有用，但那时应该用自己写的 app 了; 我再次黑一下 Heiti SC (黑体-简) 的英文字体，太扭曲了！不知现在 Miao 有没有改默认字体
	- add my account
15. Xcode 希望学; 其实说装 Xcode beta 更恰当


### Apps From Official Websites

- [Install Other Apps](#Install_Other_Apps)
- [License the Apps](#License_the_Apps)
- [Other Essential Apps](#Other_Essential_Apps)
- [Other Non-Essential Apps](#Other_Non-Essential_Apps)

Install all apps first, and then paste license keys OR drag and open from 1Password TO the apps OR Finder, and last change settings.

Some process takes time so we can put them before others:

- 下载 MacTeX 但也可以用上次下载下来的文件，因为它更新慢
- 同步 Evernote *<http://evernote.com/download/>*
- 同步 Dropbox *<https://www.dropbox.com/downloading>*

#### Install Other Apps

##### I

1. Seil <https://pqrs.org/macosx/keyremap4macbook/seil.html.en>
2. KeyRemap4MacBook <https://pqrs.org/macosx/keyremap4macbook/>
3. Keyboard Maestro <http://www.keyboardmaestro.com/>
4. Adobe Digital Editions <http://www.adobe.com/uk/products/digital-editions/download.html>
5. Alfred 2 <http://www.alfredapp.com/#download>
6. Evernote *<http://evernote.com/download/>*
7. Hazel <http://www.noodlesoft.com/Products/Hazel/download>
8. iTerm2 <http://www.iterm2.com/>
9. MacTeX <http://mirror.ctan.org/systems/mac/mactex/MacTeX.pkg>; 下载慢, 最好留着安装包
10. Marked 2 *<http://marked2app.com/download/Marked.zip>*
11. nvALT <http://brettterpstra.com/projects/nvalt/#dl>
12. Skim <http://skim-app.sourceforge.net/>
13. Snagit *<http://www.techsmith.com/download-snagit-mac-thankyou.html>*
14. Sublime Text 3 <http://www.sublimetext.com/3>
15. TextExpander <http://smilesoftware.com/TextExpander/>
16. OnyX <http://www.titanium.free.fr/downloadonyx.php>

##### II

1. Air Video Server HD *<http://download.inmethod.com/current-osx>*
2. BetterZipQL <https://github.com/sindresorhus/quick-look-plugins#betterzipql>
3. Dropbox *<https://www.dropbox.com/downloading>*
4. GitHub *<https://central.github.com/mac/latest>*
5. iStat Menus *<http://download.bjango.com/istatmenus/>*
6. Office 安装文件在移动硬盘里；更新慢
7. R <http://cran.rstudio.com/bin/macosx/>
8. RStudio <http://www.rstudio.com/products/rstudio/download/>
9. Thunder <http://mac.xunlei.com/>
10. VLC <http://www.videolan.org/vlc/>
11. Bartender *<http://www.macbartender.com/Demo/Bartender.zip>*
12. Little Snitch <http://www.obdev.at/products/littlesnitch/download.html>

#### License the Apps

- Keyboard Maestro
- Alfred 2 with Powerpack
- Hazel
- Marked 2
- Snagit
- Sublime Text 3
- TextExpander
- iStat Menus
- Office
- Bartender
- Little Snitch

#### Other Essential Apps

1. [Seil](https://pqrs.org/macosx/keyremap4macbook/seil.html.en) 帮助增加快捷键容量
	- `⌘,`
		- tab 1: change `Caps Lock` to `80`; under `Other Keys`, change `Command_R` to `64`, `Option_R` to `106`, and `Shift_R` to `79`.
2. [KeyRemap4MacBook](https://pqrs.org/macosx/keyremap4macbook/) 增加快捷键容量
	- `⌘,`
		- last tab: `Open private.xml` > paste my old private.xml to overwrite the file
		- tab 1: `ReloadXML` and check all before `General`
3. [Keyboard Maestro](http://www.keyboardmaestro.com/) 万能的 Mac 自动化枢纽
	- import all macros
	- disable `Switcher Group`
	- `⌘,`
		- tab 1 > v `Launch Engine at Login`
	- 终端，见 <http://www.keyboardmaestro.com/documentation/6/preferences.html#preferences_other>

    defaults write com.stairways.keyboardmaestro.engine InterActionDelay -float 0.2 && defaults write com.stairways.keyboardmaestro.editor DisableAnimation -bool YES && defaults write com.stairways.keyboardmaestro.engine DisableAnimation -bool YES && defaults write com.stairways.keyboardmaestro.engine RecordingCountDown -int 3

4. [Adobe Digital Editions](http://www.adobe.com/uk/products/digital-editions.html) 看 DRM 保护的电子书或放置将要被破解 DRM 保护的电子书；破解用 Kevin Pan 开发的 eBook DRM Removal，注意在一些国家破解 DRM 保护是违法行为
	- log in
5. [Alfred 2 with Powerpack](http://www.alfredapp.com/) 计算并粘贴结果, 忘记拼写时模糊找英文单词并粘贴结果，看并粘贴剪贴板历史；它的 workflow 看起来好神秘，不如用 KM 完成
	- `⌘,`
		- tab 2: `Dictionary` change to `d`, `s`; `Clipboard`, v `Persist for 24 Hours`, set shortcut to `^⌥C`
		- tab 4 > tab 3
			- v `Hide hat on Alfred window`
			- v `Hide prefs cog on Alfred window`
			- v `Hide menu bar icon`
			- x `Fade in Alfred Window`
6. [Evernote](http://evernote.com/) 支持 AppleScript (<- Hazel) 创建笔记；支持 Sublime Text 3 通过 bordaigorl 的 [sublime-evernote](https://github.com/bordaigorl/sublime-evernote) 插件写 markdown 创建笔记
	- v `Stay logged in when log in`
7. [Hazel](http://www.noodlesoft.com/hazel.php) 能 watch Finder 且 -> shell script 或 AppleScript
	- import rules
8. [iTerm2](http://www.iterm2.com/)
	- `git` and install the command line developer tools; `curl -L http://install.ohmyz.sh | sh` to install [oh-my-zsh](https://github.com/robbyrussell/oh-my-zsh)
9. [MacTeX](https://tug.org/mactex/) 论文排版；含简平快的 BibDesk，代替自动匹配精度不高而浪费用户时间的 Papers 3
10. [Marked 2](http://marked2app.com/) 用来预览 Sublime Text 3 的 markdown 然后导出为 PDF；Marked 2 提供了很多渲染 markdown 的样式
	- download MarkedBonusPack from <http://support.markedapp.com/kb/how-to-tips-and-tricks/marked-bonus-pack-scripts-commands-and-bundles> and then unzip it and move `Marked.sublime-build` to `~/Library/Application Support/Sublime Text 3/Packages/User/` and then Sublime Text 3 > `Tools` > `Build System` > `Marked`
11. [nvALT](http://brettterpstra.com/projects/nvalt/) 极简，simple plain text and markdown notebook app
	- `⌘,`
		- tab 2: `Read notes from folder` set to the one I use.
12. [Skim](http://skim-app.sourceforge.net/) 支持 AppleScript 的 PDF reader
13. [Snagit](http://www.techsmith.com/snagit.html) 截 GUI 元素的图；*我不知道像 Snagit 或 Adobe Creative Suite 要求用户在重装 app 时再次打开网页填用户信息的意义何在？上次填过的表为什么要再填一遍，难道这些公司没有保存吗？为什么要做浪费用户时间的设计，出于自己无能导致的无意识还是无所谓导致的恶意？*
	- `⌘,` tab 1 > choose `Menu Bar Icon`
14. [Sublime Text 3](http://www.sublimetext.com/3) 特色是 multiple selection; 容易找容易看明白用途的各种插件
	- `^`` and paste the code in <https://sublime.wbond.net/installation> to install Package Control
	- install packages:
		- AlignTab 对齐 markdown 或 LaTeX 的表格
		- Evernote 用 markdown 写，拿 rendered 后的样子创建 Evernote 笔记；支持 code block，但是不支持“高级的”代码高亮
		- Insert Nums 按 ⌘⌥N 输入有序序列比如数字、字母
		- LaTeXTools 生成 PDF 并在 Skim 显示
			- `LaTeXTools: you need to migrate your preferences. See the README file for instructions.` To solve, ⌘⇧P > input `mig↩`
		- WordCount 字数统计
			- menu bar > `Preferences` > `Package Settings` > `Word Count` > `Settings - Default` > `⌘A` then `⌘C` next menu bar > `Preferences` > `Package Settings` > `Word Count` > `Settings - User` > `⌘V` > replace `"enable_count_chars": false` with `"enable_count_chars": true`
	- **For first-time user:**
		- to install a package, `⌘⇧P` > `inst↩` > input package name `↩`
		- to change colour scheme, menu bar > `Preferences` > `Color Scheme` > custom color scheme
15. [TextExpander](http://smilesoftware.com/TextExpander/) 输入时自动替换字符串，还带输入框
	- `⌘,`
		- tab 3: x `Show main window at Login`
		- tab 4: `Dropbox` > `Link to Dropbox`
16. [OnyX](http://www.titanium.free.fr/)
	- last 2nd tab > set `Speed of display of sheets` to `Very Fast` (I discovered that this setup is more faster than what I can do with terminal)
	- `⌘,`
		- 4th tab> `Disable confirmation message`; 5th tab > `Don't check` all
	- routinely, 4th tab > 2nd tab > last 2rd item `QuickLook` (I'm sure about the CLI command to remove / clean quicklook cache; so this's convenient one)

#### Other Non-Essential Apps

Non-essential MAS apps are not in my workflows.

1. [Air Video Server HD](http://www.inmethod.com/airvideohd/index.html) 让 iPad 或 iPhone 播放局域网内 Mac 的视频文件，速度快
2. [BetterZipQL](https://github.com/sindresorhus/quick-look-plugins#betterzipql) 一个 quick look 插件
3. [Dropbox](https://www.dropbox.com/) 同步 TextExpander 的 snippets；还能 (但目前没用来) 保存 iOS app 产生的数据；-> Hazel > shell script 或 AppleScript；但目前 iOS to Mac 的 workflow 没有很重要的
	- Finder > remove Dropbox icon from sidebar
4. [GitHub](https://mac.github.com/) 快速搭 Mac-GitHub 环境
	- log in and clone repos to Mac
5. [iStat Menus](http://bjango.com/mac/istatmenus/) 看网速、温度
	- left only `Network` and `Sensors`; under `Network` OR `Sensors`, drag arrows OR `SEN` away
6. Office for Mac 2011 仅仅是 iWork 的微软字体包而已，仅仅如此而已
	- remove Microsoft icons from Dock 谁允许你往 Dock 加图标的？只有你一个这么干的！
	- update
7. [R](http://www.r-project.org/)
8. [RStudio](http://www.rstudio.com/) R 语言
9. [Thunder](http://mac.xunlei.com/)
	- log in
	- `⌘,`
		- tab 3 > 卸载 Chrome 扩展
		- last tab > v all
10. [VLC](http://www.videolan.org/vlc/) 解码后提供给 Air Video 的 iOS 端提供视频
11. [Bartender](http://www.macbartender.com/)隐藏菜单栏 app 图标
	- `⌘,` tab 2 > v `Launch Bartender at Login` and under tab 1:
		- set to `Show in Bartender Bar, not in Menu Bar`
			- AirPrt 都在自己屋里
			- Battery 都在自己屋里
			- BetterSnapTool 其 Snap Areas 有时可能会有用
			- Dropbox 有时可能会看同步的情况
			- Evernote 没理由
			- Hazel 其 Run Rules 有时可能会用到
			- KM 没理由
			- KeyRemap4MacBook 没理由
			- Moom 没理由
			- Snagit 没理由
			- SnappyApp 没理由
		- set to `Completely Hide Menu Bar Item`
			- Bluetooth 虽然买了很多苹果自己家的外设，但是用的不多
			- Notification Center 用的不多
			- Spotlight 用的不多
		- keep unchanged and reasons
			- Command-C 如果隐藏，作用失效
	- 按 `⌘` 不放把 Bartender 菜单栏图标拖到菜单栏右末端
12. [Little Snitch](http://www.obdev.at/products/littlesnitch/index.html) 防止 app 上传隐私信息
	- `⌘N`
		- add `Google Chrome` allowing any server with `80` `port` and `tcp` `protocol` (其实我不知道什么是 TCP) and 443 port with tcp protocol
		- add `Thunder` allowing any server with any port and any protocol
		- 勤用 ⌘N 为新 app 创建规则，和 ⌘D 来为已存在 app 创建规则

## OS X Keyboard Shortcuts

**This part is for first-time users only.**

### Stock Keyboard Shortcuts

#### Global

- `^click` is right click
- `^⌥⌘P` OCR use picatext on image and copy texts to clipboard
- `⌘\` use 1Password to log in
- `⌘⇧2` use snappyapp to take a screenshot and put it on top of all windows
- `⌘⇧3` and then space, to take a window screenshot
- `⌘⇧3` take a full desktop screenshot
- `⌘⌃⇧3` copy a full desktop screenshot
- `⌘⌃⇧4` and then space, to copy a window screenshot

#### Within Apps

- Finder and Save Dialog
	- `⌘⇧A` Applications
	- `⌘⇧D` Desktop
	- `⌘⇧H` Home
	- `⌘⇧O` Documents
	- `⌥⌘L` Downloads
	- 所以我选择把文件放在以上文件夹作为一级目录，就因为我点 sidebar 图标需要几瞬间，而我用快捷键只需要一瞬间，而多浪费的那(几-1)瞬间是多么地令我生气
	- `⌘L` Make Alias
- KM
	- tap on icon placeholder then `⌘3` choose icon
	- `⌘K` show actions
	- `⌘N` new macro
	- `⌘R` record
- TextExpander
	- `⌥⌘N` new group
- 1Password
	- `⌘E` Edit/Save
	- `⌥⌘↩` Fill Login in Browser
- Chrome with Vimium
	- `gt` or `gT` move between tabs 当手正在打字时
	- `H` or `L` go back or forward
	- `x` close tab
	- `⌘L` focus address bar
	- `⌘Y` history
	- `⌘⇧D` bookmark all into a folder like saving a session
	- `⌘⇧J` download
	- `⌘⇧T` reopen last closed tab
	- `⌘⌥B` bookmarks
	- `⌘⌥→` or `⌘⌥←` move between tabs 当手放在触摸板时
- Evernote
	- `^⌘A` change account when membership is True
	- `^⌘N` pop up mini
	- `^⌘S` sync
- iTerm2
	- `⌘D` Split Vertically with Current Proﬁle
	- `⌘⇧D` Split Horizontally with Current Proﬁle

### Custom Keyboard Shortcuts

- `右⌘` lightpeek and look up clipboard content
- `右⌘P` use picatext to OCR on image and copy texts to clipboard
- `^⌥C` alfred clipboard manager
- hyper keys

## Appendix 1 Fuck Animation Commands

**Finder**

disable snap to grid animation

{% highlight bash %}
defaults write com.apple.finder AnimateSnapToGrid -bool false
{% endhighlight %}

disable some animations

{% highlight bash %}
defaults write com.apple.finder DisableAllAnimations -bool true
{% endhighlight %}

disable opening files zoom animation

{% highlight bash %}
defaults write com.apple.finder ZoomRects -bool false
{% endhighlight %}

disable animations in Get Info window

{% highlight bash %}
defaults write com.apple.finder AnimateInfoPanes -bool false
{% endhighlight %}

disable slow-motion animation when press shift

{% highlight bash %}
defaults write com.apple.finder QLEnableSlowMotion -bool false
{% endhighlight %}

other... make ~ as path bar base location

{% highlight bash %}
defaults write com.apple.finder PathBarRootAtHome -bool true
{% endhighlight %}

**Launchpad**

speed fade-in

{% highlight bash %}
defaults write com.apple.dock springboard-show-duration -float 0.1
{% endhighlight %}

speed fade-out

{% highlight bash %}
defaults write com.apple.dock springboard-hide-duration -float 0
{% endhighlight %}

Mission Control

speed show and hide animation

{% highlight bash %}
defaults write com.apple.dock expose-animation-duration -float 0
{% endhighlight %}

reduce window drag delay

{% highlight bash %}
defaults write com.apple.dock workspaces-edge-delay -float 0
{% endhighlight %}

**Other**

speed roll out animation of save dialog

{% highlight bash %}
defaults write NSGlobalDomain NSWindowResizeTime -float 0.1
{% endhighlight %}

speed opening files zoom animation

{% highlight bash %}
defaults write NSGlobalDomain NSAutomaticWindowAnimationsEnabled -bool false
{% endhighlight %}

other... show file extension globally

{% highlight bash %}
defaults write NSGlobalDomain AppleShowAllExtensions -bool true
{% endhighlight %}

## Appendix 2 Custom Search URLs

[↑](#browser)

- g <https://www.google.co.uk/#q=%s>
- p <https://www.google.co.uk/#q=%s&tbs=qdr:y>
- l <https://www.google.co.uk/#q=%s&btnI>
- site javascript:location=‘http://www.google.com/search?num=100&q=site:'%20+%20escape(location.hostname)%20+%20'%20%S'%20;%20void%200 不是我写的，改天研究一下
- it <https://www.google.co.uk/#q=on+the+App+Store+on+iTunes+%s&btnI>
- w <http://en.wikipedia.org/w/index.php?title=Special:Search&search=%s>
- d <http://www.thefreedictionary.com/_/search.aspx?Word=%s>
- acro <http://www.allacronyms.com/%s/abbreviated>
- 信息源
	- v <https://www.google.co.uk/#q=site:v2ex.com%2Ft+%s>
	- z <http://www.zhihu.com/search?q=%s&type=question>
	- 还可以有 github, 众 userscripts alternatives, 但我没到这个境界
- 学术
	- gs <http://scholar.google.co.uk/scholar?hl=en&q=%s>
	- b <http://aleph.nottingham.ac.uk/F/?func=find-b&request=%s&find_code=WTI&adjacent=Y> 嗯，顺便黑一下；因为我在这里实在闲的蛋疼，环境不会给你施压，只能自己来
- 对于还在找 app (我已经找齐了) 的同学
	- a <http://alternativeto.net/SearchResult.aspx?search=%s>
- 对于还在找 rss 源的同学
	- rss <http://fullrss.net/analyze/?url=%s>

## Appendix 3 Additional MAS Apps

[↑](#apps-from-mas)

I don't install additional MAS apps but think they can be useful; I have bought all additional MAS apps.

- Better Rename 9 适合大众；其余的人有的 (e.g. 我) 用 python 的 os.rename
- Caffeine 多显时个别情况；远程使用 (e.g. Air Video) Mac 需要 Mac 不休眠的情况
- ColorSnapper
- Dash 内购已付费版
- Fantastical
- Kaleidoscope 找出多文件间区别
- PopClip 已被能支持 shell script (所以能支持 python) KM 的快捷键触发器或热字符串触发器代替，但对大多数人来说，因使用方法 (用触摸板选中) 自然，是更流行的选择——我的意思是快捷键触发器或热字符串触发器对大多数人来说没“用触摸板选中的触发方式”自然；PopClip 需要自己写，貌似没有入口
- QQ
- Soulver
- The Unarchiver 已被 BetterZip 代替，但对大多数人来说，因免费，是更流行的选择
- Wikibot 实现得不是很完美
- Writer Pro 目测 text statistics 可以自己写；题外话：iOS 上带 text statistics 的很多
- xScope 4 也许用 Pixelmator 或 Sketch 3 时有用，现在 Pixelmator 和 Sketch 3 没学起来，不知道