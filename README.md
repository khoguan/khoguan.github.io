# 【潘科元台語文理想國】部落閣新站建置說明書

本站使用靜態網站產生器(Static Site Generator, SSG) Jekyll，配搭 Chirpy 主題框殼
來製作。

## 舊網站鋪文个處理法

我个舊站是佇中華電信「隨意窩」blog.xuite.net/khoguan，因為 xuite.net 欲收擔矣，
我姑不將著徙岫。利用 xuite.net 提供个下載功能，將所謂 MT 格式个文字檔掠落來。
我佇隨意窩有開三本日誌，按呢就有三份MT檔，每一檔就是一本日誌開基以來全部个鋪文。
圖檔、影音檔閣愛另外掠。這無電腦技術个儂欲哪有才調搬徙過去別个部落閣中心咧？

我有寡電腦自學基礎，猶著愛用濟濟時間、心神去研究、試驗。

### 自寫程式處理MT檔

我寫寡 Raku(原名 Perl 6）程式來分割、處理MT檔，一鋪文一檔案，頭前加上新網站所用个
SSG 所要求个 front matter，佮原底个MT檔格式有出入，著愛轉換過。

### 先徙一寡仔去 blogspot.com，無理想。

blogspot.com 部落閣中心是 Google 開个，咱个網域若共 Google Domains 申請，
按呢欲踮 Google Domains 遐進一步設定，將網域指向 blogspot.com
提供予部落客个網址，可比講我申請个網域是 taigi.page，欲共伊指向 khoguan.blogspot.com
實在有夠輕可。但是 blogspot 本身縛跤縛手，已經無適合我即種有千幾篇鋪文
欲遷徙入去个部落閣大戶矣！

## 簡單个架站說明佮重要指令

### 改用 Github Pages + Jekyll SSG + Chirpy theme

後來決定欲用 Github 提供个免費空間 Github Pages 來囥我个部落閣鋪文，
用 Jekyll + Chirpy theme 來管理、製作網站。

### 安裝 Jekyll
#### 基本環境

我是用 Mac 系統，用 Linux 也差不多做法。若用 Windows 系統彼就差較遠，我無討論。
以下个terminal指令攏是針對 Mac 來寫个：

1. 安裝 Homebrew，予咱方便安裝各種開發工具。以下个指令攏是佇終端機軟體當中進行。每一條指令頭前个 `$` 號是指終端機个提示號(prompt)，毋是實際指令个一部份。

```console
$ /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

2. 透過 Homebrew 个 brew 指令來安裝 chruby 佮 ruby-install，目的就是欲安裝 Ruby
程式環境，因為 Jekyll 就是用 Ruby 語言寫出來，包裝做一个 gem（Ruby 軟體套件）。
```console
$ brew install chruby ruby-install xz
$ ruby-install ruby 3.1.4
```

設定 shell 个執行環境：

```console
$ echo "source $(brew --prefix)/opt/chruby/share/chruby/chruby.sh" >> ~/.bash_profile
$ echo "source $(brew --prefix)/opt/chruby/share/chruby/auto.sh" >> ~/.bash_profile
$ echo "chruby ruby-3.1.4" >> ~/.bash_profile # run 'chruby' to see actual version
```

以上是使用 `bash` 个儂所需要个指令，若是用 `zsh` 者，將 `.bash_profile` 改做 `.zshrc` 就著。

開掉 terminal，重開 terminal，檢查 ruby 版本是毋是 3.1.4

```console
$ ruby -v
```

3. 安裝 Jekyll
```console
$ gem install jekyll
```
以上，請參考 [Jekyll 官方文件个安裝說明](https://jekyllrb.com/docs/installation/)。

## 安裝 Chirpy 主題

Chirpy 主題个作者有另外提供一个較方便新手落手个 Chirpy Starter 予儂安裝了後，
做幾个仔簡單个設定，就會使開始進行上根本个工課：鋪文。我即个台語理想國个 repo
就是對 Chirpy Starter 充實--來个。

### 用 Chirpy Starter 做 template 佇 Github 建立 repo

登入 GitHub，揣著 [**Chirpy Starter**](https://github.com/cotes2020/chirpy-starter)，點迄个鈕仔 <kbd>Use this template</kbd> > 
<kbd>Create a new repository</kbd>，共新建新个 repo 號名做 `username.github.io`，
注意迄个 `username` 著愛用咱佇 GitHub 真正的 username。像我是用 `khoguan`
做 username。

## 佇 local 電腦建置網站程式佮內容

將頂段新建立个 repo 也佇家己 local 个電腦 clone 一份，親像我是佇我个 Mac
个 `terminal` 程式內底扑：

```console
$ gh repo clone khoguan/khoguan.github.io
```

就會佇當下个目錄內生出一份佮 GitHub 遐仝款个 `khoguan.github.io` 目錄，
以下就叫做「工作目錄」。

了後，佇 clone 好勢个工作目錄下底，執行：

```console
$ bundle
```

指令，伊就會按照目錄中迄个 `Gemfile` 个內容來安裝 Chirpy theme 佮伊需要个相關套件。
欲查 Chirpy theme 安裝去佗位，就扑：

```console
$ bundle info --path jekyll-theme-chirpy
```

### 照咱个需要，修改網路个參數

佇工作目錄內底，第一步愛改个就是規个網站个設定檔 `_config.yml`。
`Chirpy Starter` 予咱个設定檔見本內底，有詳細說明每一項目个用途。
主要愛改个項目有：

- `url`
- `avatar`
- `timezone`
- `lang`

`jekyll-theme-chirpy` 个目錄所囥个，是某一版本个 Chirpy theme
較固定个內容，`Chirpy Starter` 个目錄（也就是工作目錄）所囥个，
相對來講，就是會使予咱修改个項目，咱嘛會使將 `jekyll-theme-chirpy`
遐个一寡檔案，可比講 `_data/locales/zh-TW.yml` 複製過來工作目錄仝款个所在，
修改做台語文个 locale，予網站標題、顯示訊息攏用台文顯示）。

### 鋪文！

工作目錄个 `_posts` 下底就是予咱建立咱个鋪文个所在。一鋪文一檔案，
我个文章濟，所以有進一步照年代建立子目錄，像 `_posts/2006/`、
`_posts/2007/` 等等。

鋪文檔案通使用 Markdown 抑是 HTML 文字檔，Markdown 內底也接受直接用
HTML tags，真利便。無論用佗一種格式，文檔內底个頭前攏愛有 front matter，
前後用 `---` 隔開，內中記錄即篇鋪文个 metadata。可比講：

```markdown
---
layout: post
title: 搜揣教會公報資料庫个撇步 
date: 2023-07-16
author: 潘科元
categories: [文獻, 台語白話字文獻]
tags: [教會公報]
---
## 教會公報紹介
內文第一段，紹介教會公報个來歷。

## 教會公報相關个網站
有官方網站，佮別个單位所做个查詢系統。

## 教會公報全文檢索網紹介
設佇中研院。
```

檔名个格式就親像 `2023-07-16-搜揣教會公報資料庫个撇步.md`。

### 試運轉

拄開始，著愛先佇本地端个電腦試看網站建置會起來袂，才通上傳去 GitHub。
照頭前所寫，修改 `_config.yml`，也建立幾篇仔鋪文了後，就會使試運轉看覓。

```console
$ bundle exec jekyll s
```
伊執行个訊息若出現親像按呢个文字：
```
     Generating...
                   done in 94.329 seconds.
```
就表示初步成功矣。會使開瀏覽器連去 `http://127.0.0.1:4000/`
看咱千辛萬苦才生出來个網站囉！
（訊息其中个 94.329 是秒數，各站个文件數量無仝，各儂个電腦規格也無仝，
欲生出網頁个秒數自然就無仝。）

閣來就是透過 `git` 指令來 `add`、`commit`、`push` 等等，佇工作目錄遐：

```console
$ git add _console.yml
$ git commit -m '設定_console.yml'
$ git add _posts/
$ git commit -m '建立鋪文'
$ git push
```

按呢就上傳去 GitHub 咱个網站 repo 內，會使進一步佇遐設定，
來公開發佈咱个網站矣！

詳細請參考 [Chirpy 示範網站](https://chirpy.cotes.page/)个文件。 

## Jekyll 佮 Chirpy 使用个鋩角

1. 逐遍執行 `jekyll` 指令，頭前攏愛扑 `bundle exec` 才袂用著毋著个版本，
真費氣。會使得將版本符合个相關指令，裝入來工作目錄个 `bin/` 下底：

```
$ bundle install --binstubs
...
$ ls ./bin
bundle		jekyll		listen		racc		safe_yaml
htmlproofer	kramdown	nokogiri	rougify		sass
```

2. `htmlproofer` 真有路用，`Gemfile` 內指定愛用 "~> 3.18"，才會檢查
html 格式有正確無。`htmlproofer` v.4 以後个版本講因為 HTML5 browser 較寬容，
所以就無閣做即種檢查矣。GitHub 遐負責自動部署網站个 Action flow 當中，
測試階段有一步就是執行 `htmlproofer`。咱佇本地端用頭前所講个指令試運轉無問題，
但是往往會佇 GitHub 遐予 `htmlproofer` 掠包、袂過關。所以三不五時著佇本地端執行
`htmlproofer` 檢查一下：

```
$ bin/jekyll build  # build 會使簡單扑 b
$ bin/htmlproofer _site --disable-external --check-html --allow_hash_href
```

3. Markdown 格式，欲予超連結佇新頁籤/視窗來扑開
例：`[Google](https://google.com){:target="_blank"}`

## 原始文件

以下是 Jekyll Chirpy Starter 个原始說明文件：

---

# Chirpy Starter [![Gem Version](https://img.shields.io/gem/v/jekyll-theme-chirpy)](https://rubygems.org/gems/jekyll-theme-chirpy) [![GitHub license](https://img.shields.io/github/license/cotes2020/chirpy-starter.svg?color=blue)][mit]

When installing the [**Chirpy**][chirpy] theme through [RubyGems.org][gem], Jekyll can only read files in the folders `/_data`, `/_layouts`, `/_includes`, `/_sass` and `/assets`, as well as a small part of options of the `/_config.yml` file from the theme's gem. If you have ever installed this theme gem, you can use the command `bundle info --path jekyll-theme-chirpy` to locate these files.

The Jekyll team claims that this is to leave the ball in the user’s court, but this also results in users not being able to enjoy the out-of-the-box experience when using feature-rich themes.

To fully use all the features of **Chirpy**, you need to copy the other critical files from the theme's gem to your Jekyll site. The following is a list of targets:

```shell
.
├── _config.yml
├── _plugins
├── _tabs
└── index.html
```

To save you time, and also in case you lose some files while copying, we extract those files/configurations of the latest version of the **Chirpy** theme and the [CD][CD] workflow to here, so that you can start writing in minutes.

## Prerequisites

Follow the instructions in the [Jekyll Docs](https://jekyllrb.com/docs/installation/) to complete the installation of the basic environment. [Git](https://git-scm.com/) also needs to be installed.

## Installation

Sign in to GitHub and [**use this template**][use-template] to generate a brand new repository and name it `USERNAME.github.io`, where `USERNAME` represents your GitHub username.

Then clone it to your local machine and run:

```
$ bundle
```

## Usage

Please see the [theme's docs](https://github.com/cotes2020/jekyll-theme-chirpy#documentation).

## License

This work is published under [MIT][mit] License.

[gem]: https://rubygems.org/gems/jekyll-theme-chirpy
[chirpy]: https://github.com/cotes2020/jekyll-theme-chirpy/
[use-template]: https://github.com/cotes2020/chirpy-starter/generate
[CD]: https://en.wikipedia.org/wiki/Continuous_deployment
[mit]: https://github.com/cotes2020/chirpy-starter/blob/master/LICENSE
