# evaluation-tracer
イヴァリュエーション・トレーサーの作り方

## 背景

承認力がどのくらい得られているか、オンラインゲームのコラボイベントについて考えてみると、それはガチャが回った数で計測することができます。つまり、「イヴァリュエーション・トレーサー」は、BIツールで構築できるということになります。やってみましょう。

## Play With Docker によるお試し環境

環境を構築するために計算機リソースが必要ですが、自分のマシンにあれこれ入れたり、クラウドベンダにお金払ったり、きっと皆さん、したくないでしょう。そこで今回は、4時間だけ無料で使える [Play With Docker](http://play-with-docker.com/) を使うことにします。Docker Inc. 太っ腹。

因みに、 Play With Docker は、 docker-compose.yml を docker swarm でデプロイしてくれる環境なので、振る舞いに多少の差異はありますが、 docker-compose が使える自前環境で、このプロジェクトをデプロイすることもできます。てゆーか、これ作る作業は、Windows上のDocker環境でやってます。

## Play With Docker へのデプロイ

下のボタンをCTRL押しながらポチってください。

<a href="http://play-with-docker.com?stack=raw.githubusercontent.com/mnagaku/evaluation-tracer/master/docker-compose.yml"><img src="https://github.com/play-with-docker/stacks/raw/cff22438cb4195ace27f9b15784bbb497047afa7/assets/images/button.png" /></a>

## Jupyter の準備

デプロイが終わったら、 Play With Docker のコンソールで、 Jupyter のコンテナ名を確認します。

```
docker ps --filter name=jupyter
```

「pwd_jupyter.1.hogehoge」な感じの名前を確認できると思います。このコンテナ名を使って、起動時ログを確認し、 Jupyter へのアクセスに必要なトークンを確認します。

```
docker logs pwd_jupyter.1.hogehoge 2>&1 | grep 'is running at'
```

Play With Docker のコンソールに「8.8.8.8」というリンクがあり、これをポチると Jupyter にアクセスできます。初回のアクセスでは、確認したトークンを入力する必要があります。

 Jupyter が操作できる状態になったら、[evaluation-tracer-1st.ipynb](https://raw.githubusercontent.com/mnagaku/evaluation-tracer/master/evaluation-tracer-1st.ipynb)を Jupyter に Upload してください。

以降の操作は、 Upload した evaluation-tracer-1st.ipynb に続きがあります。
