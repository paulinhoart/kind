# Kind no WSL 
Kind (Kubernetes In Docker) Com 3 nodes e Ingress.

Contém Aplicação de exemplo com Deployment, Service, Ingress.


# DIAGRAMA
# DIAGRAMA
# DIAGRAMA
# DIAGRAMA
# DIAGRAMA


## Pré Requisitos
WSL
Docker no WSL
Kubectl
```bash
$ curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
$ sudo install -o root -g root -m 0755 kubectl /usr/local/bin/kubectl && rm kubectl
$ kubectl  version --client
Client Version: v1.33.4
Kustomize Version: v5.6.0
```
Não estar utilizando porta 80 e 443.

## Baixar e Instalar o Kind

```bash
[ $(uname -m) = x86_64 ] && curl -Lo ./kind https://kind.sigs.k8s.io/dl/v0.29.0/kind-linux-amd64
chmod +x ./kind
sudo mv ./kind /usr/local/bin/kind
```
Vamos conferir a instalação verificando a versão do kind.

```bash
$ kind --version
kind version 0.29.0
```

## Criar cluster 

Criar cluster com 1 control plane e 3 nodes.

```bash
$ kind create cluster --config kind-config.yaml
Creating cluster "kind" ...
 ✓ Ensuring node image (kindest/node:v1.33.1) 🖼
 ✓ Preparing nodes 📦 📦 📦 📦
 ✓ Writing configuration 📜
 ✓ Starting control-plane 🕹️
 ✓ Installing CNI 🔌
 ✓ Installing StorageClass 💾
 ✓ Joining worker nodes 🚜
Set kubectl context to "kind-kind"
You can now use your cluster with:

kubectl cluster-info --context kind-kind

Have a nice day! 👋
```
Vamos conferir o cluster

```bash
$ kubectl cluster-info --context kind-kind
Kubernetes control plane is running at https://127.0.0.1:38611
CoreDNS is running at https://127.0.0.1:38611/api/v1/namespaces/kube-system/services/kube-dns:dns/proxy

To further debug and diagnose cluster problems, use 'kubectl cluster-info dump'.
```

## Instalar ingress

