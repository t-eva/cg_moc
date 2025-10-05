# FrontEnd
フロントの設計について以下を記載する。
1. [アプリケーション](#アプリケーション)
2. [アーキテクチャ](#アーキテクチャ)

## アプリケーション
フロントエンドアプリケーションのソースコードは以下に格納する。  
[front_sources](../../front_sources)

アプリケーションは React にてサンプルコードを作成する。  
作成手順は以下のとおり。

- アプリ用プロジェクト作成
    ```
    $ npx create-react-app front_sources --template typescript
    ```
- アプリ起動手順
    ```
    $ cd front_sources
    $ npm start
    ```
- ビルド手順
    ```
    $ cd front_sources
    $ npm run build
    ```

## アーキテクチャ
フロントエンドの主要なコンポーネントは以下のとおり。

1. **Internet Gateway**: インターネットとの接続点
2. **ALB**: HTTPS終端、SSL証明書管理、S3への転送
3. **VPC Endpoint**: S3への安全なアクセス経路
4. **S3 Bucket**: 静的コンテンツを配信するストレージ
5. **Route 53**: プライベートDNS解決

ユーザから FrontEnd へのアクセス経路の概要は以下のとおりとなる。
```
Internet Gateway → ALB (HTTPS) → VPC Endpoint → S3 Bucket (静的ウェブサイト)
                    ↓
                VPC内のプライベートサブネット
```
上記については以下図を参照のこと  
[frontend_architecture.dio](../img/frontend_architecture.dio)

- ネットワーク構成の詳細は「[ネットワーク設計](Network_configuration.md)」を参照すること
- S3 ストレージの詳細は「[ストレージ設計](Storage.md)」を参照すること
