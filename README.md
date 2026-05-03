# neo-ergo-keymap

[QwertyKeys Neo Ergo](https://www.qwertykeys.com/products/neo-ergo) のキーマップを [VIA](https://caniusevia.com/) で管理するためのリポジトリ。

VIA でエクスポートした `.layout.json` をそのままバージョン管理し、変更履歴と視覚的なレイアウトドキュメントを残す。

## ファイル構成

| ファイル | 役割 |
|---------|------|
| `neo_ergo_wired.layout.json` | VIA エクスポートファイル（実体） |
| `LAYOUT.md` | 各レイヤーのキー配置・マクロ定義（人間が読む用） |
| `CLAUDE.md` | Claude Code 向けプロジェクトコンテキスト |
| `README.md` | このファイル |

## 使い方

### 現在のキーマップを書き込む

1. [VIA Web App](https://usevia.app/) を開く（または VIA デスクトップ版）
2. Neo Ergo を USB 接続
3. `Settings` → `Show Design tab` を有効化（Neo Ergo の definition を読み込む必要がある場合）
4. `Configure` タブで右上の **Load saved layout**（フォルダアイコン）から `neo_ergo_wired.layout.json` を読み込む
5. 自動でキーボードに書き込まれる

### VIA で変更してリポジトリに反映する

1. VIA で配列を編集
2. **Save current layout**（保存アイコン）で JSON をエクスポート
3. リポジトリ内の `neo_ergo_wired.layout.json` を上書き
4. `LAYOUT.md` を最新の配列に合わせて更新
5. コミット

## レイアウト

詳細は [LAYOUT.md](./LAYOUT.md) を参照。

ざっくり:

- Layer 0: QWERTY ベース、ホームロー Mod-Tap（A=Alt, S=Shift, L=Shift, ;=Alt）
- Layer 1: F キー / RGB バックライト / マウス（右下 `MO(1)` ホールド）
- Layer 2: ナビゲーション（矢印・Home/End/PgUp/PgDn、左サム `SPC` ホールド）
- Layer 3: 予約（未使用）

マクロは macOS のスクリーンショット系 3 種 + 画面ロック 1 種。

## 参考リンク

- [Neo Ergo 製品ページ](https://www.qwertykeys.com/products/neo-ergo)
- [VIA Specification](https://caniusevia.com/docs/specification)
- [VIA Web App](https://usevia.app/)
- [QMK Keycodes](https://docs.qmk.fm/keycodes)
