
# Macの環境設定

- 基本的にdebianを使うが，オフィスソフト等macを使うことがあるので，macもある程度快適に使えるように設定する

## 起動音を消す

- 以下のコマンドを複数回入力して，起動音（ジャーン）を消す
    - ``sudo nvram SystemAudioVolume=%80``
- しかし，これでもダメなことが多いので[MuteCon](http://homepage1.nifty.com/macbs/download.htm#MuteCon)を使って起動時に自動的にミュート状態にする

## キーボード

- google日本語入力を入れる
- システム環境設定の「キーボード」の「修飾キー」
    - ``Caps Lock -> ^Control``
    - ``Control -> ⌘ Command``
    - ``Option``と``Command``は変更なし
- システム環境設定の「キーボード」の「ショートカット」
    - Spotlightを切る
    - 入力ソースの切り替えを``Ctrl+Space``にする(修飾キー変換しているので表示は``Command+Space``になるが)

## その他

- finder
    - よく使う項目にHOMEとencfsを追加
    - ステータスバーを表示
    - [デフォルトをHOMEにする](http://inforati.jp/apple/mac-tips-techniques/system-hints/how-to-set-the-default-folder-of-new-macos-finder-window.html)
    - ``.DS_Store``を作らないようにする

```sh
defaults write com.apple.desktopservices DSDontWriteNetworkStores true
killall Finder
```

- Spotlightのアイコンを消す

```sh
sudo chmod 600 /System/Library/CoreServices/Search.bundle/Contents/MacOS/Search
```

- トラックパッドを逆にする
- サウンドを表示する
- dockの表示遅延をなくす

```sh
defaults write com.apple.dock autohide-time-modifier -int 0; Killall Dock
```

## ソフトウェア

- vlc
- iTerm2
    - VLゴシックをダウンロード/インストールして，フォントを変更する
- google chrome
- skype
- CotEditor
- dropbox
- [shiftlt](https://github.com/fikovnik/ShiftIt)
    - Keyの入れ替えを行っていないOptionを修飾キーとして設定する
- Adobe Acrobat Reader DC
    - 「環境設定」->「文書」->「ツールパネルの現在の状態」をオン
- gdrive
- slack

### iTerm2

- キーボードの設定 (Keysタブ)
    - Remap Modifier Keys: 日本語キーボード
        - ``Command``を``Left Ctrl``扱いにする
        - ``Left Ctrl``, ``Right Ctrl``を``Option``扱いにする
        - ``Option``は入れ替えない
    - Remap Modifier Keys: 英語キーボード
        - ``Ctrl``を``Left Command``扱いにする
        - ``Left Command``を``Ctrl``扱いにする
        - ``Right Command``も``Ctrl``扱いにする(?)
    - Key Mappings
        - ``Crtl + Space``を押して，``Do Not Remap Modifires``に設定する (ターミナル上でCtrl+spaceでIMEを切り替えられるように)
        - ``Crtl + Tab``を押して，``Do Not Remap Modifires``に設定する (ターミナル上でCtrl+Tabで他のアプリのウィンドウに切り替えられるように)
        - ``Crtl + Shift + Tab``を押して，``Do Not Remap Modifires``に設定する (ターミナル上でCtrl+Tabで他のアプリのウィンドウに切り替えられるように)
        - ``Capslock + Enter``を押して，``Ignore``に設定する（フルスクリーン切り替えを無効にする:[参考](https://qiita.com/kyamuise/items/4628cde234796fc7f687)）
        - ``Capslock + ←``を押して，``Send Escape Sequence``の``Esc + b``を設定する（ターミナル上でCapslockと矢印で単語単位でのカーソル移動を可能に）[参考](https://qiita.com/hokutoasari/items/e2442b87c7b381f9ff7c)
        - ``Capslock + →``を押して，``Send Escape Sequence``の``Esc + f``を設定する
- ``Profiles``の``keys``タブでエスケープシーケンスの変更
    - ``^↑``のは Esc+ ``[5~``に変更 (デフォルトでは``[1;5A``となっている)
    - ``^↓``には Esc+ ``[6~``  (デフォルトでは``[1;5B``となっている)
    - ``^→``には Esc+ ``[4~``  (デフォルトでは``[1;5C``となっている)
    - ``^←``には Esc+ ``[1~``  (デフォルトでは``[1;5D``となっている)
    - [(参考)](http://hints.macworld.com/article.php?story=20040401033846410)
- Memo
    - Shift + CapsLock + "+"で文字サイズの変更

### homebrew

```sh
brew doctor #設定のチェック
brew update
brew install tmux htop
brew install vim --with-lua
brew install binutils cmake coreutils ctags curl git glib nkf wget zsh tree watch colordiff python2 python3 imagemagick
brew install wdiff --with-gettext
brew install gnu-tar --with-default-names
brew install grep --default-names
brew install autopep8 flake8 jedi
brew install golang jvgrep jq ssh bash-completion zsh-completion awscli poppler parallel md5sha1sum rename lv peco
brew install gibo
brew cask install docker
brew install circleci
brew cask install mactex
```

### encfs

```sh
brew install homebrew/fuse/encfs
brew install Caskroom/cask/osxfuse

encfs ~/Dropbox/Private ~/Private
```
