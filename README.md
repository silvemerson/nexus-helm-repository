# Nexus Helm Repository

## Environment

Nome       | vCPUs | Memoria RAM | IP            | S.O.¹           | Script de Provisionamento²
---------- |:-----:|:-----------:|:-------------:|:---------------:| -----------------------------
nexus-server       | 1     | 2048MB      | 172.150.56.10 | devopsbox/ubuntu-20.04 | 
k3s    | 1     | 2048MB       | 172.150.56.30 | devopsbox/ubuntu-20.04 | 

```
git clone https://github.com/silvemerson/nexus-helm-repository.git

cd nexus-helm-repository

vagrant up

```