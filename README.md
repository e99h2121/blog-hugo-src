# blog-hugo

OS: Microsoft Windows 10 Home

## Install

githubからzipをダウンロード。
githubのHugoでhttps://github.com/spf13/hugo/releasesよりwindowsの64bitバージョンを選び、
`C:\hugo_0.83.1_Windows-64bit` に置いた。

Hugoのbinフォルダを作りexeを配置。
`C:\hugo_0.83.1_Windows-64bit\bin\hugo.exe`

環境変数パスを通す。以下コマンドで良い。

```
set path=%path%;C:\hugo_0.83.1_Windows-64bit\bin;
```

`hugo help` などが使えることを確認。

Hugoの初期フォルダを作る。ここでは `blog-hugo`。
作ったフォルダに移動する。

`cd C:\git\blog-hugo`
`hugo new site <サイト名>` でサイトが作れる。

```
hugo new site InitialSites
```


```cmd
C:\git\blog-hugo>hugo new site InitialSites
Congratulations! Your new Hugo site is created in C:\git\blog-hugo\InitialSites.

Just a few more steps and you're ready to go:

1. Download a theme into the same-named folder.
   Choose a theme from https://themes.gohugo.io/ or
   create your own with the "hugo new theme <THEMENAME>" command.
2. Perhaps you want to add some content. You can add single files
   with "hugo new <SECTIONNAME>\<FILENAME>.<FORMAT>".
3. Start the built-in live server via "hugo server".

Visit https://gohugo.io/ for quickstart guide and full documentation.
```

### Theme

テーマをインストール。今回は以下にした。

https://themes.gohugo.io/github-style/


```
cd InitialSites
mkdir themes
cd themes

git clone https://github.com/MeiK2333/github-style
```


```
C:\git\blog-hugo\InitialSites>hugo new readme.md
C:\git\blog-hugo\InitialSites\content\readme.md created
```

### 起動

`cd ..` InitialSitesに戻り、以下で起動してみる。


```
hugo server -t github-style -D -w
```

https://localhost:1313/


### config.toml の設定

```config.toml

baseURL = "https://e99h2121.github.io/blog-hugo/"
publishDir = "docs"
languageCode = "ja-ja"
title = "e99h2121's New Hugo Site"
theme = "github-style"
googleAnalytics = "UA-119695202-4"
pygmentsCodeFences = true
pygmentsUseClasses = true

[params]
  author = "yamada_n"
  description = "Where there is a null, there is no way."
  github = "e99h2121"
  twitter = "e99h2121"
  instagram = "e99h2121"
  tumblr = "e99h2121"
  url = "https://e99h2121.github.io/"
  keywords = "blog, google analytics"
  rss = true
  lastmod = true
  location = "Japan"

  [[params.links]]
    title = "Link"
    href = "https://e99h2121.github.io/"

[frontmatter]
  lastmod = ["lastmod", ":fileModTime", ":default"]

```

サイトプレビュー停止には中断コマンドの `Ctrl+C` でよい。

https://yonehub.y10e.com/2019/10/22/20191022_hugo_githubio/


## 記事を書く

`hugo -t github-style` で公開ファイルを生成。

`cd C:\git\blog-hugo-src\InitialSites`

例: 
`hugo new post/newpost202106091417.md`


```
C:\git\blog-hugo-src\InitialSites>hugo new post/newpost202106091417.md
C:\git\blog-hugo-src\InitialSites\content\post\newpost202106091417.md created
```

`hugo server -t github-style -D -w`

で動作確認。

`hugo -t github-style`

で生成。


```config.toml
publishDir = "docs"
```
上のとおり、config.toml に設定しているので、docs 以下を GitHubPages化しているリポジトリにコピーすることでまずは手動公開できる。


階層: 
https://github.com/<ユーザー名>/<リポジトリ名>/tree/main/docs
(例: https://github.com/e99h2121/blog-hugo/tree/main/docs)

GitHub Pages:
https://github.com/<ユーザー名>/<リポジトリ名>/settings/pages


