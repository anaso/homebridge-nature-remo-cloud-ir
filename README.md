# Homebridge Nature remo Cloud IR
## Nature remo に登録済みの赤外線信号をHomebridge経由で送信するためのツール

### こちらのテンプレートを使用しています。
[homebridge/homebridge\-plugin\-template: A template you can use to create your own Homebridge plugins\.](https://github.com/homebridge/homebridge-plugin-template)

### 使い方
- まずは公式アプリ等を使用して赤外線信号を登録しておきます。
- [https://home.nature.global/home](https://home.nature.global/home) に接続してアクセストークンを取得します。
- ` curl -X GET "https://api.nature.global/1/appliances" -H "authorization: Bearer <アクセストークン>" `へ接続し、問題無ければ一覧が帰ってきます。
 ```
<<省略>>
"model": null,
"type": "IR",
"nickname": "照明",
"image": "ico_light",
"settings": null,
"aircon": null,
"signals": [
  {
    "id": "<< Your ON ID >>",
    "name": "オン",
    "image": "ico_on"
  },
  {
    "id": "<< Your OFF ID >>",
    "name": "オフ",
    "image": "ico_off"
  }
]
<<省略>> 
```
- ` config.json ` へ記載されていたシグナルのIDを入力します。オンオフが同じボタンの際は両方に同じIDを記入してください。
```
"accessories": [
    {
        "accessory": "AnasoNatureRemoCloudIR",
        "name": "Your device name (for homekit)",
        "accessToken": "Your access token",
        "onSignalId": "Your ON ID (signals -> id)",
        "offSignalId": "Your OFF ID (signals -> id)"
    }
]
```
- 問題無ければ動いてくれるはず！
