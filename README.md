# zmk-config-roBa

<img src="keymap-drawer/roBa.svg" >

## キーマップ

凡例: `↦` = 長押しでレイヤー切替 / `trans` 表記の無いキーは透過（下のレイヤーが有効）。

### レイヤー一覧

| # | レイヤー | 進入方法 | 用途 |
|---|----------|----------|------|
| 0 | MAC | デフォルト | macOS 用ベース |
| 1 | WIN | `BT` レイヤーで切替 | Windows 用ベース |
| 2 | NUM | `SPACE` 長押し | 数字・記号 |
| 3 | ARROW | `TAB` 長押し | 矢印・Home/End・タブ操作 |
| 4 | MOUSE | トラックボール操作で自動（5秒） | マウスクリック |
| 5 | SCROLL | `-` 長押し | トラックボールでスクロール |
| 6 | BT | 両親指コンボ（最外＋左Shift位置） | Bluetooth・Mac/Win 切替 |
| 7 | FUNC | `ENTER` 長押し | ファンクションキー |
| 8 | AERO | `BACKSPACE` 長押し | AeroSpace 操作（Option 不要） |

### Layer 0: MAC

```
Q     W     E     R     T                         Y     U     I     O     P
A     S     D     F     G    ;      '             H     J     K     L     -↦
Z     X     C     V     B    TAB↦   ENTER↦        N     M     ,     .     /
         LCTL  LALT  LCTL  LSFT  SPC↦  LCMD    RCMD  BSPC↦              SS
```

- `TAB↦` = tap:Tab / hold:ARROW、`ENTER↦` = tap:Enter / hold:FUNC
- `SPC↦` = tap:Space / hold:NUM、`-↦` = tap:`-` / hold:SCROLL
- `BSPC↦` = tap:BackSpace / hold:AERO
- `SS` = tap:`Cmd+Shift+4`（範囲スクショ）/ hold:`Cmd+Shift+5`（スクショメニュー）

### Layer 1: WIN

```
Q     W     E     R     T                         Y     U     I     O     P
A     S     D     F     G   Cmd+Sft+S  '          H     J     K     L     -↦
Z(⇧)  X     C     V     B   :          ;          N     M     ,     .     /
        LGUI  LALT  LCTL  無変換↦  SPC↦  ARROW↦   BSPC  ENTER↦             DEL
```

- `無変換↦` = tap:無変換(IME英数) / hold:LCTRL
- `Z(⇧)` = tap:Z / hold:Shift、`Cmd+Sft+S` = Windows スクショ

### Layer 2: NUM（`SPACE` 長押し）

```
-     1     2     3     +                         ^     &     ~     (     )
/     4     5     6     0   Ctrl+Alt+0  _          !     @     #     $     %
*(⇧)  7     8     9     .   =          trans       [     ]     {     }     \
                                                                              |
```

### Layer 3: ARROW（`TAB` 長押し）

```
ESC   前ﾀﾌﾞ ↑     次ﾀﾌﾞ                            -     -     -     -     -
Home  ←     ↓     →     End                       ←     ↓     ↑     →
⇧     -     -     -     -                          -     -     -     -     -
```

- 左手 `E/S/D/F` = 逆T字の矢印、右手 `H/J/K/L` = vim 風の矢印
- `前ﾀﾌﾞ` = Ctrl+Shift+Tab、`次ﾀﾌﾞ` = Ctrl+Tab
- ロータリーエンコーダ: `Ctrl+PageUp` / `Ctrl+PageDown`

### Layer 4: MOUSE（トラックボール操作で自動進入）

```
右ホーム:  J = 左クリック / K = 中央クリック / L = 右クリック
右下段:    N = Cmd+[（戻る）/ . = Cmd+]（進む）
右小指:    - = 次のディスプレイ（Ctrl+Alt+N）
```

トラックボール静止後は自動で抜ける（5秒）。`excluded-positions`（J/K/L クリック・`-`・M・`.`）はマウス操作中もレイヤーを維持。

### Layer 5: SCROLL（`-` 長押し）

トラックボールがスクロール動作になる（バインディングは全て透過）。

### Layer 6: BT（両親指コンボで進入）

```
右上段: bt_mac  bt_win  BT2  BT3  BT4
右下段: ... BT_CLR
左下: bootloader / BT_CLR_ALL
```

- `bt_mac` = BT プロファイル0 + MAC レイヤー固定、`bt_win` = BT プロファイル1 + WIN レイヤー固定

### Layer 7: FUNC（`ENTER` 長押し）

```
右上段:  F1  F2  F3  F4  F5
右ホーム F13 F6  F7  F8  F9  F10
右下/親指: F11 / F12
```

### Layer 8: AERO（`BACKSPACE` 長押し / AeroSpace 操作）

```
Q     W     E     R     T                         (Tab) (F)   (M)   (R)   (,)
WS1   WS2   WS3   WS4   WS5                        直前  全画面 ﾈｲﾃｨﾌﾞ ﾘｻｲｽﾞ 分割向き
A     S     D     F     G                          H     J     K     L
WSへ移動 1〜5（Alt+Shift+数字）                     ←     ↓     ↑     →（フォーカス）
Z     X     C     V     B                          N     M     ,     .     /
                                                   ←     ↓     ↑     →（ｳｨﾝﾄﾞｳ移動）  ﾚｲｱｳﾄ
```

- 右ホーム `H/J/K/L` = フォーカス移動（`alt-h/j/k/l`）
- 右下段 `N/M/,/.` = ウィンドウ移動（`alt-shift-h/j/k/l`、Shift 不要）
- 左上段 `Q〜T` = ワークスペース 1〜5（`alt-1〜5`）
- 左ホーム `A〜G` = ウィンドウをワークスペースへ移動（`alt-shift-1〜5`）
- `/` = レイアウト tiles/accordion 切替

> AeroSpace 設定本体は `~/.config/aerospace/aerospace.toml`。このレイヤーは Alt+◯◯ を送るだけなので toml 側の変更は不要。

### コンボ

| キー | 出力 |
|------|------|
| S + D | `Tab` |
| D + F | `Shift+Tab` |
| L + `-` | `"`（ダブルクォート） |
| C + V | `=` |
| Q + W | `Esc` |
| U + I | 前タブ（`Ctrl+Shift+Tab`） |
| I + O | 次タブ（`Ctrl+Tab`） |
| M + `,` | 戻る（`Cmd+[`） |
| `,` + `.` | 進む（`Cmd+]`） |
| 左親指 最外 + 左Shift位置 | `BT` レイヤー |
