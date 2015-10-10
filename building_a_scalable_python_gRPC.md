# Building a Scalable Python gRPC Service using Kubernetes

## gRPCコンセプト

+  RPCの発展系(HTTP/2で実装)
* Protocol Buefferを使用

### HTTP/2

* バイナリデータでtelnetを使用しない
* 複合処理
* ヘッダーを圧縮しオーバヘッドを削減
* サーバ側にPushメカニズムが用意されている

### Protocol Bueffer

* JSONのような構造化されたデータである．
  + パースが簡単
  * 柔軟性がある(フィールドの追加もできる)
+ バイナリデータ
* Pythonスクリプトなどを送り込むこともできる

```
  message Person {
    string name = "1";
    int32 id = 2;
    string emal = "3";
  }

  service Greeter {
    rpc GetMe() returns(Person) {}
  }
```

## gRPC and Python

* gRPC自体はCで実装されている
  * インストールには普通のMakeが必要
* Pythonベースは最近できたもので，まだα版

```
protoc -l ../../protos --python_out=. --grpc_out=. -- plugin-protoc-gen-
grpc=/path/
```

## Containers Kubernets

### 従来の方法

+ WebService-Cache-Databaseなどで構成されているが，一つのまとまったマシンで行っている場合が多かった
* ライブラリを共有化してしまい，色々と大変

### 仮想マシン

* メンテナンス性は向上したが，OSと結びつきが強いのはかわらず
* 管理が大変

### コンテナ

* 仮想マシンと従来の方の中間
* カーネルは共通でライブラリとアプリケーションだけ，別コンテナに集まっている
* プロセスとライブラリが結びついたような感じ
* Googleでは週20億のコンテナのdeployしている

## Kubernets

+ 1.0がリリースされました
+ Pods(Web server ~ content management server)の単位でクラスタの管理を行う

## Running

## Wrap Up
