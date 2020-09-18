+++ 
date = "1979-01-01"
title = "kubernetes"
description = "kubernetes"
+++


<h2 id=Kubernetes>Kubernetes
<img src="https://kubernetes.io/images/favicon.png" height="100" width="100" align="right">
</h2>


> ### minikube

https://kubernetes.io/docs/tasks/tools/install-minikube/

#### Install
```bash
curl -Lo minikube https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64 && chmod +x minikube
sudo cp minikube /usr/local/bin && rm minikube
```
> ### Kubectl

https://kubernetes.io/docs/tasks/tools/install-kubectl/

#### Install
```bash
export latest=`curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt`

curl -LO https://storage.googleapis.com/kubernetes-release/release/$latest/bin/linux/amd64/kubectl

chmod +x ./kubectl

sudo mv ./kubectl /usr/local/bin/kubectl
```

> ### Helm

https://helm.sh/

#### Install
```bash
curl https://raw.githubusercontent.com/helm/helm/master/scripts/get | bash
helm init
```
> ### kubectx et kubens

https://github.com/ahmetb/kubectx

#### Install
```bash
git clone git@github.com:ahmetb/kubectx.git ~/.kubectx
sudo ln -s ~/.kubectx/kubectx /usr/local/bin/kubectx
sudo ln -s ~/.kubectx/kubens /usr/local/bin/kubens
```
> ### kubetail

https://github.com/johanhaleby/kubetail

#### Install
```bash
git clone git@github.com:johanhaleby/kubetail.git ~/.kubetail
sudo ln -s ~/.kubetail/kubetail /usr/local/bin/kubetail
```
