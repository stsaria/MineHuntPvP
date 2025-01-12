# MineHuntPvP
MineHuntPvPはActedが作った[ManhuntEarthMain](https://github.com/minecraftacted/ManhuntEarthMain)がBungeeCordで動いている環境でゲームマッチング機能を追加して、一般ゲームサーバーのようにするものです。
マッチング機能のために、Manhuntのプラグインは改造されています。
## ルール
マッチング時のルールです。
- すべてのゲームが4人で行われます（多くも少なくもなくちょうど）。
- 1ゲーム1サーバーで行われます。プラグインによるワールドの共有はしません。
## システム的ルール
- ロビーサーバーとメインサーバーは同じシステムの上で動かる必要があります。
- メインサーバーとして認識されるには以下の条件が必要です。
  - server.jarファイルとしてマイクラの本体サーバーが存在すること
  - pluginsディレクトリがあり、その中にmanhunt.jarファイルとしてManhuntのメインプラグインが存在すること
## インストール
### ロビーサーバー
- Paperで作成したサーバーを用意します。
- [MineHuntPvPLobbyer#releases](https://github.com/stsaria/MineHuntPvPLobbyer/releases)からロビープラグインをpluginsディレクトリにダウンロードします。
- BungeeCordにサーバーIDはmanhuntLobbyでサーバーを追加します（※）。
※サーバーIDはかならずmanhuntLobbyにしてください（これは、ゲーム終了後のロビー転送に使われます）。
### メインサーバー
ここから、めんどくさいものが多いです。書き方が悪いのですが、必ずこうしてください。こうしないと動きません。
Linuxコマンドだけは理解用に置いておきます。
- ロビーサーバーが動いているLinuxユーザーのメインディレクトリに移動して、manhuntServersディレクトリを作成します。
- manhuntServersディレクトリの中にサーバーのポート番号のディレクトリを作成します（例:25570）（※）。
※他のプログラムと衝突しないようにしてください。ポート番号だけ（25570のようなアラビア数字・十進数・半角のポート番号）にしてください。
- 作成したポート番号の中にファイル名server.jarでPaperのサーバーファイルをダウンロードします（※）。
※server.jar以外のファイル名だと認識されません。
- 同じディレクトリにpluginsフォルダを作成し、その中に[MineHuntPvPMain#releases](https://github.com/stsaria/MineHuntPvPMain/releases)からメインプラグインをファイル名manhunt.jarでダウンロードします。
```bash
pwd
-> /home/minecraft
mkdir manhuntServers
cd manhuntServers
mkdir 25570
cd 25570
curl -Lo server.jar https://api.papermc.io/v2/projects/paper/versions/1.21/builds/130/downloads/paper-1.21-130.jar
mkdir plugins
cd plugins
curl -Lo manhunt.jar https://github.com/stsaria/MineHuntPvPMain/releases/download/v1.0/ManhuntEarthMain-1.0-SNAPSHOT.jar
.......
```
- BungeeCordにサーバーID"manhunt-ポート番号"（例:manhunt-25570）でサーバー登録してください（※）。
※サーバーアドレスもlocalhost:25570のようにポート番号に合わせてください。

ここまでやったらポート番号のディレクトリを他のポート番号にコピーすることによって、BungeeCordの設定以外は簡単に複製できます。
```bash
pwd
-> /home/minecraft/manhuntServers
ls
-> 25570
cp -r 25570 25571
```