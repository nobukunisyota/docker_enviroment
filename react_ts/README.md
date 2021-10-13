# React + Typescript 開発環境

## セットアップ

1. コンテナ立ち上げ

```
docker-compose up -d --build
```

2. パッケージインストール

```
docker-compose run --rm node sh -c "npx create-react-app app --template typescript"
```

3. コンテナ起動

```
docker-compose up -d
```
