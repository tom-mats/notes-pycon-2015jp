# 基調講演 10／10 beyond grep

ox.cx/b に情報が上がっている
@hynek
vrmd.de

## ERRORS

* タイムリーな形で通知されたい
* エラー情報に使える情報が欲しい

### Sentry

* オープンソフト
* Python ~ Django
* 有償のオプションもある
* エラー情報を

* JSON-HTTPで登録(RAVEN)

## Metrics

+ DB上のデータを修正

System metrics -- load network traffic i/o
App metrics - counters, timer(画面表示，DBのアクセス速度),gauage(アクティブユーザー数などカウントしたいもの)

グラフを見れば，トレンド(相関付け)がわかる
一番遅い場合のリクエスト速度(分散など)

## Monitoring

システムの振る舞いが変わったら，何らかの異常が発生する

### Librato Metrics

https経由でデータを投げる

### Graphite

* オンプレミス
* ストレージの構成が

### GRAFANA

### influx DB

+ Goで書かれている

### Prometheus

* metrics + Monitoring
* PULLベース
* Alertを考慮した上で設計されている
  + 何かが起こったら通知してくれる
* GUI PromDash
  + GRAFANAを正式サポート

## Approaches

+ External aggregation SatsD, Riemann
  + Rimanは設定が若干難しい
  * 状態がないので単純
  * 中を簡単にはみれない
* Aggreaget in-app deliver to DB
 * 使い易い
 * 状態をもってしまうのでバグの温床になってしまう

### Scales

+ MeterStat:毎秒あたり
* PmfStat+タイマー
* JSON形式もサポート

## logging

### splunk

+ Enterprieseソフトウェア

### Papertrail

### loggly

### ELK <- これは便利そう

Elasticsearch(検索エンジン) ~ logstash(LOGGINGソフト) + Kibana(UIF)

### Graylog

* ELKハビューだけだど，様々な機能がある

## structlog

ログの際のデータとフォーマットを生成する，JSON形式で出力


## コードをきれい二する
