# Reconfigure develop environment

## Homebrrew

とりあえず、これが無ければどーにもならんですからね。

```shell
$ /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
$ vi .zshrc
```

```conf
## Homebrew
PATH="/opt/homebrew/bin/brew:$PATH"
eval "$(/opt/homebrew/bin/brew shellenv)"
```

```shell
$ eval "$(/opt/homebrew/bin/brew shellenv)"
$ brew -v
Homebrew 3.5.10
Homebrew/homebrew-core (git revision d69507037bf; last commit 2022-08-26)
```

## ユーティリティ群

### git

まず、何をするにしても`git`が入って無いと先に進めないです。

```shell
$ brew info git
==> git: stable 2.37.2 (bottled), HEAD
# 後略

$ brew info git-flow
==> git-flow: stable 0.4.1 (bottled), HEAD
# 後略

$ brew install git
$ brew install git-flow
$ git --version
git version 2.37.2
```

### pandoc

開発には関係ありませんが、Visual Studio CodeCodeを使うし、Markdownで色々書きますので、必須です。（個人的に）

```bash
$ brew search pandoc
$ brew install pandoc
$ pandoc -version
pandoc 2.19.2
```

#### この後やった事

- mysql@5.7
- httpd
- anyenv
- nodenv
  - node
  - yarn
  - ncu
- rbenv
  - ruby
  - rails
- phpenv


#### とりあえずメモ

```conf
# Local Virtual Hosts
127.0.0.1              samples.localhost
127.0.0.1              dopefolio.localhost
127.0.0.1              openapi.local
127.0.0.1              hymns.localhost
127.0.0.1              editor.localhost
127.0.0.1              lexicon.localhost
127.0.0.1              xref.localhost
```

MySQLの文字コードをutf8mb4へ

```bash
$ mysql_secure_install
$ cp /opt/homebrew/etc/my.cnf /opt/homebrew/etc/my.cnf.org
$ vi /opt/homebrew/etc/my.cnf
```

```conf
[client]
default-character-set = utf8mb4
[mysql]
default-character-set = utf8mb4
[mysqld]
character-set-server=utf8mb4
collation-server=utf8mb4_general_ci
log_timestamps=SYSTEM
```

