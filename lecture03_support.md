# 第 3 回講座 サポート資料

## rvm のインストール

### rvm とは

RVM（Ruby Version Manager）は、複数の Ruby バージョンを 1 つのシステムで管理するツールです。  
特定の Ruby のバージョンをインストールしたり、インストールされた Ruby のバージョンの中から利用したいバージョンに切り替えることができます。

### インストール手順

参考）本手順は[こちら](https://rvm.io/rvm/install)を参考にしています。

1. ユーザの切り替えとホームディレクトリへ移動

- 実行するコマンド

```bash
$ sudo su ec2-user
$ cd ~
```

- 実行結果  
  表示なし

2. GPG キーのインストール

- 実行するコマンド

```bash
$ gpg --keyserver keyserver.ubuntu.com --recv-keys 409B6B1796C275462A1703113804BB82D39DC0E3 7D2BAF1CF37B13E2069D6956105BD0E739499BDB
```

- 実行結果サンプル

```bash
gpg: directory `/home/ec2-user/.gnupg' created
gpg: new configuration file `/home/ec2-user/.gnupg/gpg.conf' created
gpg: WARNING: options in `/home/ec2-user/.gnupg/gpg.conf' are not yet active during this run
gpg: keyring `/home/ec2-user/.gnupg/secring.gpg' created
gpg: keyring `/home/ec2-user/.gnupg/pubring.gpg' created
gpg: requesting key D39DC0E3 from hkp server keyserver.ubuntu.com
gpg: requesting key 39499BDB from hkp server keyserver.ubuntu.com
gpg: /home/ec2-user/.gnupg/trustdb.gpg: trustdb created
gpg: key D39DC0E3: public key "Michal Papis (RVM signing) <mpapis@gmail.com>" imported
gpg: key 39499BDB: public key "Piotr Kuczynski <piotr.kuczynski@gmail.com>" imported
gpg: no ultimately trusted keys found
gpg: Total number processed: 2
gpg:               imported: 2  (RSA: 2)

```

3. rvm のインストール

- 実行するコマンド

```bash
$ \curl -sSL https://get.rvm.io | bash
```

- 実行結果サンプル

```bash
Downloading https://github.com/rvm/rvm/archive/master.tar.gz
Installing RVM to /home/ec2-user/.rvm/
    Adding rvm PATH line to /home/ec2-user/.profile /home/ec2-user/.mkshrc /home/ec2-user/.bashrc /home/ec2-user/.zshrc.
    Adding rvm loading line to /home/ec2-user/.profile /home/ec2-user/.bash_profile /home/ec2-user/.zlogin.
Installation of RVM in /home/ec2-user/.rvm/ is almost complete:

  * To start using RVM you need to run `source /home/ec2-user/.rvm/scripts/rvm`
    in all your open shell windows, in rare cases you need to reopen all shell windows.
Thanks for installing RVM 🙏
Please consider donating to our open collective to help us maintain RVM.

👉  Donate: https://opencollective.com/rvm/donate

```

4. rvm の読み込み

- 実行するコマンド

```bash
$ echo "source $HOME/.rvm/scripts/rvm" >> ~/.bash_profile
$ source .bash_profile
```

- 実行結果サンプル  
  表示なし

5. インストール完了確認

- 実行するコマンド

```bash
$ rvm -v
```

- 実行結果サンプル

```bash
rvm 1.29.12-next (master) by Michal Papis, Piotr Kuczynski, Wayne E. Seguin [https://rvm.io]
```
