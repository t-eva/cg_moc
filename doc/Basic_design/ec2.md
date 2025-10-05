# EC2インスタンス
EC2 の設計概要は以下のとおり。

- GitLab にてサポートされているため、AMI は AWS との親和性の高い `Amazon Linux` を採用する
- GitLab 公式アナウンスに従い、`t3.medium` 以上のマシンタイプを選択する
- Private サブネット内に構築し、ALB 経由 でWEB アクセスを行う
- EC2 への SSH アクセスは SSMセッションマネージャー経由で行う
- データは EBS に格納する
    - EBS の詳細は「[ストレージ設計](Storage.md)」を参照すること
