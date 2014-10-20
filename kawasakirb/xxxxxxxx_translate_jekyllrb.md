# Jekyllドキュメント翻訳活動振り返り

## 2014/10/xx kawasaki.rb #1x

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
1. Jekyllの翻訳フロー
1. 継続的翻訳活動のために

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

# Jekyllの翻訳フロー

---

# Jekyllの翻訳フロー

1. 本家で更新があったドキュメントに対して「翻訳して追いつくぞ！」Issueを作る
2. 更新部分を翻訳してPR
3. PR内容を議論
4. OKならマージ
5. 1. に戻る…

---

# 継続的翻訳活動のために

---

# 継続的翻訳活動のために

- 大変なのは「本家ドキュメントの更新にどうやってついていくか」
  - めんどくさい手順は減らしたい
- 本家で更新があったドキュメントに対してIssueを作る
  - これが一番めんどくさい
  - 本家ドキュメントと日本語ドキュメント、どうやって更新されたか検知する？

---

# gh-diffを使う

---

# gh-diff

- https://github.com/melborne/gh-diff
- @merborneさん謹製のファイル差分確認、出力ツール
  - http://melborne.github.io/2014/07/04/you-always-compared-with-github/
- ローカルリポジトリとリモートリポジトリのMarkdownファイルの差分を取ってくれる

---

# こんな感じ

```
jekyll/jekyll index.md(本家=主)

HELLO WORLD!!
```

```
gosyujin/jekyllrb-ja index.md(翻訳=従)

こんにちは世界。
<!--original
Hello World.
-->
```

---

# こんな感じ

```
$ gh-diff diff index.md --repo=jekyll/jekyll --no-name_only

Base revision: xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx[refs/heads/master]
--- index.md
+++ index.md

- Hello World.
+ HELLO WORLD!!
```

- diff結果をファイル出力する事もできる
  - https://github.com/jekyllrb-ja/jekyllrb-ja.github.io/blob/master/diff/_docs/variables.diff
- これをIssue化して「1ドキュメント 1Issue」とルールが決められれば、管理が楽になりそう
  - IssueにするところはRakeで

---

# 継続的翻訳活動のために

1. 本家で更新があったドキュメントに対して「翻訳して追いつくぞ！」Issueを作る
  - 常に本家との差分を確認する(gh-diff)
  - 差分があればIssue化する(rake)
  - 変更を1ドキュメント 1Issueで管理する
2. 更新部分を翻訳してPR
  - 1. でIssue化したものをターゲットとする
3. PR内容を議論
4. OKならマージ
  - 1. で選んだIssueをClose
5. 1. に戻る…
