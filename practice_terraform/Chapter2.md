■exampleフォルダ配置場所
/root/example

■Terafformコマンド
aws環境設定コマンド（シークレットキーなど）
は、tfファイルを格納したフォルダ（実際の作業場所）にて実施しなければならない。

・リージョンを合わせなければインスタンスを作れない
Terraform apply を実行すると下記メッセージが出る。
Error launching source instance: InvalidAMIID.NotFound: The image id '[ami-0c3fd0f5d33134a76]' does not exist
        status code: 400, request id: 1b3b127a-e0c7-4cd2-b85b-591a28065801
  
  ■Terraformが実施できない
Error: Invalid legacy provider address」に対処する
https://qiita.com/ymnk3/items/46ec33eb71779b03fa8a

■aws の認証一覧はUbuntuのIPが変わるたびに設定が必要？
