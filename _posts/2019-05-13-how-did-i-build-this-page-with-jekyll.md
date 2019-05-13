---
layout: page
title: 我如何製作這個blog？
date: 2019-05-13 15:34 +0800
categories: tutorials
tags: jekyll how-to blog
---

> 學習過程中我遇到不少蠢事情，如果一開始就先知道的話，肯定可以減少時間的浪費。提供幾點作為參考，建議牢記：
- 不要編輯_site資料夾**裡**的文件，是編輯_site資料夾**外**的文件。
- 更改Gemfile，就要**bundle**。
- 更改_config.yml，就要**重啟Server**。
- 別忘了要**Save**，確定你有**Save**，確定你按**Save**時是在Editor的視窗內。

這個Blog使用**Jekyll**製作。Jekyll是一種剖析引擎工具，幫助你快速製作出簡單精巧的靜態網頁，並且直接架設於Github裡，無需付費也可以建立免費的個人網頁。Jekyll同時也是Ruby裡的其中一種Gem，使用起來有點類似Ruby on Rails的邏輯，只是Jekyll構造更簡單，適合剛學習網頁製作的人作為練習使用。

大致上我是依照這樣的流程來執行：

<ol>
<li><a href="#one">安裝Ruby</a></li>
<li><a href="#two">安裝Jekyll Gem</a></li>
<li><a href="#three">安裝Hyde theme</a></li>
<li><a href="#four">解決Jekyll和Hyde的相容問題</a></li>
<li><a href="#five" name="back_to_top">針對網頁架構和視覺作調整</a></li>  
</ol>

---
<h2>1. <a name="one">安裝Ruby</a></h2>  

網路上已經有很多安裝Ruby的教學，所以這裡不再詳細敘述。通常macOS系統都預先安裝，只是版本可能比較舊一些。

