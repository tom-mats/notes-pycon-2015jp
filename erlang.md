# What Pyhton can learn from Erlang?

## Erlangとは

* ほぼ関数型言語
* Concurrent&reliable program
* OTPフレームワークというのが用意されている

### オブジェクト指向との比較

+ OOPで行いたいことはLISPやsmalltalkでできていたよね アラン ケイ

## reliableとは

* エラーに対抗するための手段
* リカバリーを簡単にするための手段
* Hot-Upgrade(アップグレードも簡単，リスタートが不要である)

### EralngにおけるReliableの実現

* プロセスが独立しており，他のプロセスに影響を与えない
  * message passing ベースのプログラム実装
  * シェアードメモリを使用しない
* パターンマッチ

### プロセスが独立しており，他のプロセスに影響を与えない

* プロセスは独立しているので，一つのプロセスが落ちてもシステム全体としては処理を継続できる
* 復旧も落ちたプロセスだけ復旧去ればいいので簡単である

### 同じことをPyhtonでもできないか

* __結構難しい__

* GIL(グローバルインタプリタロック)
  * すべてのプロセスを1スレッドで動かしている
* OSプロセスを使用する(multiprocessing, gunicorn)

* 方法?
  * PuPrallel
  * PyPy STM

## システムとしてみた場合うまくいかないかな

### Supervisor
### Load-Balancer & Proxy
### Containers

### Immutability

* 実世界はmutableである
* ただし区間を区切った場合, Immutabieとみなすこともできる

### Imuutableの意味

* 一つの入力に対して毎回同じ出力を返す

#### 利点

* テストも簡単
* プロセス間の共有も簡単(毎回同じ振る舞いをするから)
* スレッドセーフであり，ロック処理も不要

### PythonでImuutableな処理をするための手段

* Funktown
* Pysistence
* fn.py
などなど
(名前だけ見ると関数型言語の処理を追加するためのパッケージに思える)

## catch文を多用せずにクラッシュさせよう

* Erlangベース(プロセスが完全に独立している)ならば，復旧も簡単
* Crashさせる
* ログした後に再起動させる
