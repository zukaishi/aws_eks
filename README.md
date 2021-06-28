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
コンソールでの作業
<img width="1282" alt="スクリーンショット 2021-06-29 6 20 54" src="https://user-images.githubusercontent.com/22611735/123706344-22337a80-d8a3-11eb-9858-4ff65f38ae0e.png">
<img width="1315" alt="スクリーンショット 2021-06-29 6 23 08" src="https://user-images.githubusercontent.com/22611735/123706408-37100e00-d8a3-11eb-9a7d-7e6701b9c0aa.png">
<img width="1308" alt="スクリーンショット 2021-06-29 6 23 26" src="https://user-images.githubusercontent.com/22611735/123706414-3a0afe80-d8a3-11eb-9e81-3b97ce8ae6cc.png">
<img width="1328" alt="スクリーンショット 2021-06-29 6 23 33" src="https://user-images.githubusercontent.com/22611735/123706429-3d05ef00-d8a3-11eb-946b-473054ba09f5.png">
<img width="1089" alt="スクリーンショット 2021-06-29 6 23 54" src="https://user-images.githubusercontent.com/22611735/123706437-3ecfb280-d8a3-11eb-8d42-5c7eb993b90d.png">
<img width="1009" alt="スクリーンショット 2021-06-29 6 26 45" src="https://user-images.githubusercontent.com/22611735/123706451-42633980-d8a3-11eb-95ce-17d6999477ce.png">

