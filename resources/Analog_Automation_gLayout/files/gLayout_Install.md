# GLayout DEV Environment Setup 

> 🚧 **Under Construction** 

**Introducing the Tools:**   
GLayout Development Environment is set up in a container  (a sandboxed OS) built from the IIC-OSIC-TOOLS Docker image. This instruction set intends to guide you in installing the required tools to get started with the open-source design.   
You will need two software to install on your machine to set up the environment:

* Docker Desktop: A GUI-based software to manage your containers  
* Git Client: A tool to help pull open-sourced code and scripts from GitHub


Important Terms: **Docker:** The software/tool that runs a sandboxed OS. **Docker Desktop**: The GUI client that manages Docker. **Docker Image**: The image of the frozen OS with pre-installed applications that is provided to Docker. **Docker Container**: The OS that we build from a Docker image and interact with it. Multiple containers can be built from the same image. Know More [here](https://docs.docker.com/)

Thereafter, we will build a container (a sandboxed OS) with many tools you can use to get started with open-source design, including:

* GF180 PDK and SKY130 PDK  
* Magic (Used for Extraction)  
* Netgen (Used for LVS checking)  
* Klayout (Used for Visualisation, and DRC/LVS)  
* Ngspice (Pre- & Post PEX Simulations )  
* Glayout (Analog Design Tool)

**Install Git Client:**  
Installation is platform dependent, See [the steps here](https://github.com/git-guides/install-git)  
(optional) What is Git? Know more [here](https://github.com/git-guides)

Why Git? We will use git to pull (or download) the open-source codes/scripts hosted on GitHub.com. Later, we will use Git again to push (or upload) our design contributions to the open-source repositories.  
	  
**Install Docker Desktop:**   
Docker is cross-platform and installable anywhere. Docker Desktop is the all-in-one package to build images, run containers, and so much more. In this step, we are going to 

* Install the Docker Desktop software   
* Pull the IIC-OSIC-TOOLS Docker image. 

Videos (TBD; following Links are old)  
The following videos will guide you through the process of installing and using Docker Desktop on various platforms.

* Mac: [Mac: Install Open Source Design Tools](https://youtu.be/Cg5tn6dt1Fs)  
  * Ubuntu Linux: [Linux: Install Open Source Design Tools](https://youtu.be/xUYIoLpUuAo)  
    

Instructions up to this stage are common for all. In the following, we will see Glayout-specific steps  
Glayout Specific Steps  
For Glayout, we are going to build the Container with additional steps to forward Port: 888 (alongside VNC or X11) to start a Jupyter Server to execute Glayout Notebooks.    
\*\*Note: Keep an eye on the different containers that are being built for different purposes. They have different names and container IDs. 

* *Step prequel to 7:*  You will need three scripts available here (\!\!):   
  * “start\_XX\_GL.sh/.bat”  

  This builds the image and forwards port  8888 to the host

  * “setup\_GL.sh” (no .bat needed)  
     This installs all necessary Tools in a Python virtual environment   
  * “restart\_jup.sh” (no .bat needed)  
    This restarts the Jupyter server later if the container is closed or rebuild

* *Step 7:*  Now we are going to build the container from the image. The Glayout start-up scripts “start\_XX.sh”(for Linux/Mac) or “start\_XX.bat”(for Windows) use different ways to build the container. 

**Miscellaneous Docker Commands \-** 

1. To remove the container, run the command:   
   1. *(Mac) docker container rm glayoutcontainer*  
   2. *(Linux/WSL) docker rm glayoutcontainer*  
2. To stop a container, run the command:  
   1. *(Mac) docker container stop glayoutcontainer*  
   2. *(Linux/WSL) docker stop glayoutcontainer*  
3. To restart the container, run the command:   
   1. *(Mac) docker container restart glayoutcontainer*  
   2. *(Linux/WSL) docker restart glayoutcontainer*  
4. To execute a running container, first check its status by running   
   1. *(Mac) docker container ls \-a (Linux/WSL) docker ls \-a*  
   2. *docker exec \-it glayoutcontainer bash* (if *glayoutcontainer* is running) (\-it runs the container in interactive mode)   
5. To make a permanent change to Docker:   
   1. *docker container commit \<container ID\>*  
   2. *docker commit \<container ID\>*  
   3. 

***Note: ‘exit’ in a running Docker container halts all running processes and stops. A graceful shutdown can be achieved by using docker stop glayoutcontainer***  

*Installing KLive and PDK Colour Schemes*

1. Run your container using a previously described run command (Step 8 of Install with Docker)  
2. Run KLayout by just typing “klayout” in the Docker container  
3. Install KLive  
   1. Go to Tools \-\> Manage Packages \-\> Install New Packages \-\> Search  
   2. Search for KLive  
   3. Install the package that looks like this:  
      ![][image11]  
4. Once it's installed on your host system. Type in “docker ps \-a”. This will list all of your running containers. Copy the container ID of the most recently started one or the one you installed Klive  
5. Enter the command “docker commit \<container id\> openfasoc:glayout

We acknowledge Kwantae Kim for letting us use some graphics materials from his blog and providing advice. Please check out (for general open-source flow) Kwantae Kim's ['Setting Up Open Source Tools with Docker'](https://kwantaekim.github.io/2024/05/25/OSE-Docker/)\!
