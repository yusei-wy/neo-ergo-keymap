# CLAUDE.md - neo-ergo-keymap

QwertyKeys Neo Ergo のキーマップを VIA で管理するリポジトリ。
コードは無く、VIA エクスポート JSON とそのドキュメントだけ。

## ファイルの役割

- `neo_ergo_wired.layout.json` — VIA からエクスポートした実体。**これが正**。
- `LAYOUT.md` — JSON を人間が読めるように視覚化したもの。**派生物**。
- `README.md` — リポジトリの使い方。
- `CLAUDE.md` — このファイル。

## 編集ルール

### JSON が変わったら LAYOUT.md を必ず追従させる

ユーザーが VIA でキーマップを変更し、`neo_ergo_wired.layout.json` を上書きしてきた場合:

1. JSON の差分を確認する（`git diff neo_ergo_wired.layout.json`）
2. `LAYOUT.md` の該当レイヤー / マクロ表を更新する
3. レイヤーが追加/削除された場合は README.md の「レイアウト」節も合わせて更新する

JSON と LAYOUT.md がずれている状態を放置しない。

### LAYOUT.md は JSON の構造を踏襲する

- レイヤー番号は JSON の `layers` 配列のインデックスに揃える（0 始まり）
- マクロ ID は `macros` 配列のインデックスに揃える（`MACRO(0)` = `macros[0]`）
- 視覚化のためにキーを並び替えたり省略したりしない

### ASCII 表は等幅前提

`LAYOUT.md` の Layer 図は monospace で見ることを前提にしている。
列幅をいじるときは全レイヤーで揃える。

## 人間工学の指針

- **保持と操作は別の手**: レイヤートリガと操作対象を同じ手に乗せない。
- **頻度でトリガを選ぶ**: 親指 LT は頻用ナビ、小指 MO は設定系。
- **併用キー群はホームロー周辺**: 遠い物理位置に頻用キーを置かない。
- **クリックは移動と別の指**: 同じ指の往復を強いない。

## VIA / QMK 用語の最低限の知識

JSON を読むときに知っておくべきこと:

| 表記 | 意味 |
|------|------|
| `KC_*` | 通常のキーコード（`KC_A`, `KC_LSFT` など） |
| `KC_TRNS` | 透過。下位レイヤーの定義にフォールスルー |
| `KC_NO` | 無効キー |
| `MT(mod, kc)` | Mod-Tap。タップで `kc`、ホールドで `mod` |
| `LT(layer, kc)` | Layer-Tap。タップで `kc`、ホールドで指定レイヤーを有効化 |
| `MO(layer)` | ホールド中のみレイヤー有効化 |
| `MACRO(n)` | `macros[n]` のキーシーケンスを再生 |

仕様の正本: <https://caniusevia.com/docs/specification>

## やってほしくないこと

- JSON を整形ツールで強制リフォーマットしない（VIA エクスポート形式を尊重）
- LAYOUT.md だけ更新して JSON を更新しない（逆も同様）
- このファイルやリポジトリ規模に対して過剰なディレクトリ構造（`docs/`, `src/` など）を勝手に作らない
