# proofreading-api

## 今回は下記のように文章校正のapiを作っていく


![api-gateway-sagemaker-1](https://user-images.githubusercontent.com/62798122/184586514-fa11e494-1423-46bc-8952-29e3f6a44c38.gif)

[1] Amazon API Gateway マッピングテンプレートと Amazon SageMaker を使用して機械学習を搭載した REST API の作成　

https://aws.amazon.com/jp/blogs/news/creating-a-machine-learning-powered-rest-api-with-amazon-api-gateway-mapping-templates-and-amazon-sagemaker/
より

[使用する技術]

・AWS(sagemaker、sagemakerendpoint、apigateway、S3)
・BERT
・python

## 4つの手順

### 1.モデルファイルと同じ階層にcodeフォルダを作成し、そこにトークナイザとモデルの読み込みおよび推論処理を実装した推論スクリプトinference.pyと追加でインストールする必要のあるライブラリを記載したテキストファイルrequirements.txtを配置しそれらを格納したtar.gz形式のファイルを作成する。

### 2.作成したtar.gz形式のファイルをS3にアップロード

### 3.SageMaker Python SDKのHuggingFaceModelクラスのmodel_data引数にtar.gz形式のファイルのアップロード先のS3パスを指定し、deployメソッドによりモデルをデプロイしたエンドポイントを作成する。

### 4.作成されたエンドポイントに対してpredictメソッドにより推論を実行する。

