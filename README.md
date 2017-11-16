※2017/11/16現在、PWDの仕様変更でコンテナイメージのサイズの制約が強くなってしまったため、PWDで動かすことができません...

# evaluation-tracer
イヴァリュエーション・トレーサーの作り方

## 背景

承認力がどのくらい得られているか、オンラインゲームのコラボイベントについて考えてみると、それはガチャが回った数で計測することができます。つまり、「イヴァリュエーション・トレーサー」は、BIツールで構築できるということになります。やってみましょう。

## Play With Docker によるお試し環境

環境を構築するために計算機リソースが必要ですが、自分のマシンにあれこれ入れたり、クラウドベンダにお金払ったり、きっと皆さん、したくないでしょう。そこで今回は、4時間だけ無料で使える [Play With Docker](http://play-with-docker.com/) を使うことにします。Docker Inc. 太っ腹。

因みに、 Play With Docker は、 docker-compose.yml を docker swarm でデプロイしてくれる環境なので、振る舞いに多少の差異はありますが、 docker-compose が使える自前環境で、このプロジェクトをデプロイすることもできます。てゆーか、これ作る作業は、Windows上のDocker環境でやってます。

## Play With Docker へのデプロイ

下のボタンをCTRL押しながらポチってください。

<a href="http://play-with-docker.com?stack=https://raw.githubusercontent.com/mnagaku/evaluation-tracer/master/docker-compose.yml"><img src="https://github.com/play-with-docker/stacks/raw/cff22438cb4195ace27f9b15784bbb497047afa7/assets/images/button.png" /></a>

ロボット除けをかいくぐってセッションに進むと、デプロイが始まります。

## Jupyter へのアクセス

デプロイが終わったら、 Play With Docker のコンソールでインスタンスを選択状態にしてください。「8.8.8.8」というリンクができているので、これをポチって Jupyter にアクセスします。初回のアクセスでは、トークンの入力を求められますが、デプロイを定義した[docker-compose.yml](https://github.com/mnagaku/evaluation-tracer/blob/master/docker-compose.yml#L35)にトークンを指定している箇所があり、「etpassword」と入力してください。

Jupyter には「evaluation-tracer」フォルダができているので、その中に進み、「evaluation-tracer.ipynb」を開いてください。以降の操作は、そこに続きがあります。

因みに Play With Docker のコンソールの「8.0.8.8」というリンクの方は、「evaluation-tracer」へのリンクになります。念のため。

あと、 Play With Docker 、EC2のスポットインスタンスなのか、1度、突然死することがありました。突然死があり得るので、そこは、そーゆーもんだと思って使うのが良いようです。
