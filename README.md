# EC2 インスタンス起動用テンプレート（Cloud9 新規受付停止対応）

## はじめに

- 第 3 回までの課題で利用する EC2 インスタンスを作成する手順です。
- 本手順で起動する EC2 インスタンスは Cloud9 で起動した AmazonLinux2 のインスタンスからイメージを作成しています。
- 本手順の利用は任意です。

> [!NOTE]
> 本手順で EC2 インスタンスを起動するために利用する AWS サービス
>
> - CloudShell
> - CloudFormation  
>   ※これらのサービスについて、現段階で理解する必要はありません。（CloudShell はカリキュラム内では扱いませんが、CloudFormation は第 10 回で学習します。）

## 利用方法

### ① 作成する

> [!IMPORTANT]
> 本手順はすべて、東京リージョンで実行すること。

> [!NOTE]
> 以下に記載されているファイルを事前にダウンロードしておいてください。  
> アップロードするファイル： [template.yaml](./template.yaml)

- CloudShell を開く
- `template.yaml`をアップロードする
- 以下のコマンドをコピー&ペーストして実行する

```bash
aws cloudformation deploy \
    --template-file template.yaml \
    --stack-name sample-stack \
    --capabilities CAPABILITY_NAMED_IAM
```

![create_ec2](./assets/gif/create_ec2_demo.gif)

> [!NOTE]
> 作成が完了するまで数分かかります。

### ② 正常に作成されたことを確認する

- CloudShell に`Successfully`と表示されることを確認する
- CloudFormation のコンソールを開く
- sample-stack のステータスが`CREATE_COMPLETE`であることを確認する
  ![create_ec2](./assets/gif/check_stack_demo.gif)

### ③ EC2 に接続する

- EC2 のコンソールを開く
- `dev-rasetech-ec2`を選択し、`接続`からセッションマネージャで接続する
- `sudo su ec2-user`でユーザを切り替える
- `cd ~`でホームディレクトリに移動する
- `ruby -v`で ruby が利用できる状態であることを確認する
- `git- v`で git が利用できる状態であることを確認する
  ![create_ec2](./assets/gif/connect_ec2_demo.gif)

> [!TIP]
>
> - シェルの操作は補助教材`CLIの基礎`を活用ください。
> - `cd`コマンドや`ls`コマンドの意味が分からない方は必ず`CLIの基礎`で事前学習するようにしてください。
> - EC2 インスタンスは停止しておくことで料金の発生（無料枠の消費）を抑えることができます。

### VSCode で接続する

後日更新予定（SSH プラグイン利用方法）
