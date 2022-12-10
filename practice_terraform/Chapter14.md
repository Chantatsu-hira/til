■14.2
・EOFとは  
https://wa3.i-3-i.info/word12527.html  
EOFとは、ファイルの終わりを示す制御コードのことである。  

・EOFのエラー  
ECRのライフサイクルポリシーを設定するtfファイルにて  
policy = <<EOF
という記載でjsonを書くと下記エラー  

"policy" contains an invalid JSON: invalid character '\n' in string literal  

→下記記載に変更  
policy = jsonencode(　内容　）  
上記でjsonへ変換する。  

・ECRライフサイクルポリシー  
https://docs.aws.amazon.com/ja_jp/AmazonECR/latest/userguide/lifecycle_policy_examples.html

テンプレート、各パラメータの説明  
https://docs.aws.amazon.com/ja_jp/AmazonECR/latest/userguide/LifecyclePolicies.html


・get-loginコマンド  
AWS CLI Version 2では、get-loginは削除された。
代わりにget-login-passwordを使おう
https://qiita.com/hayao_k/items/3e4c822425b7b72e7fd0