```shell
 gem install rails -v 7.0.3.1
  rbenv rehash
  rails -v



If you need to have bison first in your PATH, run:
  echo 'export PATH="/opt/homebrew/opt/bison/bin:$PATH"' >> ~/.zshrc

For compilers to find bison you may need to set:
  export LDFLAGS="-L/opt/homebrew/opt/bison/lib"

==> Summary
🍺  /opt/homebrew/Cellar/bison/3.8.2: 99 files, 3.7MB
==> Running `brew cleanup bison`...
Disable this behaviour by setting HOMEBREW_NO_INSTALL_CLEANUP.
Hide these hints with HOMEBREW_NO_ENV_HINTS (see `man brew`).
==> Pouring re2c--3.0.arm64_monterey.bottle.tar.gz
🍺  /opt/homebrew/Cellar/re2c/3.0: 12 files, 2.3MB
==> Running `brew cleanup re2c`...
==> Installing dependencies for libxml2: icu4c and readline
==> Installing libxml2 dependency: icu4c
==> Pouring icu4c--70.1.arm64_monterey.bottle.tar.gz
🍺  /opt/homebrew/Cellar/icu4c/70.1: 261 files, 74.9MB
==> Installing libxml2 dependency: readline
==> Pouring readline--8.1.2.arm64_monterey.bottle.tar.gz
🍺  /opt/homebrew/Cellar/readline/8.1.2: 48 files, 1.7MB
==> Installing libxml2
==> Pouring libxml2--2.10.0.arm64_monterey.bottle.tar.gz
==> Caveats
libxml2 is keg-only, which means it was not symlinked into /opt/homebrew,
because macOS already provides this software and installing another version in
parallel can cause all kinds of trouble.

If you need to have libxml2 first in your PATH, run:
  echo 'export PATH="/opt/homebrew/opt/libxml2/bin:$PATH"' >> ~/.zshrc

For compilers to find libxml2 you may need to set:
  export LDFLAGS="-L/opt/homebrew/opt/libxml2/lib"
  export CPPFLAGS="-I/opt/homebrew/opt/libxml2/include"

==> Summary
🍺  /opt/homebrew/Cellar/libxml2/2.10.0: 199 files, 6.4MB
==> Running `brew cleanup libxml2`...
==> Pouring zlib--1.2.12.arm64_monterey.bottle.tar.gz
==> Caveats
zlib is keg-only, which means it was not symlinked into /opt/homebrew,
because macOS already provides this software and installing another version in
parallel can cause all kinds of trouble.

For compilers to find zlib you may need to set:
  export LDFLAGS="-L/opt/homebrew/opt/zlib/lib"
  export CPPFLAGS="-I/opt/homebrew/opt/zlib/include"

==> Summary
🍺  /opt/homebrew/Cellar/zlib/1.2.12: 12 files, 397.6KB
==> Running `brew cleanup zlib`...
==> Installing dependencies for libzip: lz4, xz and zstd
==> Installing libzip dependency: lz4
==> Pouring lz4--1.9.4.arm64_monterey.bottle.tar.gz
🍺  /opt/homebrew/Cellar/lz4/1.9.4: 22 files, 681.4KB
==> Installing libzip dependency: xz
==> Pouring xz--5.2.6.arm64_monterey.bottle.tar.gz
🍺  /opt/homebrew/Cellar/xz/5.2.6: 95 files, 1.5MB
==> Installing libzip dependency: zstd
==> Pouring zstd--1.5.2.arm64_monterey.bottle.3.tar.gz
🍺  /opt/homebrew/Cellar/zstd/1.5.2: 31 files, 2.2MB
==> Installing libzip
==> Pouring libzip--1.9.2.arm64_monterey.bottle.tar.gz
🍺  /opt/homebrew/Cellar/libzip/1.9.2: 145 files, 851.7KB
==> Running `brew cleanup libzip`...
==> Pouring bzip2--1.0.8.arm64_monterey.bottle.1.tar.gz
==> Caveats
bzip2 is keg-only, which means it was not symlinked into /opt/homebrew,
because macOS already provides this software and installing another version in
parallel can cause all kinds of trouble.

If you need to have bzip2 first in your PATH, run:
  echo 'export PATH="/opt/homebrew/opt/bzip2/bin:$PATH"' >> ~/.zshrc

For compilers to find bzip2 you may need to set:
  export LDFLAGS="-L/opt/homebrew/opt/bzip2/lib"
  export CPPFLAGS="-I/opt/homebrew/opt/bzip2/include"

==> Summary
🍺  /opt/homebrew/Cellar/bzip2/1.0.8: 26 files, 516.2KB
==> Running `brew cleanup bzip2`...
==> Installing dependencies for curl: libunistring, libidn2, libssh2, openldap and rtmpdump
==> Installing curl dependency: libunistring
==> Pouring libunistring--1.0.arm64_monterey.bottle.tar.gz
🍺  /opt/homebrew/Cellar/libunistring/1.0: 56 files, 5.0MB
==> Installing curl dependency: libidn2
==> Pouring libidn2--2.3.3.arm64_monterey.bottle.tar.gz
🍺  /opt/homebrew/Cellar/libidn2/2.3.3: 78 files, 1MB
==> Installing curl dependency: libssh2
==> Pouring libssh2--1.10.0.arm64_monterey.bottle.tar.gz
🍺  /opt/homebrew/Cellar/libssh2/1.10.0: 184 files, 1MB
==> Installing curl dependency: openldap
==> Pouring openldap--2.6.3.arm64_monterey.bottle.tar.gz
🍺  /opt/homebrew/Cellar/openldap/2.6.3: 340 files, 7.8MB
==> Installing curl dependency: rtmpdump
==> Pouring rtmpdump--2.4+20151223_1.arm64_monterey.bottle.tar.gz
🍺  /opt/homebrew/Cellar/rtmpdump/2.4+20151223_1: 20 files, 646.4KB
==> Installing curl
==> Pouring curl--7.84.0.arm64_monterey.bottle.tar.gz
==> Caveats
curl is keg-only, which means it was not symlinked into /opt/homebrew,
because macOS already provides this software and installing another version in
parallel can cause all kinds of trouble.

If you need to have curl first in your PATH, run:
  echo 'export PATH="/opt/homebrew/opt/curl/bin:$PATH"' >> ~/.zshrc

For compilers to find curl you may need to set:
  export LDFLAGS="-L/opt/homebrew/opt/curl/lib"
  export CPPFLAGS="-I/opt/homebrew/opt/curl/include"


zsh completions have been installed to:
  /opt/homebrew/opt/curl/share/zsh/site-functions
==> Summary
🍺  /opt/homebrew/Cellar/curl/7.84.0: 502 files, 4MB
==> Running `brew cleanup curl`...
==> Pouring libiconv--1.17.arm64_monterey.bottle.tar.gz
==> Caveats
libiconv is keg-only, which means it was not symlinked into /opt/homebrew,
because macOS already provides this software and installing another version in
parallel can cause all kinds of trouble.

If you need to have libiconv first in your PATH, run:
  echo 'export PATH="/opt/homebrew/opt/libiconv/bin:$PATH"' >> ~/.zshrc

For compilers to find libiconv you may need to set:
  export LDFLAGS="-L/opt/homebrew/opt/libiconv/lib"
  export CPPFLAGS="-I/opt/homebrew/opt/libiconv/include"

==> Summary
🍺  /opt/homebrew/Cellar/libiconv/1.17: 31 files, 2.8MB
==> Running `brew cleanup libiconv`...
==> Pouring libedit--20210910-3.1.arm64_monterey.bottle.tar.gz
==> Caveats
libedit is keg-only, which means it was not symlinked into /opt/homebrew,
because macOS already provides this software and installing another version in
parallel can cause all kinds of trouble.

For compilers to find libedit you may need to set:
  export LDFLAGS="-L/opt/homebrew/opt/libedit/lib"
  export CPPFLAGS="-I/opt/homebrew/opt/libedit/include"

==> Summary
🍺  /opt/homebrew/Cellar/libedit/20210910-3.1: 53 files, 564.5KB
==> Running `brew cleanup libedit`...
==> Pouring pkg-config--0.29.2_3.arm64_monterey.bottle.tar.gz
🍺  /opt/homebrew/Cellar/pkg-config/0.29.2_3: 11 files, 676.4KB
==> Running `brew cleanup pkg-config`...
==> Pouring krb5--1.20.arm64_monterey.bottle.tar.gz
==> Caveats
krb5 is keg-only, which means it was not symlinked into /opt/homebrew,
because macOS already provides this software and installing another version in
parallel can cause all kinds of trouble.

If you need to have krb5 first in your PATH, run:
  echo 'export PATH="/opt/homebrew/opt/krb5/bin:$PATH"' >> ~/.zshrc
  echo 'export PATH="/opt/homebrew/opt/krb5/sbin:$PATH"' >> ~/.zshrc

For compilers to find krb5 you may need to set:
  export LDFLAGS="-L/opt/homebrew/opt/krb5/lib"
  export CPPFLAGS="-I/opt/homebrew/opt/krb5/include"

==> Summary
🍺  /opt/homebrew/Cellar/krb5/1.20: 162 files, 5.6MB
==> Running `brew cleanup krb5`...
==> Running `brew cleanup icu4c`...
==> Pouring oniguruma--6.9.8.arm64_monterey.bottle.tar.gz
🍺  /opt/homebrew/Cellar/oniguruma/6.9.8: 14 files, 1.4MB
==> Running `brew cleanup oniguruma`...
==> Caveats
==> bison
bison is keg-only, which means it was not symlinked into /opt/homebrew,
because macOS already provides this software and installing another version in
parallel can cause all kinds of trouble.

If you need to have bison first in your PATH, run:
  echo 'export PATH="/opt/homebrew/opt/bison/bin:$PATH"' >> ~/.zshrc

For compilers to find bison you may need to set:
  export LDFLAGS="-L/opt/homebrew/opt/bison/lib"

==> libxml2
libxml2 is keg-only, which means it was not symlinked into /opt/homebrew,
because macOS already provides this software and installing another version in
parallel can cause all kinds of trouble.

If you need to have libxml2 first in your PATH, run:
  echo 'export PATH="/opt/homebrew/opt/libxml2/bin:$PATH"' >> ~/.zshrc

For compilers to find libxml2 you may need to set:
  export LDFLAGS="-L/opt/homebrew/opt/libxml2/lib"
  export CPPFLAGS="-I/opt/homebrew/opt/libxml2/include"

==> zlib
zlib is keg-only, which means it was not symlinked into /opt/homebrew,
because macOS already provides this software and installing another version in
parallel can cause all kinds of trouble.

For compilers to find zlib you may need to set:
  export LDFLAGS="-L/opt/homebrew/opt/zlib/lib"
  export CPPFLAGS="-I/opt/homebrew/opt/zlib/include"

==> bzip2
bzip2 is keg-only, which means it was not symlinked into /opt/homebrew,
because macOS already provides this software and installing another version in
parallel can cause all kinds of trouble.

If you need to have bzip2 first in your PATH, run:
  echo 'export PATH="/opt/homebrew/opt/bzip2/bin:$PATH"' >> ~/.zshrc

For compilers to find bzip2 you may need to set:
  export LDFLAGS="-L/opt/homebrew/opt/bzip2/lib"
  export CPPFLAGS="-I/opt/homebrew/opt/bzip2/include"

==> curl
curl is keg-only, which means it was not symlinked into /opt/homebrew,
because macOS already provides this software and installing another version in
parallel can cause all kinds of trouble.

If you need to have curl first in your PATH, run:
  echo 'export PATH="/opt/homebrew/opt/curl/bin:$PATH"' >> ~/.zshrc

For compilers to find curl you may need to set:
  export LDFLAGS="-L/opt/homebrew/opt/curl/lib"
  export CPPFLAGS="-I/opt/homebrew/opt/curl/include"


zsh completions have been installed to:
  /opt/homebrew/opt/curl/share/zsh/site-functions
==> libiconv
libiconv is keg-only, which means it was not symlinked into /opt/homebrew,
because macOS already provides this software and installing another version in
parallel can cause all kinds of trouble.

If you need to have libiconv first in your PATH, run:
  echo 'export PATH="/opt/homebrew/opt/libiconv/bin:$PATH"' >> ~/.zshrc

For compilers to find libiconv you may need to set:
  export LDFLAGS="-L/opt/homebrew/opt/libiconv/lib"
  export CPPFLAGS="-I/opt/homebrew/opt/libiconv/include"

==> libedit
libedit is keg-only, which means it was not symlinked into /opt/homebrew,
because macOS already provides this software and installing another version in
parallel can cause all kinds of trouble.

For compilers to find libedit you may need to set:
  export LDFLAGS="-L/opt/homebrew/opt/libedit/lib"
  export CPPFLAGS="-I/opt/homebrew/opt/libedit/include"

==> krb5
krb5 is keg-only, which means it was not symlinked into /opt/homebrew,
because macOS already provides this software and installing another version in
parallel can cause all kinds of trouble.

If you need to have krb5 first in your PATH, run:
  echo 'export PATH="/opt/homebrew/opt/krb5/bin:$PATH"' >> ~/.zshrc
  echo 'export PATH="/opt/homebrew/opt/krb5/sbin:$PATH"' >> ~/.zshrc

For compilers to find krb5 you may need to set:
  export LDFLAGS="-L/opt/homebrew/opt/krb5/lib"
  export CPPFLAGS="-I/opt/homebrew/opt/krb5/include"
```