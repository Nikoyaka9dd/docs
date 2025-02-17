---
title : Losettaを更新する
summary : この記事では、Losettaの実装を更新する方法について説明します。
---
### はじめに
Losettaは、不具合の修正やAliceScriptの更新に応じて新しいプログラムが配信されます。ユーザーのみなさんは、できるだけ最新のLosettaを使用することが求められています。

> [!WARNING] 古い情報
> Losetta 0.9.14からは、自動で`update`スクリプトが生成されるようになりました。このため、このバージョン以降の環境では`alice update`コマンドを実行するだけで更新できます。

> [!WARNING] 権限の付与が必要
> LinuxやmacOSなどのUnix環境では、更新を完了した後で実行ファイルに実行権限を与える必要があります。権限を与えるには、次のコマンドを実行します。
>
> `sudo chmod +x /usr/local/bin/alice`

### 更新スクリプトのダウンロード
更新用スクリプトはAliceScriptがインストールされていれば次のコマンドで導入できます。
```sh title="シェル"
alice install --args https://docs.wsoft.ws/products/alice/tutorial/media/update
```

### 更新スクリプトの編集
ダウンロードしたスクリプトを開き、最初の行を編集します。

```js title="update"
// 実行ファイルのファイル名
// Windowsの場合は"{0}alice.exe"をアンコメント
const target_filename = "{0}alice";
// const target_filename = "{0}alice.exe";

// アップデートの公開先
const download_id =144;
```

アップデートの公開先は、環境に応じて次の値を使用してください。

|ID|環境|
|---|---|
|WS144|Linux-x64|
|WS145|Linux-arm|
|WS146|Linux-arm64|
|WS147|macOS-x64|
|WS148|Windows-x64|
|WS149|Windows-x86|
|WS150|Windows-ARM64|
|WS151|Windows-ARM|


### 更新実行
編集済みのスクリプトを実行すると、必要な場合は更新が実行されます。

```bash title="シェル"
>alice -r update
https://api.wsoft.ws/download/detail?id=148&feature=version から最新バージョンを取得しています...
最新バージョン : 0.9.11.0
この実装よりも新しい実装が公開されています。
K:\LocalFiles\Docments\WSOFT\Losetta\alice\bin\Debug\net6.0\alice.exe
https://download.wsoft.ws/148/Download から最新バイナリをダウンロードしています...
0.9.11.0に更新しました。
```