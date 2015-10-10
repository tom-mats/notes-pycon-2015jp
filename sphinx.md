# Sphinxで作る貢献しやすいドキュメント翻訳の仕組み

## ツール

* Sphinx
* Sphinx-intl i18nの補助ツール
* transifex-client Transfiexのクライアント
* Drone.io CI

## 歴史

+ -2007 : Pythonのドキュメントは LaTeXだった
* 2007- : Sphinxに以降
+ 最近Read the Docsが登場し，好きなバージョンをいつでも観れるようになった

## 下準備

transifex-client 0.8を使用

* conf.py
```
language = `ja`
locale = [`locale`]
```

## 貢献しやすいドキュメント翻訳とは

* 元のソースコードを変えずに行うのが重要

### 翻訳しにくい状況

+ ドキュメントがHTMLだけ
  * HTMLを書き換える？
* マニュアルがreSTファイルやソースコードないのdocstringが生成されている  
  * reSTファイルを書き換える
  * ソース内のdocstringを書き換える

###  sphinx-i18nの機能

+ potファイルの生成
  * reSTから生成(make get text)
* poファイルの読み込み
  * potファイルを翻訳して日本語も含めたもの
  * po + reSTファイル -> HTML  

### 流れ

1. potファイルの生成
1. 翻訳者がpotファイルを翻訳して，poファイルを作る
1. もらったpoファイルを組み合わせて翻訳後のhtmlを生成する

## Sphinx i18n

### potファイルを生成
```
$ make gettext
```

### poファイルを作る

/doc/to/path/locale/ja/LC_MESSAGES/に*.poとして保存する
sphinx-intlを実行すれば自動で行ってくれる
```
$ sphinx-intl update -p _build/gettext -l ja
```

### 翻訳する

### もう一回 make html

## 自動化と便利なサービス

* gettextを作るためにclone処理が必要
* アップロードが必要

__自動化が必要__

__翻訳は並列化したい__

### Transfiex(翻訳の並列化)

* potを翻訳
* 便利そう

### 自動化

* バッチファイルで簡単にできる
* 鍵などは環境変数で定義してあげる

### Drone.io を使って自動化

* Jenkinsでもできそうである．
* gettextして，poファイルをTransfiexにアップロードする
  * 翻訳者はTransifexで翻訳すれば良い．
* Drone.ioはpoファイルが変更されればその段階でも実行されるので，htmlが更新される．
  * gitbucketにアップロードして，gitbucket上でpoファイルを編集?

### 備考

* Markdownもサポートできるけど，PlaneなMarkdownしか今の所できない 
