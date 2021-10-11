# Ruby on Rails + MySQL 開発環境

## セットアップ

1. コンテナ立ち上げ

```
docker-compose up -d --build
```

2. web のコンテナに入る

```
docker-compose exec web bash
```

3. rails プロジェクト作成

web のコンテナに入った状態で以下を実行

```
rails new . --force -d mysql --skip-bundle
```

4. database.yml を編集

修正箇所は以下の三箇所

```
default: &default
  adapter: mysql2
  encoding: utf8
  pool: <%= ENV.fetch("RAILS_MAX_THREADS") { 5 } %>
  username: root
  password:<%= ENV.fetch("DATABASE_PASSWORD") %> # passwordを環境変数から読み込むようにする
  host: db # hostをdbに変更
  port: 3306 # portを3306に設定
```

5. DB を作成する

web のコンテナに入った状態で以下を実行

```
rails db:create
rails db:migrate
```

6. webpacker をインストールする

web のコンテナに入った状態で以下を実行

```
rails webpacker:install
```

7. Rails 開始

web のコンテナに入った状態で以下を実行

```
rails s -b 0.0.0.0
```

## 参考サイト

- [メイン参考サイト](https://alterbo.jp/blog/ryu3-2106/)

- [M1 MAC での場合の追加対応](https://ryotarch.com/docker/no-matching-manifest-for-linux-arm64-v8-on-m1-mac/)

- [Rails6 の場合の追加対応](https://qiita.com/NaokiIshimura/items/8203f74f8dfd5f6b87a0)

- [rexml/document (LoadError)](https://qiita.com/asami___t/items/d0eb10efe95651a4a8d7)
