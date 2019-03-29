

# What is Vault?

Secure, store and tightly control access to tokens, passwords, certificates, encryption keys for protecting secrets and other sensitive data using a UI, CLI, or HTTP API.

## Installation

1. First you will need kubernetes cluster. You can create one on GCP under 5mins. Once it`s ready ssh to that cluster.

2. To start installation follow these steps:

```python
yum install git -y
git clone git@github.com:kolomyya/k8-jira-nexus.git
cd k8-jira-nexus
```

3. You need to encrypt your token(password) first before you add it to the vault-secret.yaml file.
To do that follow these steps(It`s just an example):

```python
echo -n 'admin' | base64
YWRtaW4=
echo -n '1f2d1e2e67df' | base64
MWYyZDFlMmU2N2Rm
```

4. Create secret and deployment by running these commands:

```python
kubectl create -f vault-secret.yaml
kubectl create -f vault-deployment.yaml
```
5. Once the installation is completed please run these command to check if everything was created or no:

```python
kubectl get sectets -n tools
kubectl get pods -n tools
kubectl get pvc -n tools
kubectl get pv -n tools
kubectl get deployment -n tools
```
6. Once it`s done, get the External IP for the Vault Service by running this command:

```python
kubectl get service -n tools
```

7. Paste the External IP on your browser. It should load Vault initial webpage where you are going to add the "token" and access your website. The token is the whatever you have specified in the vault-secret.yaml 
Once you enter the token you will access to the website where you can manage the rest stuff.

8. To decode your encrypted token run this command:

```python
echo 'MWYyZDFlMmU2N2Rm' | base64 --decode
```

and you will get this outcome:

```python
1f2d1e2e67df
```

