### サーバーサイドイベント

SocketStream 0.2 ではクライアントの初期化時や、ハートビートの送信時、または切断時に独自のコードをサーバー側で実行できます。将来はさらに多くのイベントを追加する予定です。ユーザーのログオフ時にデータベースをクリーンアップしたい時にこの機能は役立ちます。

最新の利用可能なイベント一覧を確認して、実際にイベント処理を実装するには、新規プロジェクトを作成し、 /config/events.coffee ファイルを見てください（もちろんこのファイルは event.js に変換できます）。
利用可能なサーバーサイドイベントの一覧がこのファイルに載っています。使いたいイベントがあれば、コメントを外してください。

全てのサーバーサイドイベントは自動的にバックエンドサーバー間でロードバランシングされます。そのため、トラフィックが増加したら単純にサーバーをクラスタに追加するだけで済みます。

注釈：`client:disconnect` イベントを受け取っても、それはユーザーがログアウトしたことを意味しません。別のクライアント経由でまだ接続しているかもしれません。これは大部分をアプリケーションレベルにおいて、良いデザインで解決すべき問題です。
