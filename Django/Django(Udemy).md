#Django(Udemy講座)メモ  
●Class:データと命令をセットにしたひな形  
●マイグレーション:データを統合する、データを移行する（アプリ開発において）  
●データベース記入用テーブルなどの作成 : python manage.py migrate  
●Djangoサーバーの起動方法:python manage.py runserver  
●Djangoのリクエスト処理フロー説明（クライアント→ルーティングファイル→ビュー→クライアント）  
●renderメソッド：指定されたテンプレートをレンダリングして、HttpResponseを返す（レスポンス）ためのメソッド  
●models:モデルとは、Webアプリケーションとデータベースを連携させる仕組み。 モデルはデータベースに格納されているデータにアクセス可能。 Djangoではモデルを使うことで、簡単にデータベースからデータの検索・取得・追加・削除といった一連のデータベース操作を行うことができる。  
●manage.py　〇〇　:　Djangoを操作する際に用いることが多いコマンド  
●manage.py makemigrations：新たな定義ファイルがあった場合にそれをDBに投入するためのファイルを自動生成してくれる。  
●sqlite3 db.sqlite3：データベースを対話形式で操作可能になるコマンド。  
●manage.py createsuperuser :djangoの管理者ユーザーを作る。  
●命令__str__:文字列を返す  
●order_by('-published')：公開日の降順でソート  
●return 〇〇body[:100]  
●HTML　div：Divisuion・四角形領域 コンテンツを囲んで配置をしたり動かしたりする仕組み  
●HTML　<!-- コメントアウト-->  
●HTML ｛% load static %｝に関して。これ宣言すれば以降のstaticでsetting.pyにより指定したフォルダのパスを指定できる。  
●HTML　％％　ディレクティブタグディレクティブとはJSPページの文字コードを指定したり外部のファイルを読み込んだりといったJSPページに関する制御文を記述する箇所  
