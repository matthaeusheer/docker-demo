
1) Local registry
```
docker run -d -p 5000:5000 registry
```
```
docker build -t localhost:5000/java-demo:1.0.0 .
```
```
docker push localhost:5000/java-demo:1.0.0
```
```
docker rmi localhost:5000/java-demo:1.0.0
```
```
docker pull localhost:5000/java-demo:1.0.0
```

2) Docker Hub registry
log in and push pull...