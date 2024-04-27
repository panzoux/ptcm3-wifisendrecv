### WFSEND1, WFRECV1 画面付き手順

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
