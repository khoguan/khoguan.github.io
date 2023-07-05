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

1. 安裝 Homebrew，予咱方便安裝各種開發工具。以下个指令攏是佇終端機軟體當中進行。
```
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```
2. 透過 Homebrew 个 brew 指令來安裝 chruby 佮 ruby-install，目的就是欲安裝 Ruby
程式環境，因為 Jekyll 就是用 Ruby 語言寫出來，包裝做一个 gem（Ruby 軟體套件）。
```
brew install chruby ruby-install xz
ruby-install ruby 3.1.4
```
設定 shell 个執行環境：
```
echo "source $(brew --prefix)/opt/chruby/share/chruby/chruby.sh" >> ~/.bash_profile
echo "source $(brew --prefix)/opt/chruby/share/chruby/auto.sh" >> ~/.bash_profile
echo "chruby ruby-3.1.4" >> ~/.bash_profile # run 'chruby' to see actual version
```
以上是使用 bash 个儂所需要个指令，若是用 zsh 者，將 .bash_profile 改做 .zshrc 就著。

開掉 terminal，重開 terminal，檢查 ruby 版本是毋是 3.1.4
```
ruby -v
```
3. 安裝 Jekyll
```
gem install jekyll
```
以上，請參考 [Jekyll 官方文件个安裝說明](https://jekyllrb.com/docs/installation/)。

### 安裝 Chirpy 主題

Chirpy 主題个作者有另外提供一个較方便新手落手个 Chirpy Starter 予儂安裝了後，
做幾个仔簡單个設定，就會使開始進行上根本个工課：鋪文。我即个台語理想國个 repo
就是對 Chirpy Starter 充實--來个。

### Chirpy 使用佮升級的細節（猶未寫）

### Jekyll Markdown 个鋩角

1. 欲予超連結佇新頁籤/視窗來扑開
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
