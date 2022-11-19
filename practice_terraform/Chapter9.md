●9.4 iam moduleに関してエラー発生
│ Error: Reference to undeclared resource
│ 
│   on clodwatchlogs.tf line 29, in module "ecs_task_execution_role":
│   29:     policy = data.aws_iam_policydocument.ecs_task_execution.json
│ 
│ A data resource "aws_iam_policydocument" "ecs_task_execution" has not been declared in the root module.
╵


●IAMの割り当て手順（ECSに割り当てる場合）
IAMポリシーを定義
上記のポリシーをドキュメントに落とす
上記のドキュメントを使ってECSに割り当てる。

9章本構築（Forgate）の参照サイト
https://qiita.com/tutuz/items/d6181d96c943092e8c8d

●9章apply時のエラー
＃エラー１
│ Error: error creating ECS service (example): InvalidParameterException: The target group with targetGroupArn arn:aws:elasticloadbalancing:ap-northeast-1:036838409227:targetgroup/example/401d562514a1a6fe does not have an associated load balancer.
│ 
│   with aws_ecs_service.example,
│   on ecs.tf line 18, in resource "aws_ecs_service" "example":
│   18: resource "aws_ecs_service" "example" {
│ 


→解決策
https://houdoukyokucho.com/2022/07/14/post-4158/

ECS のサービスの定義に「DependsOn: リスナー」を追加する。
・Amazon ECS サービスでは、ApplicationLoadBalancer リスナールールと ApplicationLoadBalancer リスナーに明示的に依存する必要があります。これにより、リスナーの準備が整う前にサービスが開始されなくなります。

リスナーをデプロイしてからECSをデプロイする必要があるｂ。
二回実行すればデプロイできる
またはdependsonを記述してリスナーを指定。

depends_on=各種リスナー、リスナールール.example


＃エラー２
│ Error: creating ELBv2 Listener (arn:aws:elasticloadbalancing:ap-northeast-1:036838409227:loadbalancer/app/example/e918de11c902867f): UnsupportedCertificate: The certificate 'arn:aws:acm:ap-northeast-1:036838409227:certificate/8a114414-0e88-4f88-9a08-411ae3d7549c' must have a fully-qualified domain name, a supported signature, and a supported key size.
│       status code: 400, request id: 14062aee-a5ab-44f4-822b-a6497ec177fe
│ 
│   with aws_lb_listener.https,
│   on lb.tf line 71, in resource "aws_lb_listener" "https":
│   71: resource "aws_lb_listener" "https" {

→
証明書がまだ検証待ちの場合、このエラーを受け取ることがあります。

aws_acm_certificate_validationは、作ったACM証明書と、そのvalidation用に作ったDNSレコードを紐付けるリソースです。（前提としてACM証明書の検証方法としてDNS検証を選択しています。）検証完了=このリソース作成完了になります。

depends_onを入れておかないと、aws_acm_certificate_validation 再作成完了前にaws_alb_listenerの変更、つまりACM証明書の旧→新への付け直しが始まっています。検証完了前のACM証明書がALBに紐付けられることになります。そのためError modifying LB Listener: UnsupportedCertificate:というエラーが出たと考えられます。

https://dev.classmethod.jp/articles/dnsrecord-acm-alb-with-terraform/

