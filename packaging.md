# Packaging最前線

## ツールの現状

### Pypaツール

* Pypa: パッケージングツールの管理を行っている団体

* ツール
  * setuptool
  * pip
  * wheel
などなど

### setuptool

最新バージョンは18.3.2
* 1コミットでメジャーが上がる可能性がある.ので，実はあまり違いがない

### pip

+ 最新バージョンは7.1.2
+ PEPへの対応はdistlibを利用
* 7.0からはwheelをデフォルトでサポート
* get-pip.pyでwheelもインストールするようになった

### wheel

* wheel形式を扱うフォーマット
* setuptoolはこれを利用してパッケージを作成する
*
### virtualenv/venv

* 仮想環境を作る
* venvはpython3.3以降で標準ライブラリ
  * python2.xでは使えない処理を行っているので，使い分ける人はvirtualenvを使ったほうがいい

### ensurepip

* Pythonインストール時にpipを勝手にインストール
  + virtualenvは入っていないので，追加する必要がある

#### Linuxの関係

* ensure-pipでpipを更新されると困る
  * ensure-pipはpipを更新しようとするため
* なのでpyvenvではwithout-pipにしないと失敗する

### distlib

+ pipが内部で利用しているパッケージ
* Windows8以降で日本語ファイル名の処理にバグがあったv7以降で治っている

### warehous

+ 次期pypi実装
  + まだまだ時間かかりそう
* Pyramidで出来ている

## パッケージングプログラム

### パッケージメタデータの形式

+ egg-info (setuptoolが勝手に作った形式)
+ dist-info (こっちのほうが新しい)

### Metadata2.0

* JSON形式になる
* 最終的にはpydist.jsonになったが，wheelではmetadata.jsonが作られてしまう

### パッケージプログラミング

+ site, sysといった標準ライブラリを使う

### site,sys

* sitepackageの場所を確認する
  * sitepackageはサードバーティ製パッケージをインストールするためのもの
  * Linux/Macでは/usr/のしたなのでroot権限が必要
  * venvでは仮想環境なのでローカルにインストールされる
  
