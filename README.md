# EC2 インスタンス起動用テンプレート（Cloud9 新規受付停止対応）

## はじめに

- 第 3 回までの課題で利用する EC2 インスタンスを作成する手順です。
- 本手順で起動する EC2 インスタンスは Cloud9 で起動した AmazonLinux2 のインスタンスからイメージを作成しています。
- 本手順の利用は任意です。
- 第 3 回の講座については[サポート資料](lecture03_support.md)を用意していますので、必要に応じて参照ください。

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
> アップロードするファイル： [template.yml](./template.yml)

- CloudShell を開く
- `template.yml`をアップロードする
- 以下のコマンドをコピー&ペーストして実行する

```bash
aws cloudformation deploy \
    --template-file template.yml \
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
> - セッションマネージャにはアイドルタイムアウト機能が存在するため、一定時間操作がない状態が継続すると自動的に切断されます。タイムアウトの延長は[こちら](https://docs.aws.amazon.com/ja_jp/systems-manager/latest/userguide/session-preferences-timeout.html)を確認してください。

## EC2 を Terminate（終了）してしまったら

- 誤って EC2 を Terminate（終了）してしまった場合は再度同じ手順で EC2 を起動してください。
- ただし、同名の CloudFormation スタックは存在することはできないため、スタックの削除が必要です。
- 以下にスタックの削除方法を 2 種類紹介します。

### 方法 ① CloudShell で削除コマンドを実行する

- CloudShell を開く
- 以下のコマンドを実行してスタックを削除する

```bash
aws cloudformation delete-stack \
    --stack-name sample-stack
```

- 以下のコマンドを実行し、レスポンスとして sample-stack の情報が出力されることを確認する

```bash
aws cloudformation list-stacks \
    --stack-status-filter DELETE_COMPLETE
```

### 方法 ② CloudFormation コンソールからスタックを削除する

- CloudFormation のコンソール画面を開く
- 対象のスタック（sample-stack）を選択し、削除を選択する
- スタックのステータスが`DELETE_COMPLETE`になったことを確認する
  ![スタック削除](./assets/img/delete-stack-gui.png)
