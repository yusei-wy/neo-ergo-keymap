# Neo Ergo Keymap Layout

`neo_ergo_wired.layout.json` の内容を視覚化したドキュメント。
JSON を更新したらこのファイルも合わせて更新する。

## 物理レイアウト概要

Neo Ergo は Alice 系スプリットレイアウトで、以下の構成を持つ。

- 左右分割された 6+6 のメインキー列（Y/B 列の中間に追加サムキー `\``）
- 右端に追加マクロ列（行ごとに 1 キー、合計 4 キー）
- 右下にインバーテッド T 型の矢印クラスタ
- 分割スペースバー（左 = SPC、右 = ENT）
- 左サムに複数のモディファイア、右サム側に RGUI

JSON 配列のキー数は各レイヤー 75。

## 凡例

| 表記 | 意味 |
|------|------|
| `A⌥` | Mod-Tap: タップで A、ホールドで Left Alt |
| `S⇧` | Mod-Tap: タップで S、ホールドで Left Shift |
| `L⇧` | Mod-Tap: タップで L、ホールドで Shift（L+R） |
| `;⌥` | Mod-Tap: タップで `;`、ホールドで Alt（L+R） |
| `SPC/L2` | Layer-Tap: タップで Space、ホールドで Layer 2 |
| `MO(n)` | Layer-Mod: ホールド中だけ Layer n を有効化 |
| `M0`〜`M3` | マクロスロット（後述） |
| `▽` | Transparent（下位レイヤーを透過） |
| `─` | KC_NO（無効キー） |

各レイアウト図は等幅フォント前提。左右のブロックは物理的な分割を表す。

## Layer 0 — Base (QWERTY)

ホームロー Mod-Tap と Layer-Tap で薄型カスタム化。

```
 ESC    1     2     3     4     5     6                 7     8     9     0     -     =    RCTL    M1

 TAB    Q     W     E     R     T                       Y     U     I     O     P     [     ]     \     M0

 LCTL   A⌥    S⇧    D     F     G                       H     J     K    L⇧    ;⌥     '    BSPC   LALT  M2

 LSFT   Z     X     C     V     B          `            N     M     ,     .     /     ↑    MO(1)        M3

         LALT  RALT  LGUI  NUBS      SPC/L2    ENT     RGUI                          ←     ↓     →
```

ポイント

- ホームロー Mod-Tap: `A=Alt`, `S=Shift`, `L=Shift`, `;=Alt`（タップで通常文字、ホールドでモディファイア）
- 親指 `SPC` はホールドで Layer 2（ナビ）
- 右下 `MO(1)` ホールドで Layer 1（ファンクション/RGB/マウス）
- 中央右の `\`` は Alice 系の中央サムキー
- 右端列 `M0`〜`M3` は macOS スクリーンショット系マクロ（後述）

## Layer 1 — Function / RGB / Mouse （`MO(1)` ホールドで起動）

```
 `      F1    F2    F3    F4    F5    F6                F7    F8    F9    F10   F11   F12    ▽     ▽

 ▽      ▽     ▽     ▽     ▽     ▽                       ▽     ▽     ▽     ▽    WhDn    ▽     ▽     ▽     ▽

 ▽      ▽     ▽     ▽     ▽    NKRO                     ▽     ▽     ▽    WhL   WhU    WhR    ▽     ▽     ▽

 ▽     RGBT  RGBM  RGB-  Hue+  Hue-       Sat+          Sat-  Val+  Val-   ▽     ▽    MsUp   ▽            ▽

         ▽     ▽     ▽     ▽         ▽          ▽         ▽                          MsL   MsDn  MsRt
```

ポイント

- 数字行: `\`` + F1〜F12（`Esc → \``、数字 → ファンクション）
- `P` 位置: マウスホイール下
- `G` 位置: NKRO（N-Key Rollover）切替
- `L`/`;`/`'` 位置: マウスホイール左/上/右
- `Z`〜`,` の連続: RGB バックライト制御（ON/OFF, モード前送り/後戻し, 色相, 彩度, 明度）
- `↑` 位置: マウスカーソル上
- 矢印クラスタ `←/↓/→`: マウスカーソル左/下/右

RGB キーコード対応:

| 表記 | キーコード | 効果 |
|------|------------|------|
| `RGBT` | `RGB_TOG` | バックライト ON/OFF |
| `RGBM` | `RGB_MOD` | エフェクトモード次へ |
| `RGB-` | `RGB_RMOD` | エフェクトモード前へ |
| `Hue+` / `Hue-` | `RGB_HUI` / `RGB_HUD` | 色相 増減 |
| `Sat+` / `Sat-` | `RGB_SAI` / `RGB_SAD` | 彩度 増減 |
| `Val+` / `Val-` | `RGB_VAI` / `RGB_VAD` | 明度 増減 |

