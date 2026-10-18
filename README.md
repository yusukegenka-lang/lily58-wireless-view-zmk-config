# PandaKB Lily58 Pro Wireless — ZMK config

PandaKB 公式設定（[Penguinchat/zmk-for-PandaKB.com-](https://github.com/Penguinchat/zmk-for-PandaKB.com-) の `PandaKB_Lily58` ブランチ）をベースに、
自分のキーマップ（yusukegenka-lang/lily58-wireless-view-zmk-config）を入れた設定です。

## 変更点（PandaKB 公式との差分）
- `config/Lily58.keymap`：Base / Lower / Raise を自分のキーマップに置き換え。
  Lower と Raise を同時に押すと Adjust レイヤー（RGB 操作）になる仕組みは残しています。
  - Adjust：色相 ±、彩度 ±、エフェクト切替、明るさ ±、RGB オン/オフ、外部電源の切替
  - エンコーダー：左＝音量、右＝PageUp/PageDown（全レイヤー共通）
- `config/Lily58.conf`：チャタリング防止を自分の設定（押下 1ms / 離し 10ms）に変更。
- `build.yaml`：OLED・ドングルなしの左右と `settings_reset` だけをビルド。

## ビルド
GitHub に push すると Actions が動き、`firmware.zip` に以下が出力されます。
- `Lily58_left_oled.uf2`（左・ZMK Studio 対応）
- `Lily58_right_oled.uf2`（右）
- `settings_reset-nice_nano_v2-zmk.uf2`

## 書き込み手順（初回）
1. 左右それぞれに `settings_reset` を書き込みます（リセットボタンを2回押すと USB ドライブとして見えます）。
2. 左に `Lily58_left_oled.uf2`、右に `Lily58_right_oled.uf2` を書き込みます。
3. 左右の電源を入れ直し、同時に起動させます（左右どうしが自動でペアリングします）。
4. Windows の Bluetooth 設定で古い「Lily58」「PandaKB_Lily58」を削除し、`PandaKB_Lily58` をペアリングし直します。
