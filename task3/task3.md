# Task 3

This task shows a more realistic, very lean Dockerfile. We observe some best practices and use this iamge / container.


**Inspect the Dockerfile (discussion, what is it doing, wee see some best practices)**

**Build an image using the Dockerfile**
- tag it go-demo:1.0.0 (hint: -t)
<details>
  <summary>Solution</summary>

```
$ docker build -t go-demo:1.0.0 .
```
</details>

**Check the size of the image in MB**
- compare it to a standard ubuntu image in size (e.g. `docker pull ubuntu` ;) )

**Run a container based on this image**

When starting...  
- inject environment variables REDIS_PW and REDIS_BASE_URL with any values (hint: -e)
- forward port 8000 on the docker host to port 8080 inside the container

<details>
  <summary>Solution</summary>

```
$ docker run -p 8000:8080 -e REDIS_PW=123 -e REDIS_BASE_URL=42 go-demo:1.0.0
```
</details>

**Now that the application is running, make a curl request on port 8000**
Invoke the `/liveness` and `readyness` endpoints.
<details>
  <summary>Solution</summary>

```
$ curl localhost:8000/liveness
```
```
$ curl localhost:8000/readyness
```
</details>

**Enter the running container with an interactive shell.**
- look around
- what can you find?