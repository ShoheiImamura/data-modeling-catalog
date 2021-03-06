<style>
.box{
  float: left;
}
.boxContainer{
  overflow: hidden;
}
</style>

# 4 章データモデルの進め方

## プロセス指向からデータ指向へ

### データモデルはどのように導かれるのか

#### プロセス指向 (POA)

- アプリ構成、業務構成からデータモデルを導く方法

#### データ指向(DOA)

- 何らかの手がかりからデータモデルを導き、そこからアプリ構成、業務構成を導く方法

- ビュー群からテーブル群を導くことは本質的に困難

### 歴史的経緯

① ホスト・オフィスコンピュータ時代

- RDB は存在しない
- ファイルにデータを保管
  - 「ファイルはプログラムの従属物」
  - 図 4-3
- データ構造が複雑になると問題が発生
  - データ様式がプログラム間で矛盾する
  - システム変更に膨大な労力が必要

② 90~2000 年代（RDB の登場）

- RDB が登場
- データ様式はテーブル側に一元管理
- プログラム間のデータ定義の矛盾が一掃された
  - データ処理（並び順や結合）をプログラムの命令で端的に記述できた
  - トランザクション処理も RDB の機能で対処できた
- DB が「主」で、プロセスが「従」

②' 90~2000 年代（システムのオープン化）

- オブジェクト指向プログラミング（OOP）の台頭
  - データと処理がセット
  - 「データはプログラムの従属物」の価値観
  - RDB と OOP の相性の悪さが明らかに(インピーダンスミスマッチ)
    - OOP: 「データの扱いはオブジェクト内部で個別に対処すべき」
    - RDB: 「データ様式はテーブル側に一元管理」
  - 結局、業務システムのような複雑で膨大なデータは RDB を流用せざるを得ない

③ ORM(Object-Relational Mapping)の登場

- ORM でオブジェクト内のデータを RDB のテーブルに永続化する
- 全てのテーブルに「ID」の単独主キーとする設計
  - オブジェクト ID と対応
  - 関数従属性や更新不可制約の見落としの要因となる...

### 業務システムの仕様検討

- 業務システムの仕様検討は DB 構造を起点とすべき
  - DB 構造は、他の要素のあり方を強く規定する
  - DB 構造は、後で変更することが難しい
    - 「変えたくても変えられない」
  - 分析的 DOA フローでは本格的なシステム刷新プロジェクトでは結局失敗する
    - 図 4-7

## 分析主義的アプローチ

- 分析主義的アプローチでは解決できない
  - 「現状の問題と不満」をまとめたものでしかない
  - 「最新の建材で生まれ変わった竪穴式住居」
- 「想像的 DOA」が必要
  - 図 4-8
  - 「顧客の思い」と「設計者の経験と知識」を起点とする
  - 生み出された「あるべきデータモデル」から「あるべきアプリや業務体制」を導く
  - われわれは創造の覚悟を持たねばならない
    - 大量のアプリや業務が不要とみなされる／大幅に変更される

### プロトタイピング

- データモデルの妥当性はどのように検証するか？
  - 以前よりもシステム開発が効率化された
    - 設計者自身がシステム全体を手早く「プロトタイピング」できる
      - ユーザーに使ってもらう
      - 現行システムのデータを取り込む
  - プロトタイピングを繰り返すことで、DB 設計の品質はようやく許容できるレベルに達する
    - プログラミング主体のアジャイル開発では、検証単位が小さすぎる
- 技術者のキャリアとして、「データモデリング」を基礎とする設計スキルには大きな市場価値がある

### 現行踏襲のデメリット

- 「特定ユーザーしかできない仕事」が独占していく
  - 古参ユーザーはシステム／業務刷新に反発する
- 想像以上にコストがかかる
  - 例）古い UI を、新しい技術で踏襲する

### 業者のオーディション

- システム刷新は、「あるべきデータモデルを創造できる業者」と競業する必要がある
  - 高スキルの業者を探し出すことは困難
  - オーディションで低スキルの業者をスクリーニングすることは簡単

#### オーディションの流れ

- オーディション開催の旨を公示する
- その場でデータモデリングを行ってもらう
- その場でシステムのプロトタイプを作ってもらう
- 成果物を比較する
- 見出した技術者と契約を結ぶ
- 使用期間で、DB 構成、アプリ構成の確立を目指す
-
