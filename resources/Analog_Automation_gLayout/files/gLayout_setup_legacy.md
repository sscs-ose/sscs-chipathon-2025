
**Legacy:** DEV Environment Setup   
(based on GLayout Docker Image hosted [here](https://github.com/idea-fasoc/OpenFASOC/))

* Introducing the [Tools	1](#heading=h.4ins7t8hyerw)  
* [Install with Docker (Recommended method)	1](#heading=h.cfs5dkl45z9f)  
  * [Videos	1](#heading=h.4nrx24gadq7h)  
  * [Steps](#heading=h.w157p6yst78f)	[3](#heading=h.m4p3k620wxsu)  
* Installing Git and cloning the [OpenFASOC](https://github.com/idea-fasoc/OpenFASOC) repository  
* [Checking your install	4](#heading=h.koqgh2m0p9eb)  
* [Getting started with GLayout	4](#heading=h.g7fp5cujyjr9)

**Introducing the Tools**  
The following steps will install a container (a sand-boxed OS) with many tools you can use to get started with open-source design, including:

* GF180 PDK and SKY130 PDK  
* Magic (Used for Extraction)  
* Netgen (Used for LVS checking)  
* Klayout (Used for Visualisation, and DRC/LVS)  
* Ngspice (Pre- & Post PEX Simulations )  
* Glayout (Analog Design Tool)


**Install with Docker**   
**The easiest way to install the tools is using Docker.**

* Videos  
  The following videos will guide you through the process of installing and using Docker on various platforms.  
  * Mac: [Mac: Install Open Source Design Tools](https://youtu.be/Cg5tn6dt1Fs)  
  * Ubuntu Linux (you will need the Docker install steps for your distro, see links below): [Linux: Install Open Source Design Tools](https://youtu.be/xUYIoLpUuAo)  
* *Steps*  
  Docker is cross-platform and installable anywhere. The installation process for Docker varies based on the platform you are using. Please follow the specific instructions for your platform:  
  * [Install Docker on Mac](https://docs.docker.com/desktop/install/mac-install/)  
  * [Install Docker on Linux](https://docs.docker.com/engine/install/) (select your OS below)  
    * [CentOS](https://docs.docker.com/engine/install/centos/)  
    * [Ubuntu](https://docs.docker.com/engine/install/ubuntu/)  
    * [Fedora](https://docs.docker.com/engine/install/fedora/)  
    * [Debian](https://docs.docker.com/engine/install/debian/)   
    * [Red-Hat](https://docs.docker.com/engine/install/rhel/)

* Install git so that you can get the Docker image  
    
  * Installation is platform dependent, [you can see the steps here](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)  
      
* Once Docker and git are installed, clone the OpenFASOC repository  
1. Navigate to the Docker folder  
   

| git clone [https://github.com/idea-fasoc/OpenFASOC.git](https://github.com/idea-fasoc/OpenFASOC.git) |
| :---- |

   

2. Navigate to the Docker folder  
   

| cd OpenFASOC/docker/conda |
| :---- |

   

3. ***(Mac only)***, Edit “*\~/.docker/config.json*” to remove the line *“credsStore” : “desktop”*  
     
4. Build and run the Docker container  
   

| Linux/WSL |
| :---- |
| (*Building the Docker Image*) sudo docker build \-t openfasoc:glayout . (Navigating back to the main directory) cd ../../ (Starting the Docker Image) sudo docker run \-v $(pwd):$(pwd) \-w $(pwd) \--name glayoutcontainer \-it openfasoc:glayout (Installing packages) pip install \-r requirements.txt (Installing packages) pip install gdstk prettyprint |
| **Mac** |
| sudo docker build \-t openfasoc:glayout . \--platform=”linux/amd64” cd ../../ sudo docker run \-v $(pwd):$(pwd) \-w $(pwd) \--name glayoutcontainer \-it openfasoc:glayout pip install \-r requirements.txt pip install gdstk prettyprint |

   

   

   

   

   

***For running graphical applications (such as KLayout) in the Docker container***

5. Port graphical applications in Docker (so you can run KLayout inside the Docker container)  
   * Mac  
     * Visit [https://www.xquartz.org/](https://www.xquartz.org/) and download the “Quick Download” file  
     * Once the package is installed, run the installer  
     * Reboot your computer after XQuartz is installed  
     * Launch the XQuartz application  
       * Type in “xhost \+ 127.0.0.1”

       ![][image9]

     * Go to XQuartz preferences \> Security and check these options  
       ​​![][image10]  
     * Open the Docker application or use the docker start command in the terminal and start the container, and copy the container ID

     ![][image12]

     

   * Linux/WSL  
     * Open a terminal and run “xhost \+Local:\*”  
         
         
         
6. Open the Docker Container (the following commands create a new container from the image).   
   *Note: If you already have a Docker container running, don’t make a new one.*  
   

| Linux |
| :---- |
| sudo docker run \-v $(pwd):$(pwd) \-w $(pwd) \-e DISPLAY \-v /temp/.X11-unix:/tmp/.X11-unix \--net=host \-it \--name glayoutcontainer openfasoc:glayout |
| **WSL** |
| docker run \-it \-v /tmp/.X11-unix:/tmp/.X11-unix \-v /mnt/wslg:/mnt/wslg \-v $(pwd):$(pwd) \-w $(pwd)  \-e DISPLAY \-e WAYLAND\_DISPLAY \-e XDG\_RUNTIME\_DIR \-e PULSE\_SERVER \--name glayoutcontainer openfasoc:glayout |
| **Mac** |
| open \-a xquartz sudo docker run \--env=DISPLAY=host.docker.internal:0 \-v $(pwd):$(pwd) \-w $(pwd) \-it \--name glayoutcontainer openfasoc:glayout |

**Miscellaneous Docker Commands \-** 

6. To remove the container, run the command:   
   1. *(Mac) docker container rm glayoutcontainer*  
   2. *(Linux/WSL) docker rm glayoutcontainer*  
7. To stop a container, run the command:  
   1. *(Mac) docker container stop glayoutcontainer*  
   2. *(Linux/WSL) docker stop glayoutcontainer*  
8. To restart the container, run the command:   
   1. *(Mac) docker container restart glayoutcontainer*  
   2. *(Linux/WSL) docker restart glayoutcontainer*  
9. To execute a running container, first check its status by running   
   1. *(Mac) docker container ls \-a (Linux/WSL) docker ls \-a*  
   2. *docker exec \-it glayoutcontainer bash* (if *glayoutcontainer* is running) (\-it runs the container in interactive mode)   
10. To make a permanent change to Docker:   
    1. *docker container commit \<container ID\>*  
    2. *docker commit \<container ID\>*  
    3. 

***Note: ‘exit’ in a running Docker container halts all running processes and stops. A graceful shutdown can be achieved by using docker stop glayoutcontainer***    
*Checking your install*  
Once the install is complete, you can check your install by running the following command

| Check Install |
| :---- |
| \# assuming you are in the OpenFASOC directory *cd openfasoc/generators/glayout python3 test\_glayout.py* |

This script will test if: 

1. The Python version meets requirements (3.10 or newer)  
2. The conda packages have been installed  
3. The PDKs sky130 or GF180 have been installed and are in their expected locations  
4. Python packages have been properly installed  
5. glayout is working as required. The script:  
   1. places an nmos component   
   2. runs a Layout vs. Schematic check on it  
      

*Installing KLive*

6. Run your container using a previously described run command (Step 8 of Install with Docker)  
7. Run KLayout by just typing “klayout” in the Docker container  
8. Install KLive  
   1. Go to Tools \-\> Manage Packages \-\> Install New Packages \-\> Search  
   2. Search for KLive  
   3. Install the package that looks like this:  
      ![][image11]  
9. Once it's installed on your host system. Type in “docker ps \-a”. This will list all of your running containers. Copy the container ID of the most recently started one or the one you installed Klive  
10. Enter the command “docker commit \<container id\> openfasoc:glayout  
      
      
      
      
      
      
    

***Common Issues***

1. “Conflict. The container name ‘/glayoutcontainer’ is already in use by container…”?  
     
   Remove the container with docker rm \<container id\> or start the container again with docker start \<container id\>. It is up to you to decide whether to reuse or remove and run a container. Going with the latter will give you the option to mount folders in your host system.  
     
2. WSL:  
   Error: cannot connect to Docker daemon at unix:///var/run/docker.sock …   
   1. Select one after running this command:  
      sudo update-alternatives –config iptables  
   2. Start the Docker daemon  
      sudo service docker start  
   3. Check the status of the Docker daemon  
      sudo service docker status  
        
3. Info: Could not load the Qt platform plugin "xcb" in "" even though it was found.  
   Fatal: This application failed to start because no Qt platform plugin could be initialized. Reinstalling the application may fix this problem.  
     
   MacOS: Make sure you follow all of the steps within Step 7 and 8 in this document. When you run the container make sure it has the argument \--env=DISPLAY=host.docker.internal:0  
     
   All other systems: Make sure you run the corresponding run command provided in step 8 of this document with the relevant command line arguments.  
     
4. Getting a bunch of E: Unable to locate package errors within your container?  
   1. First reboot your computer.  
   2. Reinstall the Docker engine on [Linux](https://docs.docker.com/engine/install/) or [Mac](https://docs.docker.com/desktop/install/mac-install/)  
   3. Run these commands:  
      docker stop $(sudo docker ps \-aq)  
      docker container prune  
      docker image prune  
      sudo docker builder prune-- all  
   4. Restart the building process  
        
      

**Next: Coding with GLayout:** 

Recommended Method: Through VS Code with Docker Plugin

**\<TBD\>**

Now that the tools are installed, please go through the doc to start coding with GLayout and contributing:  
[Contributing and Coding Documentation](https://docs.google.com/document/d/e/2PACX-1vQduXvAvLcvnUl_nkruGJeud9f8mEEf7Z2Pyn9ruxjQrNC_s406X3afV-gwsXWyS-dWH_KgLFieesrP/pub)



[image11]: <data:image/png;base64,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>

[image12]: <data:image/png;base64,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>