```


Teams in order to remain consistant in how we deploy application at Devops easylearning I did some researches yesterday and to mimic what others companies are 
doing out there,  to easy the  hassle and stress  of application deployment, we can launch a master deployment container that contain all required packages pertinent to the 
deployment of all our application. 
The benefit of this is :
   1- a single master deployment container will be called for all application 
   2-  this will cut engineering time since we will have only once master deplyment container to mainting
   3- a single Dockerfile will be used as deployment for all application 

to make thing easy on us and to speed the build time and deployment process I have done research and opted for a very light container that will be using 
ubuntu 

here are the instruction need for the image

* the base image tag version should defined by the user at build time ( hint try to set it up with ARG )
* base image ubuntu 
* set the company DEVOPS EASY LEARNING  as the sole owner of the image
* install the following package 
   *  ansible
   *  curl
   *  git
   *  gnupg
   *  jq
   *  linux-headers
   *  openssh-client
   *  postgresql-client
   *  python3
   *  kubectl
   *  kubens
   *  nodejs
   *  npm                        
   *  vim
   *  wget
   * pip
   *  net-tools
   *  iputils-ping
   *  terraform 
   *  awscli
   * default-jre
   * default-jdk
   * maven
   * helm
   * ufw
   * git
   * go
* the default directory should be set to "BUILDER"
* create the following environment variable 
   APP_NAME    # this varibale name should be enter by the user at build time 
   ENV        # this varibale name should be enter by the user at build time 
   TEAM=Devops 
* set the default user to be "root" at this point 
* create a directory called "REPOS"  and under root user home directory
* open port range from "80 to 6000" make sure to excluse "3030 4878 4596 "
* create a directory called GIT under the REPOS  you just create above
* copy  the following repository under a directory called GIT located at "/root/REPOS"
      * https://github.com/devopseasylearning/KFC-app.git
      * https://github.com/devopseasylearning/awesome-compose.git 
      * https://github.com/devopseasylearning/production-deployment.git

* copy directy K8S backend under the default directory 
* create a directory called FRONTEND under the default directory and copy frontend directory inside 
* create a user called  "builder" and make himas the default user
* the first command to run when the container start should be "/bin/bash"
```
