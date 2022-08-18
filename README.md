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

## 5つの手順

### 1.モデルファイルと同じ階層にcodeフォルダを作成する。

### 2.codeフォルダにトークナイザとモデルの読み込みおよび推論処理を実装した推論スクリプトinference.pyと追加でインストールする必要のあるライブラリを記載したテキストファイルrequirements.txtを配置しそれらを格納したtar.gz形式のファイルを作成する。

### 3.作成したtar.gz形式のファイルをS3にアップロード

### 4.SageMaker Python SDKのHuggingFaceModelクラスのmodel_data引数にtar.gz形式のファイルのアップロード先のS3パスを指定し、deployメソッドによりモデルをデプロイしたエンドポイントを作成する。

### 5.作成されたエンドポイントに対してpredictメソッドにより推論を実行する。

注意：モデル保存は、bert.ipynbで、またtar.gz形式のファイル作成は各自で行ってください。
　　　APIGatewayの使い方は今回割愛させていただきます。


## 結果（GET、POST）今回は、野→の、先行→専攻の校正がしっかりできているのか見てみる。

### GETメソッドを使って実装した場合

#### sentence=<'校正前文章'>

![スクリーンショット (113)](https://user-images.githubusercontent.com/62798122/185280305-bef6ebba-970c-4c9d-8021-acb8220a32c9.jpg)

### POSTメソッドを使って実装した場合

#### 校正ボタンを押して校正する。

![スクリーンショット (112)](https://user-images.githubusercontent.com/62798122/185280649-2a852c83-9ad3-4fed-b1b1-96d31524ed90.png)
