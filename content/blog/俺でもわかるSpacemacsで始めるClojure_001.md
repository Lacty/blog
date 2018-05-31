+++
title        = "#1 俺でもわかるSpacemacsで始めるClojure"
description  = "Spacemacsのインストールと設定、プロジェクトの作成からビルド、REPLの起動まで"

author       = "やない"
date         = "2018-05-28T22:33:39+09:00"

categories   = ["Programming"]
tags         = ["Spacemacs", "Clojure", "Leiningen"]
type         = "post"

featured     = ""
featuredalt  = ""
featuredpath = ""

+++

# 環境
俺氏は__Fedora28__で環境構築します  
パッケージ管理のコマンドは`dnf`なので環境の違う読者は適所置き換えて読んで下さい  
例えば__Ubuntu__の場合は`apt`です  

# Leiningenのインストール
<details open><summary>__Leiningen__について</summary>
Clojureのビルドツールです  
コードのコンパイルやテストの実行、REPLの起動などが可能になり  
プロジェクト開発の手助けをしてくれます。  
<span style="color:teal">[https://leiningen.org/](https://leiningen.org/)</span>
</details>

1. スクリプトのダウンロード  
```
wget https://raw.githubusercontent.com/technomancy/leiningen/stable/bin/lein
```

2. leinスクリプトを実行できるようにパスの通ったディレクトリに移動させる  
普通のLinuxであれば__~/bin__にパスが通っているので以下のコマンドを使います  
```
mv lein ~/bin
```  

3. leinスクリプトにコマンド実行権限を与える  
```
chmod a+x ~/bin/lein
```  

4. 必要なパッケージをダウンロードする  
```
lein
```  

`-v`オプションを付けるとLeiningenやJavaのバージョンを確認できます  
```
$ lein -v
Leiningen 2.8.1 on Java 1.8.0_171 OpenJDK 64-Bit Server VM
```

# Spacemacsのインストール
<details open><summary>__Spacemacs__について</summary>
EmacsとVimのいいとこ取りをしたEmacsベースのテキストエディタです  
名前の通りSpaceKeyを軸にしたコマンドが特徴で  
キーバインドが表示されるので初心者にもやさしくなっています
</details>  

1. Emacsのインストール  
```
sudo dnf install emacs
```

2. Spacemacsから.emacs.dをダウンロード  
```
git clone https://github.com/syl20bnr/spacemacs ~/.emacs.d
```

3. 必要なパッケージをインストール  
emacsの初回起動`emacs`でうまくインストールができなかった場合は  
HTTPSを無効にするオプション`--insecure`を付けて再度実行  
```
emacs --insecure
```

{{< img-fit "4u" "俺でもわかるSpacemacsで始めるClojure_001/pic01.png" "pic01.png" "date" >}}

# dotspacemacs/layersにClojureを追加
Spacemacsの設定ファイル`.spacemacs`にClojureの設定を追加すると  
`.clj`を開いた際にClojure用のコマンドが使用できるようになります

1. `SPC f e d`で.spacemacsファイルを開く  
emacsを開いてコマンドを打ちます、`SPC`は__SpaceKey__の意  
__f__ile __e__macs __d__otfile のように分かりやすくなっている

2. `dotspacemacs/layers`関数内の`dotspacemacs-configuration-layers`に`clojure`を追加  
編集モードへの移行は`i`

3. `SPC f e R`で設定をリロード  
編集モードからは`ESC`で抜けれます

{{< img-fit "4u" "俺でもわかるSpacemacsで始めるClojure_001/pic02.png" "pic02.png" "date" >}}

これでClojureをSpacemacsで書くための設定は済みました  
次はClojureのプロジェクトを作成しましょう。

# Clojureプロジェクトの作成
プロジェクトの作成には`lein`を使用します  
```
lein new project-name
```

Spacemacsから`SPC !`コマンドでshellが実行できます  
{{< img-fit "4u" "俺でもわかるSpacemacsで始めるClojure_001/pic03.png" "pic03.png" "date" >}}
