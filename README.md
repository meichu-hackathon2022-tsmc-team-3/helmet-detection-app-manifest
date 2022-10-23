# Helmet Detection App Manifest

## Requirement

- Helm v3
- K8s cluster

## installation

1. change config in values.yaml

2. setup application db secret and chatbot secret

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
```
apiVersion: v1
kind: Secret
metadata:
  name: chatbot-secret
  namespace: helmetapp
data:
  ROCKET_CHAT_HOST: <CHAT_SERVER_URL>
  BOT_USER: <BOT_USERNAME>
  BOT_PASS: <BOT_PASSWORD>
```



3. apply secret

```
kubectl apply -f <your_db_secret.yaml>
kubectl apply -f <your_bot_secret.yaml>
```

4. install helm application

```
helm install helmet-detection-app .
```

5. check the installation is complete

```
helm list
```
