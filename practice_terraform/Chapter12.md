■12.2.1
●cli ssmコマンド
記載通りのコマンドではうまくいかない

aws   ssm   get-parameter  --output   text  --name  ' plain_ name'  \   --query   Parameter. Value
ではなく、
aws ssm get-parameter --name testDataTypeParameter --query "Parameter.Value"
https://docs.aws.amazon.com/ja_jp/systems-manager/latest/userguide/param-create-cli.html

●暗号化されたssmパラメータ
decryptionしない場合は暗号化された文字列が返される。

12.2.2
●CLIでのValue上書き
CLIからValueを上書きできてしまうがいいのか？（コンソールを操作可能な人、すなわち認証済みの人しか操作できないからいい？）

ここでOvewriteしているので再apply後ももう一度overwriteが必要。

●alpineとは
C標準ライブラリとしてmusllibcを採用し、BusyBoxをベースに利用して構築されたLinuxディストリビューションです。
https://charlie1012.hatenablog.jp/entry/2021/01/14/090000

●envコマンドとは
環境変数を設定してコマンドを実行するときに使うコマンド
https://wa3.i-3-i.info/word11209.html

→applyで動作未実行（書籍にapply工程無し）
