# SIerでもSphinxを使いたい！ 総括

## 2014/10/26 SphinxCon JP 2014

## @kk_Ataka

---

# 自己紹介

- Twitter: @kk_Ataka 
- GitHub:  gosyujin
- 普段いるところ
  - Kawasaki.rb
  - Jekyllrb-ja(主催)
- Python力
  - 文法もまだあやしい

![75%, right](https://pbs.twimg.com/profile_images/2222065431/image.png)

---

# 発表の趣旨

- SIerでもSphinxを使いたいので職場で奮闘してみた備忘録
  - 利用事例
  - 拡張の紹介
- Kawasaki.rbというイベントで話した内容の総集編
- できたこと、できなかったこと含めて駆け足で共有します
  - 主観が多め

---

# 今日話さないこと

- Sphinxとはなんぞや
- reST記法とはなんぞや
- Sphinxのインストール方法とか使い方とか

---

# アジェンダ

1. 競合ツールとの比較
1. 導入のためのあれこれ、または導入後の課題
3. 実際に導入してみた感想

---

# 競合ツールとの比較

---

# 競合ツールとの比較！

- 導入するためには上の人を説得するための政治が必要…
- 競合ツールと比較してよさ気と思ったことを伝えていく
  1. Office(Word, Excel)
  1. Wiki, Markdown
  1. Sphinx
- 好きな言葉「適材適所」

---

# 比較1 Office

---

# Office 長所

- SI界のスタンダード
- WYSIWYGな操作
  - きめ細かいデザインが可能
  - 図やフローの挿入が容易
- 誰のPCにも入っていて、誰でも使える

---

# !?

---

# Office 短所

- あらゆるものがOfficeで作成され、至る所にちらかる
  - 日付バージョン管理…(主観)
  - 恐怖の「 **議事録\_20140505\_2(最新)(xx修正).xls** 」
- 検索性が非常に悪い
  - 違うシートとか、吹出しとか 非表示とか…探せない…

---

# Office 短所

- diffが取るのがメンドくさい
  - 取れないとは言ってない、最近は取れるっぽい
- ミリ単位のレイアウト修正を強いられる
  - リストとかすぐ壊れる
  - 内容を集中して書かせて！
- (職人芸が発揮されるほど)重い

---

# 番外

## Officeのいいところ…カット！

---

# Officeのいいところ

- Officeでしかできないことも、ある
- 過去資料でいいところあげてます！
- ようは適材適所でよろしくお願いします

---

# 比較2 Wiki, Markdown と Sphinx

---

# Wiki, Markdown と Sphinx の長所

Officeで短所として挙げた問題は解消できている！…と思う

---

# Wiki, Markdown と Sphinx の長所

    > あらゆるものがOfficeで作成され、至る所にちらかる 問題

- プレーンテキストで作成される
- Officeよりは探しやすいんじゃないかと思うのだが…
  - ブラウザ、エディタの検索とか、Wiki内検索とか

---

# Wiki, Markdown と Sphinx の長所

    > diffが取るのがメンドくさい 問題

- Markdownはプレーンテキストなので簡単
  - バージョン管理もしやすい
- Wikiもだいたい差分表示機能あり
  - diff取りやすい

---

# Wiki, Markdown と Sphinx の長所

    > ミリ単位のレイアウト修正 問題

- 出力先(html+css、pdfなど)である程度統一できる

---

# Wiki, Markdown と Sphinx の短所

Officeでは特に意識していなかったことを考慮する必要あり

---

# Wiki, Markdown と Sphinx の短所

- 記法を覚える必要がある
  - 未経験者にちょい敷居が高い…
- 「特定部分のみ」のレイアウト修正
  - cssなどに独自の処理を入れなければならない
- 図やフローの挿入はタグで挿入
  - 直感的にいじれない(現物をD&D…)

---

# Wiki, Markdown の短所

- 検索性はあまりよくない
  - しっかり作れば…
  - それでもOffice + 共有サーバコンボよりは…
- 重い
  - 体感としては Office > Wiki, Markdown > Sphinx
  - サーバ性能とか同時アクセス数によるけど

---

# Sphinx だけの長所

- **体系的なドキュメントの骨組みを簡単に整えられる** 強力な機能がある
  - この辺をサクッとよろしくやってくれているのがdoctree...である気がする(まだ未調査)
  - Wikiとかでこれを整備するのはちょっとしんどい

---

# Sphinx だけの長所

- 検索性はよいと思う
  - 体系的にまとまるため
- 軽い
  - Outputが静的ファイル
  - htmlをWebサーバに置けば静的ファイルを取ってくるのと変わらない

---

# ここまでのまとめ

- 慣れ親しんだOfficeから脱却したい、管理しやすい形式でドキュメント作成に挑戦してみよう
  - ならば Wiki, Markdown か Sphinx だ！
- TipsとかならWiki, Markdownでもいいけど、ドキュメントなのである程度体系的に管理したい
  - 体系的に管理するのが得意な Sphinx だ！

結論: 一回Sphinxチャレンジしてみましょう！

---

# 導入のためのあれこれ、または導入後の課題

---

# 導入するための壁

1. 対プロジェクトメンバー(PM)に対して(布教)
2. 対顧客に対して(納品)

![inline](https://cloud.githubusercontent.com/assets/588166/3563656/ac52d408-0a48-11e4-9013-aac931c21e40.png)

---

# 壁1. 対PM

---

# 対PM 登場人物

- 自分
  - Sphinxを導入したい人、基本的になんでもやる
- メンバー
  - 導入したSphinxを使ってほしい人

---

# 対PM 「自分」の仕事

- **今回はreSTで進めることの明確な宣言とサポート**
  - 一番大事
  - これができないと負の成果物が生成される…

---

# 対PM 「自分」の仕事

- メンバーが「rstファイルを開いてドキュメント作成」に注力できる環境を作る
  1. sphinx-quickstartで下準備
  2. ドキュメント自体のアウトライン作成
  3. doctreeの作成

などなど

---

# 対PM 「自分」の仕事

- ビルド環境、デプロイ環境などもお膳立て
    - ビルドはJenkinsなどで拾う
    - デプロイはApacheにhtmlファイル配備とか(お手軽)

---

# 対PM 「メンバー」の仕事

- reST記法を覚えてもらう
  - Markdown -> reST -> Outputという裏技もある(Pandoc経由)
  - バージョン管理ツールとかの話は…割愛

---

# 対PM 課題

- ローカルPCでのプレビュー
  - メンバーのPCにSphinxを入れてもらうのは厳しい…
  - そうすると、確認できるのがサーバにプッシュした時のみになってしまう
  - ローカルで簡単にreSTプレビューできないだろうか…
      - GitHubとか使えばある程度できるんだけど

---

# 対PM 課題

- プロジェクト(会社)の風土にあわせたカスタマイズが必要かも
  - こういうレイアウトがいい
  - こういうヘッダフッタがほしい
  - こういう改訂履歴ページがほしい

---

# 対PM 課題
  - 今回は「変更履歴」出力プラグイン作ってみた
- sphinxcontrib-releasenotesプラグイン
  - .. releasenotes:: ディレクティブを追加したところにGitのコミットログと差分を貼り付け
  - Git使えない人用

---

![inline](https://cloud.githubusercontent.com/assets/588166/4243915/d0f9c750-3a16-11e4-96ba-375516fb44ee.png)

---

![inline](https://cloud.githubusercontent.com/assets/588166/4243916/d943b42a-3a16-11e4-8ca3-9dfd6249e3d1.png)

---

![inline](https://cloud.githubusercontent.com/assets/588166/4243918/e237b3b0-3a16-11e4-8890-1c93279fb57b.png)

---

# 壁2. 対顧客

---

# 対顧客 登場人物

- プロジェクト
  - Sphinxでドキュメント納品する側
- 顧客 (社内の人 or 社外の人)
  - ドキュメントを納品される側
  - 歴史的経緯からOfficeで納品される事が多い
      - 例外はJavadocとか？

---

# 対顧客 「プロジェクト」側の仕事

- Sphinxで作成するドキュメントに関して「今回はOfficeじゃない形式で設計書とか書きますよ」の合意を得とく

---

# 対顧客 「顧客」側の仕事

- 特になし？心構えくらい？

---

# 対顧客 課題

- **納品形式** 最重要(次ページ参照)
  - 納品後 **「誰が」** 保守するのか
  - 顧客が巻取ってしまう場合、どう保守すればよいのか
      - 要解決事項、誰かどうやってるか教えてください…
      - これが解決できないと、Sphinxは納品対象外ドキュメントにしか適用できない…

---

![inline](https://cloud.githubusercontent.com/assets/588166/3563987/1ac73444-0a65-11e4-929f-f5915950ba94.png)

---

# 実際に導入してみた感想

---

# 環境

- 3ヶ月位のほぼ1人プロジェクトで「社内資料」をSphinx！
  - 社内資料なので、納品関係の課題はスルー
  - 環境揃えたい放題
      - Git + Sphinx + Jenkins etc
  - 途中で1人サポートに入ってもらった

---

# 結果

- Gitでバージョン管理、テキストなので差分管理も簡単！
- エディタが軽いので作成が快適！
- Outputからお目当ての章が見やすい！探しやすい！
- Outputは、意外と営業の人に受けが良かった！
  - 「え？なにこれ？なんてツール？あとで教えて」

---

# 結論

- 競合ツールとの比較
  - ドキュメントを書くスピードは早いよ！
- 導入のためのあれこれ、または導入後の課題
  - 「Sphinxで書いていく！」空気を作るのが難しい
  - 個人的には、「仲間(賛同者)」がいてくれると助かる

---

# 結論

- メンバーにreSTを書いてもらうのが難しい
  - メリットの周知、慣例からの脱却までが長い
- 納品物にするにはちょっと課題が多いかも
  - 今回解決の糸口は見つからず…
