# Helmet Detection App Manifest

## Requirement

- Helm v3
- K8s cluster

## installation

1. change config in values.yaml

2. setup application db secret

```
apiVersion: v1
kind: Secret
metadata:
  name: api-mongo-secret
  namespace: <YOUR_HELMET_DETECTION_APP_NAMESPACE>
  labels:
    app: mongo
data:
  MONGO_HOST: <MONGO_HOST_URL>
  MONGO_USER: <MONGO_USER>
  MONGO_PASS: <MONGO_PASSWORD>
```

3. apply db secret

```
kubectl apply -f <your_secret.yaml>
```

4. install helm application

```
helm install helmet-detection-app .
```

5. check the installation is complete

```
helm list
```
