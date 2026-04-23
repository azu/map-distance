# map-distance

不動産情報の駅徒歩テキストから、各駅の徒歩圏を円で可視化するツール。複数駅の条件が重なるエリアを地図上で確認できる。

Demo: <https://azu.github.io/map-distance/>

## 使い方

1. デモサイトを開く
2. 物件情報のテキストを貼り付けて「表示」
   - 例: `京成本線「新三河島」駅 徒歩4分／山手線・京浜東北線・千代田線「西日暮里」駅 徒歩14分`
3. 各駅を中心とした徒歩圏の円が地図に描画される。円が重なる部分が両方の条件を満たすエリア
4. マーカーをクリックすると、その座標を Google Maps で開くリンクが表示される

### URLパラメータ

クエリを URL で共有できる。

- `q`: 物件テキスト
- `speed`: 徒歩速度 (m/分, 省略時 80)

例: <https://azu.github.io/map-distance/?q=%E4%BA%AC%E6%88%90%E6%9C%AC%E7%B7%9A%E3%80%8C%E6%96%B0%E4%B8%89%E6%B2%B3%E5%B3%B6%E3%80%8D%E9%A7%85%20%E5%BE%92%E6%AD%A94%E5%88%86>

## 仕様

- 徒歩速度は「不動産の表示に関する公正競争規約」に従い **80m/分** をデフォルトとする (端数切り上げ)
- パース対象: `「駅名」` と `徒歩N分` を `／` `/` で区切った各区間から抽出
- 複数路線の表記 (`山手線・京浜東北線・千代田線`) は駅名の前に付いていればポップアップに表示

## 技術スタック

- Pure JavaScript (ビルド不要、単一HTMLファイル)
- 地図: [Leaflet](https://leafletjs.com/) + [OpenStreetMap](https://www.openstreetmap.org/)
- ジオコーディング: [Photon](https://photon.komoot.io/) (OSMベース, APIキー不要)
- デプロイ: GitHub Pages (`.github/workflows/deploy.yml` が main プッシュで自動デプロイ)

## 開発

リポジトリをクローンし、`index.html` をブラウザで開くだけで動作する。

## ライセンス

MIT
