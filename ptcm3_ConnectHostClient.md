### WFSEND1, WFRECV1 画面付き操作手順

1. 送信側 (WFSEND1) → 親機 「はい」
    ![](images/2-1-SEND_willThisBeHost.png)

1. 受信側 (WFRECV1) → 子機 「いいえ」
    ![](images/2-2-RECV_willThisBeHostIMG_2665.png)

1. 送信側 何もしない
    ![](images/3-1-SEND_waitingForClient.png)

1. 受信側 親機の名前をタッチする
    ![](images/3-2-RECV_selectHostToConnect.png)

1. 受信側 「決定」
    ![](images/3-4-RECV_connectToSelectedHost.png)

1. 送信側 子機が表示されたら「実行」
    ![](images/3-3-SEND_isClientConnected.png)

    ![](images/3-5-SEND_ClientConnected.png)

1. 受信側 同期完了を待つ
    ![](images/3-6-RECV_syncing.png)

1. 送信側 「WAITING RECVSTART」と表示されることを確認
    ![](images/4-1-SEND_WFSEND_WAITINGRECVSTART.png)

1. 受信側 受信できる状態の合図としてボタンを押す (A,B,X,Y,L,Rのどれか)
    ![](images/4-2-RECV_WFRECV_PUSHBTNFORRECVREADY.png)

1. 送信側 何もしない。送信完了すると、受信側の完了を待ってワイヤレス通信を切断する
    ![](images/5-1-SEND_WAITINGRECVEND.png)

1. 受信側 受信完了すると終了する。受信したプログラムはSLOT3にあるので、問題なければ保存など。
    ![](images/5-2-RECV_RECVEND_WIFIdisconnected.png)

## シーケンス図
```mermaid
sequenceDiagram
    actor u as user
    participant o as 親機
    participant k as 子機

    note over u,k : 3DS本体のワイヤレス通信を有効にする
    u ->> o : wifi on
    u ->> k : wifi on

    note over u,k : 送信、受信プログラムを実行
    u ->> +o : load,run WFSEND1
    u ->> +k : load,run WFRECV1

    note over u,k : プチコン3号で親機と子機を接続

    note over k : 親機になりますか？
    u ->> k : いいえ

    note over o : 親機になりますか？
    u ->> o : はい

    note over o : 子機の接続を待っています…
    note over k : 接続する親機の名前を<タッチして選択してください
    u ->> k : 親機の名前をタッチ
    note over k : 決定ボタンをタッチすると選択した親機に接続します
    u ->> k : 決定
    k ->> o : 親機が選択された
    o ->> o : 子機の名前が表示される
    u ->> o : (全ての子機が接続されたら)<br>実行

    note over k : 同期中です…

    note over u,k : 送受信プログラムでプログラムを転送

    loop 子機ボタン待ち
    note over o : WAITING RECVSTART
    note over k : PUSH BUTTON FOR RECV READY
    u ->> k : BUTTON A ( or B,X,Y,L,R)
    end

    k ->> o : RECV READY
    o ->> k : 行数
    loop 全ての行について
    o ->> k : SLOT3のプログラム行送信
    k ->> k : プログラム行受信しSLOT3へ格納
    end

    loop 受信完了待ち
    note over o : WAITING RECVEND
    note over k : RECV END
    k ->> o : RECVEND
    end

    o ->> k : 通信終了
    o ->> -u : プログラム終了

    note over k : ワイヤレス通信が切断されました
    u ->> k : 了解
    k ->> -u : プログラム終了

```
