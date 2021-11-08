# docker-demo 🔥
![image](https://user-images.githubusercontent.com/8364783/140619846-e4733d97-7479-4eb4-8b12-dec8b7f0fce0.png)


## 1. Pre-Workshop Preparations
### 1.1 Setup your Linux System
You will need a Linux OS System (Ubuntu 20.04 *highly* recommended!) running either natively (😎) or on a Virtual Machine (e.g. using https://www.virtualbox.org/).  
To setup a VM, watch: https://www.youtube.com/watch?v=x5MhydijWmc

### 1.2 Install Docker
**Install docker** the fast way 🚀
```
sudo apt install curl
```
```
curl -fsSL https://get.docker.com -o get-docker.sh
sh get-docker.sh
```
This convenience script detects your distribution and installs docker and required dependencies (needs sudo access). It should have created a `docker` group already, so you just have to add your own user to it to be able to run `docker` commands without `sudo`
```
sudo usermod -aG docker $USER
```
Restart your system for the changes to take effect.  

**Test the installation** by running
```
docker run hello-world
```
and reading the output prompt.  
To enable docker auto-completion in the shell (like a boss 🤓), run
```
sudo curl \
    -L https://raw.githubusercontent.com/docker/compose/1.29.2/contrib/completion/bash/docker-compose \
    -o /etc/bash_completion.d/docker-compose
```

If you run into issues, see official documentation at https://docs.docker.com/engine/install/ubuntu/.

### 1.3 Install development tools
1) Since we need to clone this repo for the workshop, we need to have git installed
```
sudo apt install git
```
2) Download the docker-demo repo
```
git clone https://github.com/matthaeusheer/docker-demo.git
```
3) We are comfortable with IntelliJ, so let's install this one as well
- Go to https://www.jetbrains.com/de-de/idea/download/#section=linux and download the community edition
- Extract the file with `tar -xf <intellij_downloaded_file>`
- Run `<path_to_extracted_folder>/bin/idea.sh`
- Choose "add desktop entry" in the little settings icon to be able to start IDEA as a normal application outside the command line
