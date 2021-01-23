# Browser MCU for Ayame-Labo

- Browser MCU for Ayame-Labo は WebRTCシグナリングサービスの[Ayame Labo](https://ayame-labo.shiguredo.jp/)向けの、ブラウザによるMCU（映像、音声合成）ツールです
  - [ayame-web-sdk](https://github.com/OpenAyame/ayame-web-sdk) を利用しています(Apache 2.0 ライセンス)
- [Browser MCU Core](https://github.com/mganeko/browser_mcu_core) ライブラリを利用しています
- Browser MCU for Ayame-Labo は [Browser MCU](https://github.com/mganeko/browser_mcu) シリーズの一部です
- Browser MCU シリーズに関するプレゼン資料はこちら
  - [Node.js x Headless Chrome for WeRTC MCU / Node.js x Chrome headless で、お手軽WebRTC MCU](https://www.slideshare.net/mganeko/nodejs-x-headless-chrome-for-wertc-mcu-nodejs-x-chrome-headless-webrtc-mcu)

# LICENSE / ライセンス

MIT LICENSE / MITライセンス

# 利用方

## 事前準備

- GitHub アカウントで、[Ayame Labo](https://ayame-labo.shiguredo.jp/) にサインアップ
- シグナリングキーを取得


## GitHub Pagesで使う

### MCU側

- PCブラウザを起動(Chrome推奨)
- https://mganeko.github.io/browser_mcu_ayame/ にアクセス
- Signaling-Key: に Ayame Labo のシグナリングキーを入力
- Room-Prefix: にルームIDのプレフィッックスを入力
  - Username@Room の形式
  - 参加者側のブラウザが実際に接続するルームIDには、1始まりのの連番が付与される
- Room-Capacity （参加可能人数）を選択
- [Connect] ボタンをクリック

※ Room-Prefix: が「user@mcu-room」、Room-Capacity:で「4」を選択した場合は、参加者は次のRoomIDでぞれぞれ接続する

- user@mcu-room-1
- user@mcu-room-2
- user@mcu-room-3
- user@mcu-room-4

URLを次の形式で指定すると、シグナリングキーとルームIDのプレフィックスを指定可能

- https://mganeko.github.io/browser_mcu_ayame/?room=ルームプレフィックス&key=シグナリングキー


### 参加者側

- 各参加者ごとにブラウザを起動、それぞれ https://mganeko.github.io/react_ts_ayame/ にアクセス
- SignalingKey: に Ayame Labo のシグナリングキーを入力
- Room: にルームIDを入力
  - Username@RoomPrefix-連番 の形式
  - 連番は1始まり、参加者ごとに異なる連番を用いる
- [Start Video]ボタンをクリック
- [Connect]ボタンをクリックして接続
  - リモートの音量はゼロの状態なので、必要に応じて音量をあげてください
- ブラウザだけでなく、[WebRTC Native Client Momo](https://github.com/shiguredo/momo) の Ayame モードでも参加可能

URLを次の形式で指定すると、シグナリングキーとルームIDを指定可能

- https://mganeko.github.io/react_ts_ayame/?room=ルーム名&key=シグナリングキー

### 注意点

- MCU側のブラウザのウィンドウ/タブが完全に隠れてしまうと（最小化含む）映像の合成が停止してしまうため、必ず一部は表示した状態で利用する

# コードを取得する場合

サブモジュールを利用しているので、--recursiveをつけて取得してください

```
$ git clone --recursive https://github.com/mganeko/browser_mcu_ayame.git
```

