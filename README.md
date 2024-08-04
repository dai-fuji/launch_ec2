# EC2 インスタンス起動用テンプレート（Cloud9 新規受付停止対応）

## はじめに

- Cloud9 の新規受付停止に伴い、第 3 回までの課題で利用を想定した
-
- 本手順を利用せずに
  > [!NOTE]
  > 本手順で EC2 インスタンスを起動するために利用する AWS サービス
  >
  > - CloudShell
  > - CloudFormation

## 利用方法

### ① 作成する

> [!NOTE]
> 以下に記載されているファイルを事前にダウンロードしておいてください。

- アップロードするファイル [template.yaml](./template.yaml)
- 利用するコマンド

```bash
aws cloudformation deploy \
    --template-file template.yaml \
    --stack-name sample-stack \
    --capabilities CAPABILITY_NAMED_IAM
```

![create_ec2](./assets/gif/create_ec2_demo.gif)

### ② 作成されたことを確認する

![create_ec2](./assets/gif/check_stack_demo.gif)

### ③EC2 に接続する

> [!NOTE]
> AWS Systems Manager のセッションマネージャと呼ばれる機能を利用して接続しています。

![create_ec2](./assets/gif/connect_ec2_demo.gif)

> [!TIP]
> EC2 インスタンスは停止しておくことで料金の発生（無料枠の消費）を抑えることができます。

### VSCode から接続する

後日更新予定（SSH プラグイン利用方法）

## 補足事項

- Cloud9 で作成した AL2 のインスタンスのイメージを使用しています。
