# Nexus Helm Repository

## Environment

Nome       | vCPUs | Memoria RAM | IP            | S.O.┬╣           | Script de Provisionamento┬▓
---------- |:-----:|:-----------:|:-------------:|:---------------:| -----------------------------
nexus-server       | 1     | 2703MB      | 192.168.56.10 | silvemerson/ubuntu-20-04-ansible | 
k3s    | 1     | 2048MB       | 192.168.56.20 | silvemerson/ubuntu-20-04-ansible | 

```
git clone https://github.com/silvemerson/nexus-helm-repository.git

cd nexus-helm-repository

vagrant up

```

##  K3s, setting KUBECONFIG

```
export KUBECONFIG=/etc/rancher/k3s/k3s.yaml
```

## Pushing Helm charts to Nexus

```
helm package super-mario
curl -u helm_user:helmpass http://192.168.56.10:8081/repository/helm-repository/ --upload-file super-mario-0.0.1.tgz -v

```

## Accessing the Helm repository

```
helm repo add super-mario http://192.168.56.10:8081/repository/helm-repository --username helm_user --password helmpass

```

## Installing Helm charts from Nexus

```
helm repo update
helm install --repo http://192.168.56.10:8081/repository/helm-repository/ super-mario super-mario 

```

## Access APP

```
kubectl port-forward --address 0.0.0.0 pod/<PODNAME> 8080:8080
```

<img src="assents/supermario.gif" width="800" height="600" />

