# Jekyllドキュメント翻訳活動振り返り

## 2014/11/29 TokyuRuby会議08

## @kk_Ataka

---

# 自己紹介

- Twitter: @kk_Ataka 
- 勢いでJekyllrbの翻訳はじめました

![75%, right](https://pbs.twimg.com/profile_images/2222065431/image.png)

---

# アジェンダ

1. Jekyllとは
1. Jekyllrb-jaの翻訳フロー
1. 継続的翻訳活動のために

![150%, right](https://cloud.githubusercontent.com/assets/588166/4730736/87f9c094-599e-11e4-92f0-4081003c6425.png)

---

# 今日話さないこと

1. ドキュメント翻訳の是非について
1. 英語力とかの話

---

# Jekyllとは

---

# Jekyllとは

Transform your plain text into static websites and blogs.

- Ruby製
- Markdownとかで書く
- GitHub Pagesでも使われてる
- 以下略

![100%, right](https://cloud.githubusercontent.com/assets/588166/4730750/cf55fb24-599e-11e4-8384-c194a1755489.png)

---

## (紆余曲折あり)翻訳してます

![inline](https://cloud.githubusercontent.com/assets/588166/4730751/d4008df6-599e-11e4-87bb-f7d033566f7c.png)

---

# [fit]翻訳してみたい人待ってます！

---

# Jekyllrb-jaの翻訳フロー

---

# Jekyllrb-jaの翻訳フロー

1. 本家で更新があったドキュメントに対して「翻訳して追いつくぞ！」Issueを作る
  - ＼めんどい／
2. 更新部分を翻訳してPR
3. PR内容を議論
4. OKならマージ
5. 1. に戻る…

---

# 継続的翻訳活動のために

---

# 継続的翻訳活動のために

- 「本家ドキュメントの更新にどうやってついていくか」
  - めんどくさい手順は減らしたい
- 本家で更新があったドキュメントに対してIssueを作って残ドキュメントを管理したい
  - これが一番めんどくさい
  - どうやって更新されたかを検知する？

---

# gh-diffを使う

---

# gh-diff

- https://github.com/melborne/gh-diff
- @merborneさん謹製のファイル差分確認、出力ツール[^1]
- ローカルとGitHub上のリモートのMarkdownファイルの差分を取ってくれる[^2]

[^1]: http://melborne.github.io/2014/07/04/you-always-compared-with-github/

[^2]: ただし、翻訳ドキュメントは一定のルールに則って作成されている必要がある

---

# 翻訳はこんな感じ

- jekyll/jekyll の index.md(本家=リモート=主)

```html
  ## Hello
```

- gosyujin/jekyllrb-ja の index.md(翻訳=ローカル=従)

```html
  ## こんにちは
  <!--original
  ## Hello
  -->
```

---

# 差分出力はこんな感じ

```
$ gh-diff diff index.md --repo=jekyll/jekyll --no-name_only

Base revision: xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx[refs/heads/master]
--- index.md
+++ index.md

- ## Hello
+ ## Good bye !!
```

- リモートリポジトリが進んでる場合、こんな感じでdiffが出る！

---

# こんな感じ

- diff結果をファイル出力する事もできる
- このdiffファイルの内容を消化する事で本家の更新についていく
  - Issue化して **「1ドキュメント 1Issue」** とルールが決められれば、管理が楽になりそう
  - IssueにするところはRakeで自動化！

![100%, right](https://cloud.githubusercontent.com/assets/588166/4730875/b808d9e8-59a1-11e4-8d06-4274171d268e.png)

---

# 「翻訳して追いつくぞ！」

- 常に本家との差分を確認する (gh-diffを使う)
- 差分があればIssue化する(rakeで自動化)
- 変更を1ドキュメント 1Issueで管理する

---

- gh-diffで変更を見つけたファイルをIssue化(Rakeで)

![inline](https://cloud.githubusercontent.com/assets/588166/4730939/e6f5d8ea-59a2-11e4-8a68-0e94f00a18b7.png)

---

- Issueの内容

![inline](https://cloud.githubusercontent.com/assets/588166/4730940/eb440bb0-59a2-11e4-97c8-589d76ce584c.png)

---

- 変更点をまとめたファイル

![inline](https://cloud.githubusercontent.com/assets/588166/4730942/eefc3c50-59a2-11e4-9b3c-1c46a3c17283.png)

---

- マイルストーンごとに進捗

![inline](https://cloud.githubusercontent.com/assets/588166/4730945/f32c3e1a-59a2-11e4-92b7-5ce3797585dd.png)
