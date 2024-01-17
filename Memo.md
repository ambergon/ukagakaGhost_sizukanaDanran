




# 開発メモ
## アップデート作法
Version UPは versionリポジトリを使用する。
このリポジトリにプッシュされた時、自動でリリースが作成される。

1. Release.md に更新内容を書き溜める。
    [v1.xxx -> v1.xxx]と始める。

1. Update ファイルを作る。
    Ghost -> Del -> U

1. git commit 
1. git push origin master
1. git push origin version
1. git tag v1.xxx
1. git push origin v1.xxx

1. ReadMe.mdにRelease.mdの内容を移す。



## 基本方針
起動・終了を除いて、自分から発言する機能は導入しない。


## 命名規則
functionは専用メニューを持つ機能を指す。
systemは発言を主目的としない処理を指す。
talkを発言を主目的とする処理を指す。



## 主要関数
### 接頭辞
#### AutoLoad.
起動時に実行される関数群
初期化等に使用する。


#### AutoUnload.
終了時に実行される関数群
セーブデータを綺麗に維持したりする。


#### OnMenu.
起動時に生成される。 リアルタイムでない点に注意すること。
ダブルクリック時のメニューテキストは関数名OnMenu.XXXになる。


#### Status.
Del -> s を押したときに実行される。
Status.関数をすべて実行し、その返り値を表示する。


#### CheckSecond. / CheckMinute. / CheckHour.
Notifyの時はスキップ。
実行可能なときにその結果すべてを結合して出力する。


#### InputKey.
命名規則として実装している。
system.KeyPressから呼び出される。


#### GearUp.
撫でなど、現在の状態を変更したい時に`Surface.GearUp()`が呼ばれる。
この関数が呼ばれた時、次の状態へ一段階進む。
状態の変化が発生するとき、各種GearUp.関数が実行される。
発言をさせずに変数の初期化等を実行すること。


#### GearDown. 
時間経過により一段階状態が下がる。
状態が変化されるときGearDown.関数が呼ばれる。
発言させないこと。


#### TEST.test
接頭辞による検索はない。
当たり判定がない所をダブルクリックしたときに実行される。
TEST.ukaに記入する。
