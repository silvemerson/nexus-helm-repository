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

## Accessing the Helm repository

```
helm repo add nexus http://192.168.88.20:8081/repository/helm-repository/ --username admin --password 4linux

helm fetch nexus/super-mario

```

## Pushing Helm charts to Nexus

```
helm package <chart_dir>
curl -u <username>:<password> http://<host>:<port>/repository/<repository_name>/ --upload-file mysql-1.4.0.tgz -v


```

## Installing Helm charts from Nexus

```
helm repo update
helm install super-mario-helm nexus/super-mario  --version 0.0.1

helm fetch nexus/super-mario --version 0.0.1

https://help.sonatype.com/repomanager3/nexus-repository-administration/formats/helm-repositories