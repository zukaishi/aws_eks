# aws_eks

# 参考
- https://business.ntt-east.co.jp/content/cloudsolution/column-try-40.html
- https://qiita.com/ezaqiita/items/74e4ef80e63f98dbea1f


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
$ curl -LO https://storage.googleapis.com/kubernetes-release/release/v1.10.0/bin/darwin/amd64/kubectl
```

- そのほかの場合
```
$ curl -LO https://storage.googleapis.com/kubernetes-release/release/v1.10.0/bin/linux/amd64/kubectl
```

```
$ chmod +x ./kubectl
```
```
Client Version: version.Info{Major:"1", Minor:"10", GitVersion:"v1.10.0", GitCommit:"fc32d2f3698e36b93322a3465f63a14e9f0eaead", GitTreeState:"clean", BuildDate:"2018-03-26T16:55:54Z", GoVersion:"go1.9.3", Compiler:"gc", Platform:"darwin/amd64"}
```