如果你不知道要從哪裡開始著手，可以參考這些網站：
* Windows系統: [RubyInstaller for Windows](https://rubyinstaller.org/)
* macOS系統: [(Official) Ruby Programming Language](https://www.ruby-lang.org/en/documentation/installation/)

我使用的Ruby版本是`ruby 2.6.0p0 (2018-12-25 revision 66547) [x86_64-darwin18]`，僅作參考。

---
<h2>2. <a name="two">安裝Jekyll Gem</a></h2>  

開啟Terminal之後輸入：
~~~
> gem install bundler jekyll
~~~
安裝完成後，可以直接透過指令，新建一個Jekyll網頁：
~~~
> jekyll new YOUR_SITE_NAME**
> cd **YOUR_SITE_NAME
~~~
這時可以試試看你所建立的Jekyll專案是否成功：
~~~
> jekyll serve
~~~
此時Terminal畫面上會告訴你，要去哪裡開啟網頁查看。想停止Server時使用`Ctrl-c`快捷鍵。
~~~
    Server address: http://127.0.0.1:4000/blog//
  Server running... press ctrl-c to stop.
~~~
我使用的Ruby版本是`jekyll 3.8.5`，僅作參考。

---
<h2>3. <a name="three">安裝Hyde theme</a></h2>  

這步驟並非必要，可以直接沿用預設的主題就好。如果想試試看不一樣的風格，也可以自己手動更換。網路上有許多主題可以更換，不論是免費或付費都有。以下是Jekyll官網推薦的主題網站：
- [https://jekyllthemes.io/](https://jekyllthemes.io/)
- [http://jekyllthemes.org/](http://jekyllthemes.org/)
- [https://rubygems.org/search?utf8=%E2%9C%93&query=jekyll-theme](https://rubygems.org/search?utf8=%E2%9C%93&query=jekyll-theme)

每個主題的作者都會在其Github專案內提供安裝方式。普通做法是直接把檔案放進資料夾中，最後到Terminal裡用`bundle`就解決。如果作者有提到他的主題有打包成Gem，這樣就只要在`Gemfile`檔案裡做點修改，再去Terminal輸入`bundle`就好，更為輕鬆。  

我使用的主題是[Hyde](https://github.com/poole/hyde)，在其Github專案網頁上有提到：
> Hyde is a theme built on top of Poole, which provides a fully furnished Jekyll setup—just download and start the Jekyll server. **See the Poole usage guidelines** for how to install and use Jekyll.

Hyde主題是從[Poole](https://github.com/poole/poole)主題做修改，再提供他人使用。所以先下載Hyde後，再搭配Poole的安裝說明：
> Folks wishing to use Jekyll's templates and styles can do so with a little bit of manual labor. **Download Poole and then copy what you need** (likely _layouts/, *.html files, atom.xml for RSS, and public/ for CSS, JS, etc.).

把Poole的安裝方式套在Hyde上，也就是將下載的Hyde檔案，全部手動複製到你所創建的Jekyll專案資料夾裡。如果有重複的就直接覆蓋過去。

接著跟剛才相同，先去Terminal輸入`jekyll serve`看看是否能成功開啟網頁
~~~
> jekyll serve
.
.
.
      Generating...
       Jekyll Feed: Generating feed for posts
                    done in 0.852 seconds.
 Auto-regeneration: enabled for '/Users/YOU_USER_NAME/YOUR_SITE_NAME'
    Server address: http://127.0.0.1:4000/blog//
  Server running... press ctrl-c to stop.
~~~

---
<h2>4. <a name="four">解決Jekyll和Hyde的相容問題</a></h2>  

通常到這裡，Terminal畫面會顯示錯誤訊息，而不會像前一步的畫面一樣顯示順利運作。

如果Terminal顯示錯誤訊息是正常情形，因為Hyde已經很久沒更新。距離它最近一次commit的時間是2015年5月12日，而Jekyll則是在2015年10月26日開始進入[v3.0.0](https://jekyllrb.com/docs/history/#v3-0-0)版本，甚至我撰寫的當下已經釋出了v4.0.0.pre.alpha1。Hyde久未隨著Jekyll更新版本，因此設定上的對應有落差。

根據我遇到的經驗，其實沒有想像中的繁雜。Terminal很貼心地指出哪裡出錯，只要一次只修一個接著再`jekyll serve`一次，如果有出現新的錯誤就再修正，沒多久就能看到Server啟動成功的畫面。我修正時忘了留下紀錄，只能照印象說個大概。

最深刻的就是第一個permalink問題，讓我苦惱最久。不過也因此知道Jekyll出問題時要怎麼觀察，就是把Terminal出現的關鍵字拿去Google。這個問題在Terminal上顯示的狀態如下：
~~~
Since v3.0, permalinks for pages in subfolders must be relative to the site
source directory, not the parent directory. Check
https://jekyllrb.com/docs/upgrading/ for more info.
~~~
根據Jykell的[更新說明](https://jekyllrb.com/docs/upgrading/2-to-3/#relative-permalink-support-removed)，從Jekyll 3開始就不再支援Relative Permalink功能。雖然我當下根本不懂是什麼意思，但網頁也有記載，只要去`_config.yml`檔案裡刪去下面這一行即可：
~~~yaml
relative_permalinks: true
~~~
Github也有相關說明可以參考：[Page build failed: Relative permalinks configured](https://help.github.com/en/articles/page-build-failed-relative-permalinks-configured)

Terminal裡出現最多的問題就是**Gem版本不相容**，或者**根本沒安裝**。類似這樣:
~~~
Dependency Error: Yikes! It looks like you don't have pygments or one of its dependencies installed. In order to use Jekyll as currently configured, you'll need to install this gem. The full error message from Ruby is: 'cannot load such file -- pygments' If you run into trouble, you can find helpful resources at https://jekyllrb.com/help/!
Liquid Exception: pygments in /Users/danadanad/Documents/linkchen1982.github.io/_posts/2019-05-07-welcome-to-jekyll.markdown
            ERROR: YOUR SITE COULD NOT BE BUILT:
                  ------------------------------------
                  pygments
~~~
只要Terminal畫面說少了什麼，就到[RubyGems.org](https://rubygems.org/)上搜尋並且安裝即可。以下這幾個是我自己另外選的：
~~~ruby
# /Gemfile

# 我選擇Rough來標示Highlighter功能，pygments.rb似乎也要跟著裝才不會出問題
# http://rouge.jneen.net/
gem 'pygments.rb', '~> 1.2', '>= 1.2.1'
gem 'rouge', '~> 3.3'

# 我將recarpet換成kramdown，因為我比較習慣
# 更詳細的官方說明：https://jekyllrb.com/docs/configuration/markdown/
gem "kramdown"

# If you have any plugins, put them here!
group :jekyll_plugins do
  gem "jekyll-feed", "~> 0.6"
  gem "jekyll-compose"
  gem "jekyll-paginate", "~> 1.1.0"
end
~~~
Rouge能讓這網頁裡顯示彩色般的程式碼外觀。由於使用Rouge，所以也要去`_config.yml`追加一些設定。
~~~yaml
# /_config.yml

# 這裡設定我主要是參照這個網頁：https://frankindev.com/2017/03/18/syntax-highlight-with-rouge-in-jekyll/#theme-and-colour
markdown: kramdown
highlighter: rouge
kramdown:
  # https://kramdown.gettalong.org/parser/gfm.html
  input: GFM
  syntax_highlighter_opts:
    default_lang: html
    css_class: 'syntax'
~~~
其他的我暫時想不到，大概就是見招拆招。

---
<h2>5. <a name="five">針對視覺和網頁架構作調整</a></h2>

Hyde的預設畫面是以黑色為主，Nav在左邊。詳情可以參照Hyde提供的[Demo](http://hyde.getpoole.com/)。接下來我將做些視覺上的改造。

### 將預設主題修改為橘色外觀 ###

根據[Hyde文件](https://github.com/poole/hyde#themes)說明：
> Hyde ships with **eight** optional themes based on the base16 color scheme. Apply a theme to change the color scheme (mostly applies to sidebar and links).

所以我挑選8個預設的顏色之一`.theme-base-09`。到`default.html`裡加入：
~~~html
<!-- /_layouts/default.html -->

<body class="theme-base-09">
  .
  .
  .
</body>
~~~
如果你不喜歡它提供的8個預設主題，可以到原始`hyde.css`做修正：
~~~css
/*  /public/css/hyde.css  */

/* 更改預設的顏色值 */
.theme-base-09 .sidebar {
  background-color: #d28445;
}

/* 或是使用相同架構，自己新造顏色主題 */
.NEW-COLOR-BASE .sidebar {
  background-color: #f4bf75;
}
~~~

### 將Nav移到右側顯示 ###

到`default.html`裡加入`layout-reverse`：
~~~html
<!-- /_layouts/default.html -->

<body class="layout-reverse theme-base-09">
  .
  .
  .
</body>
~~~

### 新建自己的CSS設定 ###

Nav這裡我要修改為靠右顯示、加入社群icon、Copyright縮小、點擊連結時有發亮特效。Jekyll的做法很簡單，直接新建CSS檔即可覆蓋原本的設定，最後記得加入連結到`<head>`裡就好。根據[官方convention](https://jekyllrb.com/docs/step-by-step/07-assets/)，新建assets資料夾與3個子資料夾：
~~~
.
├── assets
|   ├── css
|   ├── images
|   └── js
...
~~~
在`/assets/css`裡新增檔案即可，例如我專為Nav新增的sidebarstyle.css：
~~~css
/*  /assets/css/sidebarstyle.css  */

@charset "utf-8";

/* 全體靠右 */
.sidebar {
  text-align: right;
}

/* 針對「Link Chen」兩字做設定 */
#sidebar-site-title a {
  font-weight: bold;
  font-size: 2em;
  font-family: Georgia, 'Times New Roman', Times, serif;
  text-decoration: none;
}

/* 針對「Link Chen」兩字做發亮特效 */
#sidebar-site-title a:hover {
  text-shadow: 0 0 10px #fff;
  transition: .5s
}

/* 社群icon的排版，使用的icon文字是來自font awesome */
.sidebar-nav ul li{
  display: inline;
  margin-left: 10px;
}

/* 社群icon的大小 */
.sidebar-nav span {
  font-size: 1.5em;
}

/* 針對社群icon做發亮特效 */
.sidebar-nav span:hover {
  text-shadow: 0 0 5px #fff;
  transition: .5s
}

/* Copyright縮小 */
#copyright {
  font-size: .7em;
}
~~~
### URL的設定 ###

網頁的基本路徑我想架設成這樣：

網頁名稱|網址
Home|{{site.url}}
About|{{site.url}}/about
Contact|{{site.url}}/contact
Posts in catgories|{{ site.url }}{{page.url}}

跟URL設定有關的，大致上是這3種：
- 檔案安置的位置
- `_config.yml`設定
- `_posts`資料夾裡每個post所設定的front matter

檔案安置的位置最好解決。例如我想要About網址是`https://linkchen1982.github.com/about`，只要直接創建一個`about.md`檔案即可。又或者你可以先創建一個`about`資料夾，裡面再創建`index.html`檔案，效果是一模一樣。我偏好後者，因為有資料夾可以分類，架構上比較好懂。

`_config.yml`反而比較重要，這會完全影響整個網址的運作方式。開啟`_config.yml`看到這兩行：
~~~yml
# 如果沒有就自己手動加入
url:      /
baseurl:  /
~~~
以我的網頁為例，`url`就會是` {{ site.url }} `，而`baseurl`則是` {{ site.baseurl }} `。但是`_posts`所對應的網址就只會是

` {{ site.url }}/how-did-i-build-this-page-with-jekyll `

，缺少了`tutorials/`這部分。

解決方法是使用Categories功能。首先去`_config.yml`設定post的固定路徑：
~~~yml
# 記得每次更改完_config.yml，都一定要重啟一次jekyll serve

# 你可以比對一下我現在的網址，就是這樣自動生成的。
permalink: /:categories/:title
~~~
接著在post裡的front matter，追加categories：
~~~ruby
---
layout: post
title: 我如何製作這個blog？
date: 2019-05-08 11:17 +0800
categories: tutorials
---
~~~
這樣就不需要特地在資料夾裡新增`tutorials`資料夾，Jekyll會自動幫你安排。

---
## 總結 ##
其實我一開始是打算學習Ruby on Rails，但學了一陣子才發現比我想像還要困難。如果看一下[官方說明文件](https://guides.rubyonrails.org/getting_started.html#creating-the-blog-application)就能明白，光是資料夾的架構組成，Rails比Jekyll複雜更多。Rails還要理解MVC觀念、資料庫的操作...以及一堆我忘了是什麼的什麼，要一個剛學習網路開發的人能短時間內就理解，這要求可能過高。

當時我卡在Rails某個問題，然後在網路上搜尋解答時，突然看到有人說Jekyll比較容易學習，於是我就稍微試玩了一下，接著就黏上了。Jekyll彷彿就是Rails的Lite版，在很多方面來說都是。由於我有稍微先碰一下Rails以後才接觸Jekyll，反而讓我在學Jekyll的過程中更為順暢。當然...不是真的完全順暢，但起碼Jekyll可以讓我靠自己找答案，並且實做出來了。Jekyll的學習過程也讓我知道網路開發資源的豐富性，幾乎我想到什麼點子，立刻搜尋就能看到別人已經發問，並且有很多人回答。如果現在重頭開始學Rails的話，我相信會更容易進展下去。

學習Jekyll時另一個讓我感到驚喜的是Github。以前是聽說過，但不是很理解可以做什麼。現在Github對我來說是一個全新的玩具庫，可以在這裡挖寶，每天都非常期待新發現。

我想，這網站並非稱得上強大或創意十足，還有很多地方可以修改、新增功能、改成更酷炫的外觀。但這也說明了Jekyll容易學習，而且具有廣泛的擴充性。

---
### 推薦網站 ###
- [Jekyll•Simple, blog-aware, static sites](https://jekyllrb.com/docs/)：官方網站，我覺得是每個使用Jekyll的人都一定要扎實地看過一遍，甚至常回來翻翻。雖然我覺得很多地方都寫得不清楚，還是得Google其他資料來輔助學習，但Jekyll每次改版時，只有這裡才是第一時間公布，其他人都幫不了你。
- [Jekyll•简单静态博客网站生成器-将纯文本转换为静态博客网站](https://jekyllcn.com/)：但如果英文看不習慣的人，這裡有好心人翻譯成簡體中文版。只是它的內容停在2016年就再也沒更新了，請自行參酌。
- [Liquid template language](https://shopify.github.io/liquid/)：所有在HTML或Markdown文件裡出現的{% raw %}{{ }}、{% %}{% endraw %}}等等，都是使用Liquid這個Gem的語法。用法簡單，而且內容不多，值得你快速掃一下。
- [Liquid for Designers](https://github.com/Shopify/liquid/wiki/Liquid-for-Designers)：跟前者差不多，只是這是用文章的形式來講解Liquid如何使用。
- [CloudCannon Academy](https://learn.cloudcannon.com/)：我幾乎快寫完這篇文章時才發現這個網站，排版看起來整齊清潔，感覺舒服。教學非常完整，從一開始架設Jekyll到進階應用都有。
- [Alligator.io](https://alligator.io/jekyll/)：我剛好在這裡看了不少介紹，覺得他寫的很清楚，雖然文章篇數不多。像是Collections功能的介紹，對於我這樣的新手來說也能理解...大概提升到六成理解。總比什麼都看不懂的好。
- [Jekyll](https://github.com/jekyll)：Jekyll官方的Github網頁，裡面有許多官方製作的Plugins，日後我會慢慢嘗試。