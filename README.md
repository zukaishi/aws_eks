# aws_eks

# 参考
- https://business.ntt-east.co.jp/content/cloudsolution/column-try-40.html
- https://qiita.com/ezaqiita/items/74e4ef80e63f98dbea1f
- https://kubernetes.io/ja/docs/tasks/tools/install-kubectl/

```
curl --silent --location "https://github.com/weaveworks/eksctl/releases/latest/download/eksctl_$(uname -s)_amd64.tar.gz" | tar xz -C /tmp
sudo mv /tmp/eksctl /usr/local/bin
eksctl version 
```
```
$ 0.54.0
```

- macの場合
```
$ curl -LO "https://storage.googleapis.com/kubernetes-release/release/$(curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt)/bin/darwin/amd64/kubectl"
```

- そのほかの場合
```
$ curl -LO "https://storage.googleapis.com/kubernetes-release/release/$(curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt)/bin/linux/amd64/kubectl"
```

```
$ chmod +x ./kubectl
$ sudo mv ./kubectl /usr/local/bin
$ kubectl version --short --client
```
```
Client Version: v1.21.2
```

```
$ aws configure
$ AWS Access Key ID [None]: <アクセスキー>
$ AWS Secret Access Key [None]: <シークレットキー>
$ Default region name [None]: <リージョン>
```

```
vim KS-service-role.json
```
## コンソールでの作業

### EKSサービスロールのスタック作成
- スタックは、単一のユニットとして管理できる AWS リソースのコレクション。
- つまり、スタックを作成、更新、削除することで、リソースのコレクションを作成、更新、削除できます。

<img width="1282" alt="スクリーンショット 2021-06-29 6 20 54" src="https://user-images.githubusercontent.com/22611735/123706344-22337a80-d8a3-11eb-9858-4ff65f38ae0e.png">
<img width="1315" alt="スクリーンショット 2021-06-29 6 23 08" src="https://user-images.githubusercontent.com/22611735/123706408-37100e00-d8a3-11eb-9a7d-7e6701b9c0aa.png">
<img width="1328" alt="スクリーンショット 2021-06-29 6 23 33" src="https://user-images.githubusercontent.com/22611735/123706429-3d05ef00-d8a3-11eb-946b-473054ba09f5.png">
<img width="1308" alt="スクリーンショット 2021-06-29 6 23 26" src="https://user-images.githubusercontent.com/22611735/123706414-3a0afe80-d8a3-11eb-9e81-3b97ce8ae6cc.png">
<img width="1089" alt="スクリーンショット 2021-06-29 6 23 54" src="https://user-images.githubusercontent.com/22611735/123706437-3ecfb280-d8a3-11eb-8d42-5c7eb993b90d.png">
<img width="1009" alt="スクリーンショット 2021-06-29 6 26 45" src="https://user-images.githubusercontent.com/22611735/123706451-42633980-d8a3-11eb-95ce-17d6999477ce.png">

### EKSワーカーノードロールのスタック作成
- 同じようなものをもう一つ作る
- 「テンプレートの指定」の「テンプレートソース」に、「Amazon S3 URL」を選択し、その下段に「https://amazon-eks.s3.us-west-2.amazonaws.com/
cloudformation/2020-08-12/amazon-eks-nodegroup-role.yaml」して作成する

<img width="326" alt="スクリーンショット 2021-06-30 6 18 23" src="https://user-images.githubusercontent.com/22611735/123868775-1b703a80-d96b-11eb-89c0-9177054ddfbf.png">

### クラスター環境用VPCのスタック作成
- スタックをもう一つ作る
- 「テンプレートの指定」の「テンプレートソース」に、「Amazon S3 URL」を選択し、下段に「https://amazon-eks.s3.us-west-2.amazonaws.com/
cloudformation/2020-08-12/amazon-eks-vpc-sample.yaml」して作成する

<img width="327" alt="スクリーンショット 2021-06-30 6 23 22" src="https://user-images.githubusercontent.com/22611735/123869221-acdfac80-d96b-11eb-8953-0e46b3ec7935.png">


### EKSクラスターの設定を行うため、「出力」タブをクリックします。
- 「SecurityGroups、SubnetIds、VpcId」をメモ

<img width="1010" alt="スクリーンショット 2021-06-30 6 24 14" src="https://user-images.githubusercontent.com/22611735/123869351-d13b8900-d96b-11eb-8ee6-e81cff165fd0.png">

### EKSクラスターの作成
- EKSへ遷移し作成したスタック「EKS-service-role」を選択
- ネットワーキングでは、「eks-cluster-vpc」を選択、SecurityGroupsを選択


<img width="1091" alt="スクリーンショット 2021-07-02 6 20 58" src="https://user-images.githubusercontent.com/22611735/124190804-d6304200-dafd-11eb-8376-67a837756cce.png">

<img width="1093" alt="スクリーンショット 2021-07-02 6 25 32" src="https://user-images.githubusercontent.com/22611735/124191142-50f95d00-dafe-11eb-87ba-dcb0f3a55944.png">

### kubeconfigファイルの作成
```
$ aws_eks hishizuka$ aws eks --region ap-northeast-1 update-kubeconfig --name eks-cluster
$ Updated context arn:aws:eks:ap-northeast-1:431928468872:cluster/eks-cluster in /Users/hishizuka/.kube/config
```
```
$ kubectl get svc
$ error: You must be logged in to the server (Unauthorized)
```
ここで足止め、権限不足かな
https://qiita.com/keng000/items/4afe077c649ec3e22ef5#eks%E3%81%AB%E3%81%A6rbac%E3%83%AD%E3%83%BC%E3%83%AB%E3%82%92%E4%BB%98%E4%B8%8E%E3%81%99%E3%82%8B%E6%96%B9%E6%B3%95

この辺りな気がする

