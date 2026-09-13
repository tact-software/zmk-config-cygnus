# zmk-config-cygnus

無線分割キーボード [Cygnus-S](https://github.com/Dist16384/Cygnus-S)(Dist16384 作)用の ZMK 設定です。
Cygnus は [roBa](https://github.com/kumamuk-git/zmk-config-roBa)(kumamuk-git 作)インスパイアのキーボードで、
本リポジトリは自作の [zmk-config-roBa](https://github.com/tact-software/zmk-config-roBa) のキーマップと
カスタム機能を Cygnus に移植したものです。

## 特徴

- **オートマウスレイヤー**: ドライバ内蔵の `automouse-layer` ではなく、ZMK 公式の
  input processor (`zip_temp_layer`) で実現。タイピング直後の誤発動抑制
  (`require-prior-idle-ms`) と特定キーでのレイヤー維持 (`excluded-positions`) に対応
- **トラックボールジェスチャ**: ジェスチャレイヤーを押しながらトラックボールを弾くと
  ウィンドウ切替/タブ操作を発火する自作 input processor (`src/input_processors/`)
- **マウスクリック即時レイヤー離脱**: クリック後にマウスレイヤーを素早く抜ける
  自作 behavior (`src/behaviors/`)
- **OS 切替**: BT プロファイル切替と同時に Mac/Windows モードを確定する
  `&bt_mac` / `&bt_win` マクロ。スクロール方向・IME 切替・ジェスチャキーが OS に追従
- **ホームロウ Mod**、tri-layer、RGB LED ウィジェット(バッテリー残量・レイヤー表示)

## ハードウェア

- Seeed XIAO BLE × 2、右手: PMW3610 トラックボール(セントラル)、左手: 48 ステップロータリーエンコーダ
- ピン配置・マトリクスは Cygnus-S / roBa 互換

## ビルド

GitHub Actions でビルドされます(`build.yaml` 参照)。右手側は ZMK Studio 対応
(`studio-rpc-usb-uart` スニペット)です。

## クレジット

- キーボード設計・ハードウェアパラメータ: [Dist16384/Cygnus-S](https://github.com/Dist16384/Cygnus-S)
- オリジナルの roBa 設計: [kumamuk-git/zmk-config-roBa](https://github.com/kumamuk-git/zmk-config-roBa)
- PMW3610 ドライバ: [Dist16384/zmk-pmw3610-driver](https://github.com/Dist16384/zmk-pmw3610-driver)
- RGB LED ウィジェット: [caksoylar/zmk-rgbled-widget](https://github.com/caksoylar/zmk-rgbled-widget)

## ライセンス

本リポジトリのオリジナル部分は MIT License です。シールド定義の構成は roBa 由来、
ハードウェア固有のパラメータ値は Cygnus-S 由来です。