## Layer 2 — Navigation （`SPC` ホールドで起動）

```
 ▽      ▽     ▽     ▽     ▽     ▽     ▽                 ▽     ▽     ▽     ▽     ▽     ▽     ▽     ▽

 ▽      ▽     ▽     ▽     ▽     ▽                      Home  PgUp   ↑    End    ▽     ▽     ▽     ▽     ▽

 ▽      ▽     ▽     ▽     ▽     ▽                       ▽     ←     ↓     →     ▽     ▽     ▽     ▽     ▽

 ▽      ▽     ▽     ▽     ▽     ▽          ▽           PgDn   ▽     ▽     ▽     ▽     ▽     ▽            ▽

         ▽     ▽     ▽     ▽         ▽          ▽         ▽                          ▽     ▽     ▽
```

ポイント

- 右手上段（Y/U/I/O）: Home / PgUp / ↑ / End
- 右手中段（J/K/L）: ← / ↓ / →
- 右手下段（N）: PgDn
- それ以外は Layer 0 を透過

## Layer 3 — Reserved

全キー Transparent（未使用予約レイヤー）。

```
すべて ▽
```

## マクロ定義

`MACRO(n)` は QMK のマクロスロットで、JSON `macros` 配列の n 番目に対応する。

| ID | 配列内の表記 | 動作 | 用途 |
|----|--------------|------|------|
| `MACRO(0)` (M0) | `{KC_LGUI,KC_LSFT,KC_4}` | ⌘ + ⇧ + 4 | macOS 範囲スクリーンショット |
| `MACRO(1)` (M1) | `{KC_LSFT,KC_LGUI,KC_LCTL,KC_4}` | ⌘ + ⇧ + ⌃ + 4 | macOS スクリーンショット（クリップボード） |
| `MACRO(2)` (M2) | `{KC_LGUI,KC_LSFT,KC_5}` | ⌘ + ⇧ + 5 | macOS スクリーンショットツール起動 |
| `MACRO(3)` (M3) | `{KC_LGUI,KC_LCTL,KC_Q}` | ⌘ + ⌃ + Q | macOS 画面ロック |

スロット 4〜15 は未割り当て（空文字列）。

## キーコード参考

VIA / QMK のキーコード仕様は <https://caniusevia.com/docs/specification> および <https://docs.qmk.fm/keycodes> を参照。

主要なものだけ抜粋:

| キーコード | 意味 |
|------------|------|
| `KC_TRNS` | このレイヤーでは透過（下のレイヤーを使う） |
| `KC_NO` | 無効キー（押しても何もしない） |
| `MT(mod, kc)` | Mod-Tap（タップ=kc, ホールド=mod） |
| `LT(layer, kc)` | Layer-Tap（タップ=kc, ホールド=layer 有効化） |
| `MO(layer)` | ホールド中のみ layer を有効化 |
| `MAGIC_TOGGLE_NKRO` | NKRO（N-Key Rollover）切替 |
| `RGB_TOG` 他 | RGB バックライト制御 |

## JSON 配列インデックスとキー対応表

`layers[*]` 配列のインデックスと Layer 0 の物理キー対応。新しいレイヤーを編集するときの索引用。

| idx | Layer 0 キー | 行 |
|-----|--------------|-----|
| 0–6 | ESC, 1, 2, 3, 4, 5, 6 | row 0 (左) |
| 7 | `KC_NO` (中央ギャップ) | row 0 |
| 8–13 | 7, 8, 9, 0, -, = | row 0 (右) |
| 14–15 | RCTL, M1 | row 0 (右端列) |
| 16–21 | TAB, Q, W, E, R, T | row 1 (左) |
| 22–26 | Y, U, I, O, P | row 1 (右) |
| 27–29 | [, ], \\ | row 1 (右端) |
| 30 | M0 | row 1 (右端列) |
| 31–36 | LCTL, A, S, D, F, G | row 2 (左) |
| 37–42 | H, J, K, L, ;, ' | row 2 (右) |
| 43–44 | BSPC, LALT | row 2 (右端) |
| 45 | M2 | row 2 (右端列) |
| 46–51 | LSFT, Z, X, C, V, B | row 3 (左) |
| 52 | \` | row 3 (中央サム) |
| 53–57 | N, M, ,, ., / | row 3 (右) |
| 58–59 | ↑, MO(1) | row 3 (右端) |
| 60 | M3 | row 3 (右端列) |
| 61–64 | LALT, RALT, LGUI, NUBS | row 4 (左サム) |
| 65 | `KC_NO` | row 4 |
| 66–67 | SPC/L2, ENT | row 4 (中央サム) |
| 68–69 | `KC_NO` × 2 | row 4 |
| 70 | RGUI | row 4 (右サム) |
| 71 | `KC_NO` | row 4 |
| 72–74 | ←, ↓, → | row 4 (矢印クラスタ) |
