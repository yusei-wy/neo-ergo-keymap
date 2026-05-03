# Neo Ergo Keymap Layout

`neo_ergo_wired.layout.json` の内容を視覚化したドキュメント。
JSON を更新したらこのファイルも合わせて更新する。

## 物理レイアウト概要

Neo Ergo は Alice 系スプリットレイアウトで、以下の構成を持つ。

- 左右分割された 6+6 のメインキー列
- 右端に追加マクロ列（縦 4 キー）
- 右下にインバーテッド T 型の矢印クラスタ
- スペースバーは分割（SPC + ENT）
- 左サムに複数のモディファイア、右サム側に RGUI

JSON 配列のキー数は各レイヤー 75。

## 凡例

| 表記 | 意味 |
|------|------|
| `A⌥` | Mod-Tap: タップで A、ホールドで Left Alt |
| `S⇧` | Mod-Tap: タップで S、ホールドで Left Shift |
| `L⇧` | Mod-Tap: タップで L、ホールドで Shift（L+R） |
| `;⌥` | Mod-Tap: タップで `;`、ホールドで Alt（L+R） |
| `SPC/L1` | Layer-Tap: タップで Space、ホールドで Layer 1 |
| `MO(n)` | Layer-Mod: ホールド中だけ Layer n を有効化 |
| `M0`〜`M3` | マクロスロット（後述） |
| `▽` | Transparent（下位レイヤーを透過） |
| `─` | KC_NO（無効キー） |

## Layer 0 — Base (QWERTY)

ホームロー Mod-Tap と Layer-Tap で薄型カスタム化。

```
 ESC    1     2     3     4     5     6                 7     8     9     0     -     =    RCTL    M1

 TAB    Q     W     E     R     T                       Y     U     I     O     P     [     ]     \     M0

 LCTL   A⌥    S⇧    D     F     G                       H     J     K    L⇧    ;⌥     '    BSPC   LALT  M2

 LSFT   Z     X     C     V     B          `            N     M     ,     .     /     ↑    MO(2)        M3

         LALT  RALT  LGUI  NUBS      SPC/L1    ENT     RGUI                          ←     ↓     →
```

ポイント

- ホームロー: `A=Alt`, `S=Shift`, `L=Shift`, `;=Alt`（タップで通常文字、ホールドでモディファイア）
- 親指 `SPC` はホールドで Layer 1（カーソル + マウス、頻用）
- 右下 `MO(2)` ホールドで Layer 2（ファンクション / RGB、設定系）
- 中央右の `\`` は Alice 系の追加サムキー

## Layer 1 — Cursor / Mouse （`SPC` ホールドで起動）

`▽` は Layer 0 を透過。

```
 ▽      ▽     ▽     ▽     ▽     ▽     ▽                 ▽     ▽     ▽     ▽     ▽     ▽     ▽     ▽

 ▽      ▽    WhU   MsU   WhD    ▽                      Home  PgUp   ↑    End    ▽     ▽     ▽     ▽     ▽

 ▽    ACL0   MsL   MsDn  MsR  ACL2                      ←     ↓     →     ▽     ▽     ▽     ▽     ▽     ▽

 ▽      ▽    BTN3  BTN2  BTN1   ▽          ▽            ▽     ▽     ▽    PgDn   ▽     ▽     ─           ▽

         ▽     ▽     ▽     ▽         ▽         BTN1     ▽                          ▽     ▽     ▽
```

ポイント

- マウスカーソルは左手 ESDF（`E`=上, `S`=左, `D`=下, `F`=右）。ホームポジションのまま操作
- クリックは ESDF の真下列（`V`=BTN1, `C`=BTN2, `X`=BTN3）。指の縦移動だけで打てる
- 右親指 `ENT` 跡地にも BTN1 を重複配置（両手分担 / 片手完結を選べる）
- 右手カーソルは旧 Layer 2 と同じ（`Y`/`U`/`I`/`O` = Home/PgUp/↑/End, `H`/`J`/`K` = ←/↓/→, `.` = PgDn）
- ホイール: `W`=上, `R`=下
- 加速: `A`=ACL0（精密）, `G`=ACL2（高速）
- 物理矢印クラスタは透過 → Layer 0 の物理矢印が機能
- 旧 `MO(1)` 跡地（位置 59）は誤発火防止のため `─`（KC_NO）

## Layer 2 — Function / RGB （`MO(2)` ホールドで起動）

`▽` は Layer 0 を透過。

```
 `      F1    F2    F3    F4    F5    F6                F7    F8    F9    F10   F11   F12    ▽     ▽

 ▽      ▽     ▽     ▽     ▽     ▽                       ▽     ▽     ▽     ▽     ▽     ▽     ▽     ▽     ▽

 ▽      ▽     ▽     ▽     ▽    NKRO                     ▽     ▽     ▽     ▽     ▽     ▽     ▽     ▽     ▽

 ▽    RGBT  RGBM  RGBM' RGBH+ RGBH-      RGBS+         RGBS- RGBV+ RGBV-  ▽     ▽     ▽     ▽           ▽

         ▽     ▽     ▽     ▽         ▽          ▽       ▽                          ▽     ▽     ▽
```

ポイント

- 数字行: F1〜F12
- 右小指の `MO(2)` ホールドで起動。設定系を集約
- NKRO トグルは `G` に
- RGB バックライト一式（ON/OFF, モード, 色相, 彩度, 明度）は下段 `Z`〜`,` に展開（中央 `` ` `` を含む）

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
| `KC_MS_UP` 他 | マウスカーソル移動（UP/DOWN/LEFT/RIGHT） |
| `KC_MS_BTN1` 他 | クリック（BTN1=左, BTN2=右, BTN3=中） |
| `KC_MS_WH_UP` 他 | ホイール（UP/DOWN/LEFT/RIGHT） |
| `KC_MS_ACCEL0` 他 | カーソル加速モード（0=精密, 2=高速） |
| `MAGIC_TOGGLE_NKRO` | NKRO（N-Key Rollover）切替 |
| `RGB_TOG` 他 | RGB バックライト制御 |
