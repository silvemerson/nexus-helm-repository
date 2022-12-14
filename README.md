# Nexus Helm Repository

## Environment

Nome       | vCPUs | Memoria RAM | IP            | S.O.¹           | Script de Provisionamento²
---------- |:-----:|:-----------:|:-------------:|:---------------:| -----------------------------
nexus-server       | 1     | 2048MB      | 172.150.56.10 | devopsbox/ubuntu-20.04 | 
k3s    | 1     | 2048MB       | 172.150.56.20 | devopsbox/ubuntu-20.04 | 

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
curl -u helm:helmpass http://172.150.56.10:8081/repository/helm-repository --upload-file super-mario-0.0.1.tgz -v

```

## Accessing the Helm repository

```
helm repo add super-mario http://172.150.56.10:8081/repository/helm-repository/ --username helm --password helmpass

```

## Installing Helm charts from Nexus

```
helm repo update
helm install --repo http://172.150.56.10:8081/repository/helm-repository/ super-mario super-mario 

```

https://help.sonatype.com/repomanager3/nexus-repository-administration/formats/helm-repositories