# TexLiveマニュアルインストール

## TexLive 2022

### ネットワークインストール

1. `/usr/local/texlive`を作成し、ユーザー権限に変更する
2. 別途作業用ディレクトリを作成する。
   1. ここでは`~/temp`とする

```bash
$ cd temp
$ wget https://mirror.ctan.org/systems/texlive/tlnet/install-tl-unx.tar.gz
$ tar xvzf install-tl-unx.tar.gz
# 解凍するとinstall-tl-YYYYMMDDディレクトリが作成される。
$ cd install-tl-YYYYMMDD
$ ./install-tl
Loading https://ftp.yz.yamagata-u.ac.jp/pub/CTAN/systems/texlive/tlnet/tlpkg/texlive.tlpdb
Installing TeX Live 2022 from: https://ftp.yz.yamagata-u.ac.jp/pub/CTAN/systems/texlive/tlnet (verified)
Platform: universal-darwin => 'MacOSX current (10.14-) on ARM/x86_64'
Distribution: net  (downloading)
Using URL: https://ftp.yz.yamagata-u.ac.jp/pub/CTAN/systems/texlive/tlnet
Directory for temporary files: /var/folders/y5/f66194_10gn5gvwrcrck1w_w0000gn/T/7ecYsFIEs7
======================> TeX Live installation procedure <=====================

======>   Letters/digits in <angle brackets> indicate   <=======
======>   menu items for actions or customizations      <=======
= help>   https://tug.org/texlive/doc/install-tl.html   <=======

 Detected platform: MacOSX current (10.14-) on ARM/x86_64

 <B> set binary platforms: 1 out of 16

 <S> set installation scheme: scheme-full

 <C> set installation collections:
     40 collections out of 41, disk space required: 7722 MB (free: 18958 MB)

 <D> set directories:
   TEXDIR (the main TeX directory):
     /usr/local/texlive/2022
   TEXMFLOCAL (directory for site-wide local files):
     /usr/local/texlive/texmf-local
   TEXMFSYSVAR (directory for variable and automatically generated data):
     /usr/local/texlive/2022/texmf-var
   TEXMFSYSCONFIG (directory for local config):
     /usr/local/texlive/2022/texmf-config
   TEXMFVAR (personal directory for variable and automatically generated data):
     ~/Library/texlive/2022/texmf-var
   TEXMFCONFIG (personal directory for local config):
     ~/Library/texlive/2022/texmf-config
   TEXMFHOME (directory for user-specific files):
     ~/Library/texmf

 <O> options:
   [ ] use letter size instead of A4 by default
   [X] allow execution of restricted list of programs via \write18
   [X] create all format files
   [X] install macro/font doc tree
   [X] install macro/font source tree
   [ ] create symlinks to standard directories

 <V> set up for portable installation

Actions:
 <I> start installation to hard disk
 <P> save installation profile to 'texlive.profile' and exit
 <Q> quit

Enter command:
```
ここで`I`を選択するとインストールが開始される。

かなり時間がかかりますが、終わると以下のメッセージが表示されます。


```bash
ドキュメントの一覧は /usr/local/texlive/2022/index.html をご覧ください．TeX Live のウェブサイト (https://tug.org/texlive/) にはすべてのアップデートとコレクションの情報が掲載されています．TeX Live は全世界の TeX ユーザ会有志による合同プロジェクトです．TeX Live プロジェクトをサポートしていただける場合お好きな TeX ユーザ会に入会することをご検討ください．TeX ユーザ会の一覧はhttps://tug.org/usergroups.html でご確認いただけます．


Add /usr/local/texlive/2022/texmf-dist/doc/man to MANPATH.
Add /usr/local/texlive/2022/texmf-dist/doc/info to INFOPATH.
Most importantly, add /usr/local/texlive/2022/bin/universal-darwin
to your PATH for current and future sessions.
Logfile: /usr/local/texlive/2022/install-tl.log
```

との事なのでホームディレクトリに戻ります。

```bash
$ vi .zshrc
## TexLive(2022)
export MANPATH="/usr/local/texlive/2022/texmf-dist/doc/man:$MANPATH"
export INFOPATH="/usr/local/texlive/2022/texmf-dist/doc/info:$INFOPATH"
PATH="/usr/local/texlive/2022/bin/universal-darwin:$PATH"
# :wqで終了させます。
$ source .zshrc
# 一応アップデートしてみる
$ tlmgr update --self --all
```

特に無かった。これは時々行ってパッケージのアップデートなどを取り込みましょう。

## Visual Studio Codeで使いたい！

既に[Visual Studio Code](https://azure.microsoft.com/ja-jp/products/visual-studio-code/)はインストールしてあるので、機能拡張のインストールやら設定をします。

まず**必須**とも言える[LaTeX Workshop](https://marketplace.visualstudio.com/items?itemName=James-Yu.latex-workshop)をインストールします。

明日成形してね。

   TEXDIR (the main TeX directory):
     /usr/local/texlive/2022
   TEXMFLOCAL (directory for site-wide local files):
     /usr/local/texlive/texmf-local
   TEXMFSYSVAR (directory for variable and automatically generated data):
     /usr/local/texlive/2022/texmf-var
   TEXMFSYSCONFIG (directory for local config):
     /usr/local/texlive/2022/texmf-config
   TEXMFVAR (personal directory for variable and automatically generated data):
     ~/Library/texlive/2022/texmf-var
   TEXMFCONFIG (personal directory for local config):
     ~/Library/texlive/2022/texmf-config
   TEXMFHOME (directory for user-specific files):
     ~/Library/texmf
     ドキュメントの一覧は /usr/local/texlive/2022/index.html をご覧ください．TeX Live のウェブサイト (https://tug.org/texlive/) にはすべてのアップデートとコレクションの情報が掲載されています．TeX Live は全世界の TeX ユーザ会有志による合同プロジェクトです．TeX Live プロジェクトをサポートしていただける場合お好きな TeX ユーザ会に入会することをご検討ください．TeX ユーザ会の一覧はhttps://tug.org/usergroups.html でご確認いただけます．