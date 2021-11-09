# docker-demo 🔥
<p align="center">
  <img width="264" src="https://user-images.githubusercontent.com/8364783/140619846-e4733d97-7479-4eb4-8b12-dec8b7f0fce0.png">
</p>


## Pre-Workshop Preparations
### Variant 1 - Using Docker Desktop on Windows and Windows Subsystem for Linux (WSL)
**1) Install WSL**  
Run a Windows Powershell as administrator (right click).  
Type  
```
wsl --install
```
This will take some time. Restart your computer. A WSL windows will open and install Ubuntu. This will take some time. Restart. WSL is now installed.  

**2) Install Docker Desktop**  
Go to https://docs.docker.com/desktop/windows/install/ and hit _Docker Desktop for Windows_. Run the executable. Follow the install process.  
Once installed, open Docker Desktop. Go to Settings -> Resources -> WSL Integration -> Hit the Ubuntu slider.  
Open the _Ubuntu_ app. **Test the installation** by running  
```
docker run hello-world
```
Read the output.  

### Variant 2 - Using an Ubuntu VM running on Virtualbox
**1) Set up your VM**  
You will need a Linux OS System (Ubuntu 20.04 *highly* recommended!) running either natively (😎) or on a Virtual Machine (e.g. using https://www.virtualbox.org/).  
To setup a VM, watch: https://www.youtube.com/watch?v=x5MhydijWmc

**2) Install docker** the fast way 🚀
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

**Install development tools (only for Ubuntu VM - use your preferred tools on Windows WSL, like VIM :-) )**
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
