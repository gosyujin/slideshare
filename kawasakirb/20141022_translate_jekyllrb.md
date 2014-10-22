# Jekyllドキュメント翻訳活動振り返り

## 2014/10/22 kawasaki.rb #17

## @kk_Ataka

---

# 自己紹介

- Twitter: @kk_Ataka 
- GitHub:  gosyujin

![75%, right](https://pbs.twimg.com/profile_images/2222065431/image.png)

---

# アジェンダ

1. Jekyllとは
1. 翻訳に至る流れ
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

- 決まった記法で記事を書き、buildするとhtmlに変換してくれる
- Ruby製
- Markdownとかで書く
- GitHub Pagesでも使われてる

![100%, right](https://cloud.githubusercontent.com/assets/588166/4730750/cf55fb24-599e-11e4-8384-c194a1755489.png)

---

# 翻訳に至る流れ

---

# 翻訳に至る流れ 起

- 自分「Jekyllのしくみを知るために公式ドキュメント読むか」
- 自分「せっかくだから翻訳しながら読んでみよう」
- 自分「PRもしてみよう」

---

# 翻訳に至る流れ 承

- 自分「はじめにREADME.mdとか翻訳してみたよ」
- 中の人「ありがとう」

---

# 翻訳に至る流れ 転

- 自分「次に、ドキュメントも翻訳していきたいんだけどルールとかある？」
- 中の人「他の言語読めないから管理できないし、ウチでは扱わないよ」

---

# 翻訳に至る流れ 結

- 中の人「ポルトガル語翻訳のリポジトリを作ってる人がいるから参考にしなよ」
- 自分「わかった」
= http://github.com/jekyllrb-ja 作った

---

![inline](https://cloud.githubusercontent.com/assets/588166/4730751/d4008df6-599e-11e4-87bb-f7d033566f7c.png)

---

# Jekyllrb-jaの翻訳フロー

---

# Jekyllrb-jaの翻訳フロー

1. 本家で更新があったドキュメントに対して「翻訳して追いつくぞ！」Issueを作る
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
  - 本家ドキュメントと日本語ドキュメント、どうやって更新されたか検知する？

---

# gh-diffを使う

---

# gh-diff

- https://github.com/melborne/gh-diff
- @merborneさん謹製のファイル差分確認、出力ツール[^*]
- ローカルリポジトリとGitHub上のリモートリポジトリのMarkdownファイルの差分を取ってくれる
  - ただし、翻訳ドキュメントは一定のルールに則って作成されている必要がある

[^*]: http://melborne.github.io/2014/07/04/you-always-compared-with-github/

---

# こんな感じ

- jekyll/jekyll の index.md(本家=リモート=主)

```html
  <h1>HELLO WORLD!!</h1>
```

- gosyujin/jekyllrb-ja の index.md(翻訳=ローカル=従)

```html
  <h1>こんにちは世界。</h1>
  <!--original
  ## Hello World.
  -->
```

---

# こんな感じ

```
$ gh-diff diff index.md --repo=jekyll/jekyll --no-name_only

Base revision: xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx[refs/heads/master]
--- index.md
+++ index.md

- <h1>Hello World.</h1>
+ <h1>HELLO WORLD!!</h1>
```

- リモートリポジトリとローカルリポジトリ(のコメントアウト部分)のdiffを取って表示してくれる

---

# こんな感じ

- diff結果をファイル出力する事もできる
- このdiffファイルの内容を消化する事で本家の更新についていく
  - Issue化して **「1ドキュメント 1Issue」** とルールが決められれば、管理が楽になりそう
  - IssueにするところはRakeで自動化！

![100%, right](https://cloud.githubusercontent.com/assets/588166/4730875/b808d9e8-59a1-11e4-8d06-4274171d268e.png)

---

# 継続的翻訳活動のために まとめ

1. 本家で更新があったドキュメントに対して「翻訳して追いつくぞ！」Issueを作る
  - これが大変
2. 更新部分を翻訳してPR
3. PR内容を議論
4. OKならマージ
5. 1. に戻る…

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

- 進捗

![inline](https://cloud.githubusercontent.com/assets/588166/4730945/f32c3e1a-59a2-11e4-92b7-5ce3797585dd.png)

---

# [fit]翻訳してみたい人待ってます！
