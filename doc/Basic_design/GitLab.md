# GitLab
GitLab の設計について以下を記載する。
1. [アプリケーション](#アプリケーション)
2. [アーキテクチャ](#アーキテクチャ)

## アプリケーション
Managed self の GitLab CE を EC2 サーバ上で稼働させる。  
moc のため、マルチAZは考慮しない。

以下の公式手順に沿ってインストールを行う。
- []()

インストール手順は以下のとおり。
```
```

## アーキテクチャ
GitLab の主要なコンポーネントは以下のとおり。

1. **Internet Gateway**: インターネットとの接続点
2. **ALB**: HTTPS終端、SSL証明書管理、S3への転送
3. **EC2**: Gitlab アプリケーションを稼働させるためのサーバ機
4. **Route 53**: プライベートDNS解決

ユーザから Gitlab へのアクセス経路の概要は以下のとおり。
```
Internet Gateway → ALB (HTTPS) → EC2（HTTP）
```
上記については以下図を参照のこと  
[gitlab_architecture.dio](../img/gitlab_architecture.dio)

- ネットワーク構成の詳細は「[ネットワーク設計](Network_configuration.md)」を参照すること。  
- EC2 の詳細は「[EC2インスタンス](ec2.md)」を参照すること。
