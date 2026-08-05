# gsc
# Glider Open Atlas
## ― 滑空場の暗黙知をひらく：オープンデータとVGIによる滑空場情報基盤の設計と検証 ―

Development of "Glider Open Atlas": Structuring Tacit Knowledge of Glider Airfields through Open Data and Volunteered Geographic Information

2026年度 古橋研究室 ゼミ論（3年）構想資料
著者: Kousaku Nakagawa（青山学院大学 地球社会共生学部 / 体育会航空部）

---

## 1. Introduction（背景と課題）

グライダーの訓練・遠征では、滑空場ごとに地形、施設、進入経路、障害物、運航ルールが大きく異なる。しかしこれらの情報は部内資料・口頭伝承・紙地図に分散した「暗黙知」であり、初めてその滑空場を利用する訓練生が事前に全体像を把握することは難しい。

一方、既存の滑空場情報基盤には次の空白がある。

- Worldwide Soaring Turnpoint Exchange 等の既存データベースは旋回点座標が中心で、地上施設・アクセス・安全上の注意といった訓練生に必要な地上情報を扱わない
- OpenStreetMap には滑空場が一部登録されているものの、発航地点・ウィンチ位置・索道・注意障害物などグライダー運航特有の地物を表現するタグ運用が確立していない
- 現地画像（Mapillary 等）や高解像度オルソ画像は滑空場周辺でほぼ空白である（OpenAerialMap 上の妻沼周辺データは本研究開始時点で未整備）

### Research Question

部内に分散した滑空場の暗黙知を、オープンデータと VGI（Volunteered Geographic Information）を用いてどこまで構造化・共有できるか。また、安全に関わる VGI の信頼性はどのような運用設計で担保できるか。

## 2. Methods（研究方法）

### 2.1 情報要件の整理
航空部員・上級者への聞き取りと部内資料の分析から、訓練生が滑空場について事前に必要とする情報項目を整理する。

### 2.2 OSMタグ付けスキームの設計（研究の柱）
世界の OSM コミュニティにおける滑空場関連タグ（aeroway=* 等）の運用を調査し、日本の滑空場の実態（河川敷滑空場、ウィンチ曳航、場外離着陸場制度）に対応したタグ付けスキームを提案する。

### 2.3 妻沼滑空場のデータ整備
- 提案スキームに基づき妻沼滑空場周辺を OSM 上にマッピングする（データは OSM 本体に直接書き戻す）
- ドローン空撮を実施し、OpenDroneMap でオルソモザイクを生成、OpenAerialMap に公開して背景画像・マッピングソースとする
- Mapillary により地上画像を整備する

### 2.4 Glider Open Atlas プロトタイプ開発
Overpass API 経由で OSM データを動的に取得・表示する WebGIS を GitHub Pages 上に構築する。先行開発済みの [drone-ortho-xyz-viewer](https://github.com/KousakuNakagawa/drone-ortho-xyz-viewer)（ODM/OAM XYZ タイル用軽量ビューア）を技術基盤とする。Atlas 側に独自データを溜め込まず、地理データはすべて OSM / OAM 側に置く設計とする。

### 2.5 安全情報ガバナンスの設計
安全に関わる情報の掲載ルール（教官・上級者レビューを経た情報のみ掲載、公式規程へのリンク必須化、情報の鮮度表示）を設計し、運用する。本 Atlas は公式資料の代替ではなく事前学習の補助と位置づける。

### 2.6 評価
航空部の訓練生を対象に、Atlas 利用前後で妻沼滑空場に関する理解度テスト（場周経路・施設配置・注意障害物）を実施し、pre/post 比較により学習効果を定量評価する。あわせて使いやすさに関するアンケート・ヒアリングを行う。

## 3. Scope（今年度の研究範囲）

3年次は妻沼滑空場に対象を絞り切り、タグスキーム設計＋データ整備＋プロトタイプ＋評価を完遂する。他滑空場への展開は4年次に送る。

## 4. Expected Results（成果物）

- 滑空場情報の OSM タグ付けスキーム提案（OSM Wiki 形式のドキュメント）
- 妻沼滑空場周辺の OSM データ整備（チェンジセットとして定量的に記録）
- 妻沼滑空場のドローンオルソ画像（OpenAerialMap 公開）
- WebGIS「Glider Open Atlas」プロトタイプ（GitHub Pages）
- 安全情報ガバナンス運用ルール
- 訓練生による利用評価（理解度テスト pre/post 比較）
- IMRaD 型ゼミ論本文（本リポジトリ README / GitHub Pages）

## 5. Discussion（考察の見込み）

安全クリティカルな領域における VGI の可能性と限界を、データ設計者・現役パイロット双方の立場から論じる。「一億総伊能化」ビジョンにおける、飛行訓練・航空安全という空間情報の新しい応用領域を提示する。

## 6. 4年次卒論への発展

- 対象を全国の主要滑空場へ拡大し、各大学航空部が情報提供・更新に参加できる共同編集体制を構築
- 気象データ・空域情報・場外着陸候補地・3Dデータとの連携
- タグ付けスキームの OSM コミュニティ（talk-ja / Wiki）への正式提案
- 情報の正確性を維持する更新ルールの運用検証

## 7. スケジュール

| 時期 | マイルストーン |
|---|---|
| 夏合宿 | 構想発表（1分） |
| 〜10月 | 聞き取り・タグスキーム調査・ドローン空撮・OAM公開 |
| 11月 | 中間発表：妻沼マッピング＋プロトタイプα版 |
| 12月 | Advent Calendar で進捗レポート |
| 〜1月中旬 | 評価実施（理解度テスト・アンケート） |
| 1/31 | 研究室内最終提出（GitHub） |
| 2月第1土曜 | 最終発表会 @紗ら＋ |

## 8. License

- 本リポジトリ（論文本文・ドキュメント・コード）: © FuruhashiLabratory/Kousaku Nakagawa, CC BY 4.0（LICENSE.md 参照）
- OSM に書き戻す地理データ: ODbL（OpenStreetMap のライセンスに従う）
- OpenAerialMap 公開画像: CC BY 4.0

## 9. 進捗管理

- タスク管理: 本リポジトリの GitHub Project
- 参考文献リスト: 独立 Issue として APA ルールで管理（LLM 活用）

## 10. 参考（主要一次情報）

- OpenStreetMap Wiki: aeroway タグ群
- Worldwide Soaring Turnpoint Exchange
- OpenAerialMap / Open Imagery Network
- 公益財団法人日本学生航空連盟 妻沼訓練所
- 暦本純一 (2016)『研究法について』 / 落合陽一 #FTMA15（研究室指定文献）
