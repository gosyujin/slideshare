# ふわふわAnsible入門

## xxxx/xx/xx kawasaki.rb #xx

## @kk_Ataka

---

# 自己紹介

- Twitter: @kk_Ataka 
- GitHub:  gosyujin

![75%, right](https://pbs.twimg.com/profile_images/2222065431/image.png)

---

## アジェンダ

---

## 話さないこと

- 本格的なAnsibleの使い方
- yamlとは、yaml構文

---

## 対象者

1. 構成管理ツール何それな人
2. サーバの構成管理を手作業で行っている人
3. Ansibleを使いたいなーと思っている人

---

### 構成管理ツールとは

- サーバを調達し、必要なMW, SWなどをインストールすること
- 設定ファイルを適切に編集すること
    - これらの作業を適切に維持、管理してくれるツールの事を「構成管理ツール」という

「サーバが正しく稼動していること」の監視、確認は今回対象外

---

## サーバの構成管理の辛さ

- サーバが複数台構成になっている場合、 **基本的に**
    1. サーバ間で同一設定を維持しなければならない
        - 誰かがちょこちょこっと変更したりしてたら即死(特に開発系/テスト系サーバが自由)
    1. 設定変更が発生した場合、全てのサーバにそれを適用しなければならない
        - 一つずつログインする？ばらまくシェル作る？
- 設定ファイルってきちんと管理なされていない印象…
    - 日付管理 `xxx.conf xxx.conf.20141001 xxx.conf.20141101` が多い…
- 手順があっても、それ手作業…？
    - ミスの元
    - ダブルチェック？トリプルチェック？

---

## そこで構成管理ツール

---

## 構成管理ツールの嬉しさ

- サーバ構築手順をコード化できる(Infrastructure as Code)
- 何度実行しても同じ結果になる
- コードなのでバージョン管理がしやすい
- などなど

Chef, Puppet, Ansibleなどが挙げられる、今回はAnsibleを使ってみようという話

---

## Ansible

- あんしぶる
    - 由来はハイニッシュ・ユニバースシリーズ[^1]に登場する超光速通信技術
- Python製
- 基本理念はシンプル

[^1]: アーシュラ・K・ル・グウィン著

---

## Ansibleの長所

- べき等性(Idempotency)がある
    - 前述した、何度実行しても同じ結果になること

Ansibleのというよりは、構成管理ツール全般の長所か

例

「 `hoge.conf` の最後に "Hello World" を追加する」という処理をシェルでフツーに作ると、
そのシェルを実行するたびに "Hello World" が追加されてしまう…
(回避するためにはけっこうめんどくさい処理をシェル中に書かなければならない)

べき等性があれば、特に意識しなくても「既に変更済みなら何もしない」としてくれる。便利！

---

## Ansibleの長所

- (一応)過去の資産を活用できる
    - シェルスクリプトでInfrastructure as codeっぽいことをしていたなら、それを再利用できる
        - Ansibleからシェルスクリプトをサーバへ送り、実行できる機能がある
        - 資産を流用すると(ただのシェルスクリプトなので)べき等性はない[^1]

[^1]: `sh hoge.sh creates=/tmp/hoge.txt` とcreates指定があればそのファイルがある=スキップとしてくれる

---

## Ansibleの長所

- `python` コマンドが実行できるサーバにSSH接続できればすぐ使える
    - サーバ側に余計なツールをインストールする必要がない
    - 競合ツールでは基本的にサーバにもエージェントをインストールする必要がある
- 必要がファイルが少ない
    - とりあえずinventoryファイルとplaybookファイル(後述)
- 処理はyamlファイルで書く
    - Python製だがPythonを書ける必要はない

競合ツールと比べてきわめてシンプル、ただし一長一短あり

---

## Ansibleの短所

- 大規模システムの構成管理は苦手
- 複雑な処理も苦手

両方ともできないことはないけど、こんなときは素直にChefなどを導入したほうが良さ気
逆に小さな環境にChefを導入しようとしたらかなりToo much...(個人的な印象)

---

## Ansible 入門

---

## 登場人物

- ホスト
    - Ansible を実行するマシン
    - Python 2.6 -
        - Python 3 未対応
- サーバ
    - Ansible で環境を整えるマシン
    - Python 2.4 -

---

## 実行するために必要なファイル

- inventoryファイル
- playbookファイル
- ansible.cfgファイル

---

## inventoryファイル

- ini形式で実行対象のサーバを記述する、変数も使える

```ini
[web]
web01.example.com
web02.example.com

[web:vars]
ansible_ssh_port=20022

[db]
db01.example.com
```

---

## playbookファイル

大きく分けて3つのセクションに分けられる

- TARGETセクション
- VARSセクション
- TASKセクション
    - モジュール

---

## playbookファイル TARGETセクション

どこにだれがインストールするか

```yaml
- hosts: all           # すべてのホストに
  sudo: yes            # sudo使う
  remote_user: vagrant # vagrantユーザでログイン
```

---

## playbookファイル VARSセクション

変数を指定する。TASKセクションで使用する

```yaml
  vars:
    username: newuser
```

---

## playbookファイル TASKセクション

どんなことをするのかモジュールを使って記述する。VARSで宣言した変数も使える

```yaml
  tasks:
    - name: ユーザを追加するよ # taskの名前、必須ではない
      user: name={{ username }} group=vagrant shell=/bin/bash # モジュール
```

- userモジュールを使って以下のユーザを追加している
    - ユーザ名は newuser (VARSの変数から)
    - グループは vagrant でログインシェルは bash

---

## playbookファイル

demo.playbook

```yaml
- hosts: all
  sudo: yes
  remote_user: vagrant
  vars:
    username: newuser
  tasks:
    - name: ユーザを追加するよ
      user: name={{ username }} group=vagrant shell=/bin/bash
```

