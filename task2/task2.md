# Task 2 - Getting Familiar With Dockerfiles

In this task you write and use your very first Dockerfile.

## 1) Build an image from an existing Dockerfile

**Inspect the Dockerfile in the _pokemon_ subfolder**
- What is each line (one line = one layer) doing?

**Build an image with the given Dockerfile**
Run the following command inside the `docker-demo/task2/pokemon` folder
```
docker build -t pokemon:1.0.0 .
```
- Understand the command itself, the dot `.` is the path to the Dockerfile (which in this case is in the same folder)
- Check the images on your system, can you find the newly created pokemon image with the 1.0.0 tag?
- Run the command again, this time with `-t pokemon:2.0.0`. Why is the build so freaking fast now?