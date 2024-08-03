# EC2 インスタンス起動用テンプレート（Cloud9 新規受付停止対応）

## 概要

- Cloud9 のコンソールで起動した AL2 のインスタンスから
- AWS CloudFormation と`template.yaml`を利用します。
- Cloud9 同様、Ruby や Git などがプリインストールされているため、環境構築

## 利用方法

1. CloudShell を開く
2. アクションから、ファイルのアップロードをクリックし、`template.yaml`をアップロードする
3. 以下のコマンドを CloudShell に貼り付け、Enter をタイプする

```bash
aws cloudformation deploy \
    --template-file template.yaml \
    --stack-name sample-stack \
    --capabilities CAPABILITY_NAMED_IAM
```

![create_ec2](./assets/gif/create_ec2.gif)
