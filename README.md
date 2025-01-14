# MineHuntPvP
MineHuntPvPはActedが作った[ManhuntEarthMain](https://github.com/minecraftacted/ManhuntEarthMain)がBungeeCordで動いている環境でゲームマッチング機能を追加して、一般ゲームサーバーのようにするものです。
マッチング機能のために、Manhuntのプラグインは改造されています。
## インストール
### ロビーサーバーの設定
#### ロビープラグインの導入
- Paperで作成したサーバーを用意します。
- [MineHuntPvPLobbyer#releases](https://github.com/stsaria/MineHuntPvPLobbyer/releases)からロビープラグインをpluginsディレクトリにダウンロードします。
- BungeeCordにサーバーIDは`manhuntLobby`でサーバーを追加します（※）。
※サーバーIDはかならずmanhuntLobbyにしてください（これは、ゲーム終了後のロビー転送に使われます）。
#### ロビープラグインの設定
##### 設定ファイルについて
ロビープラグインの設定ファイルはロビーサーバー・Manhuntサーバーがどのように動くのかの設定が書かれています。

ここからロビープラグインの設定を変えますが、一回ロビープラグインを起動してから変えてください（デフォルトの設定を作成してからのほうがやりやすいです）。

※ロビープラグインはロビープラグインの設定を一番に優先します。間違えないでください。

設定ファイルは`plugins/MineHuntPvPLobbyer/config.yml`です。

##### 初期状態
``` yaml
serverTimeoutMinutes: 34 
mainServerOps:
- oun9
serverMoveWaitSec: 60
gamePlayerMax: 4
manhuntMainDownloadURL: https://github.com/stsaria/MineHuntPvPMain/releases/download/v1.0/ManhuntEarthMain-1.0-SNAPSHOT.jar
ports:
- 25570
- 25571
```
##### 設定項目
- `serverTimeoutMinutes`: Manhuntサーバーの最大起動時間
- `mainServerOps`: ManhuntサーバーのOPプレイヤーリスト  
  最初には自分のユーザー名が書いてありますが、ここは自分のユーザー名に変更してください
- `serverMoveWaitSec`: Manhuntサーバーに移動するまでの待機時間
- `gamePlayerMax`: Manhuntの最大プレイヤー  
  最大値:`6`
- `manhuntMainDownloadURL`: ManhuntプラグインのダウンロードURL（改造プラグインを使用しない場合は変更しないでください）
- `ports`: サーバーポートリスト  
  ポートの数だけサーバーの数が増えます。  
### BungeeCordの設定
さっき設定した`ports`項目のポートをすべてBungeeCordの設定にも`manhunt-ポート番号`という項目で`address: localhost:ポート番号`として追加します。