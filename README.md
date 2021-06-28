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


