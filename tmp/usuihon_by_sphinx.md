footer: ©2015 @kk_Ataka
slidenumbers: true

# All Sphinx環境で薄い本を作った知見

## yyyy//mm/dd

---

# 自己紹介

- Twitter: @kk_Ataka 
- GitHub:  gosyujin

![75%, right](https://pbs.twimg.com/profile_images/2222065431/image.png)

---

# アジェンダ

1. 今回のゴール
1. 環境、作成方法
1. ハマった点

Pythonコードは1行も書かずに本を作れた！

---

# 今回のゴール

---

- Sphinxを使って薄い本(epub形式)を作る！

TODOここに画像

---

# 環境

---

# 環境

1. 一人なので、Sphinxが使えるマシンを一台準備
    - Bitbucketでコード管理
1. 書いては `make html` を繰り返し
1. ある程度形になったら `make epub` で本の体裁を確認

---

# 作成方法

---

# まずは骨組み

- 目次を作成。章ごとにファイルを分割
- Sphinxだから一気通貫で見やすい

---

# 次にルール決め

- 一人だけど、書き方のルールを決めた

---

# あとは中身を書いていく

- 文章の確認は `make html` したアウトプットで

TODOここに画像

---

# 最終確認はepubで

- やはりhtmlで見るのとは見え方が違う 

TODOここに画像

---

# ハマった点

---

# 意外とあるハマりポイント

- あんな事こんな事がしたいのに…

---

# 世に出ているSphinx製の本から類推

1. Sphinxをはじめよう [^*1] [^*2]
1. 入門Ansible [^*3]

[^*1]: O'Reilly Japan 清水川貴之、小宮健、山田剛、若山史郎 著

[^*2]: 厳密にはSphinxで書いてからO'Reillyフォーマットに変換されている

[^*3]: 若山史郎 著
