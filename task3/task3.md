# Task 3 - Getting Familiar With Dockerfiles, Building Images, Starting Containers

In this task you will learn how to build and run images using a Dockerfile.

## 1) Build an image from an existing Dockerfile
**Inspect the Dockerfile in the _pokemon_ subfolder**
- What is each line (one line = one layer) doing?

**Scan through the codebase**
- It is a simple Spring Boot application and exposes a /pokemon/random endpoint which returns a JSON object describing a random pokemon.

**Build an image with the given Dockerfile**
Run the following command inside the `docker-demo/task2/pokemon` folder
```
docker build -t pokemon:1.0.0 .
```
- Understand the command itself, the dot `.` is the path to the Dockerfile (which in this case is in the same folder)
- Check the images on your system, can you find the newly created pokemon image with the 1.0.0 tag?
- Run the command again, this time with `-t pokemon:2.0.0`. Why is the build so freaking fast now? Hint search for " ---> Using cache" in the output.

## 2) Run a new container given the freshly built image
**Run an instance of the `pokemon:1.0.0` image.**
- Think about how you would do that, then use the following:
    <details>
      <summary>command</summary>
    
    ```
    $ docker run pokemon:1.0.0
    ```
    </details>
**Try to query the endpoint using curl:**  
- Use this command but you should really know it yourself ;)  
    <details>
    <summary>curl command</summary>
    
    ```
    $ curl localhost:8000/pokemon/random
    ```
    </details>
- The connection is being refused. What have we forgot?
- Stop the container (docker stop) and delete (docker rm) it.
- Run a new instance of the same container but now expose the ports correctly
    <details>
    <summary>command</summary>

    ```
    $ docker run -p 8000:8000 pokemon:1.0.0
    ```
    note that you could also run the container in detached mode with
    ```
    $ docker run -d -p 8000:8000 pokemon:1.0.0
    ```
    </details>