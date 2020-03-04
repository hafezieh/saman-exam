# saman-exam

in this project i want to create a set of **3 CentOS Linux containers** with **updated YUM repo** , a **build tool** and **Python 3** .
i choose **'buildit'** that is a  simple build tool for small projects.
for buildit installation , at first we should install **'pip'**

# dockerfile configuration:
for this dockerfile i used **centos:7** as a base image
these are our main steps to write dockerfile

1. yum update & python installation
2. install pip for build tool installation
3. install build tool (buildit)

and i exposed port:8090 for my service
___
**note:** we can use -p [port-number] during docker run instead of EXPOSE

after that we sould put this docker file to 3 diffrent directory that i used **dir1**, **dir2** and **dir3** for that (the name of directories)
we can test our docker file by this command:

`docker build --rm -t [optional-name]/python:centos7 .`

# docker-compose configuration
at the next step we write our docker-compose file to bring our services at the same time 
i named my docker-compose file , **'local.yaml'**
i consider 3 isolate services with 3 defined network for that 
my services are : **os1**, **os2**, and **os3**
and i maped 8080 to the port 8090 for os1 , 8085 to the port 8090 for os1 , 8090 to the port 8090 for os1

for more details see the 'local.yaml' file
___
**note:** after running docker-compose file with command bellow our container will be exited so i used **"tty: true"** and **"stdin_open: true"**
to prevent it . 

this option do what **"-i"** and **"-t"** do in **"docker run -it [container-name] /bin/ bash"** , for **in foreground mode** and **intractive mode**

use this command to bring services up :

`docker-compose -f local.yaml up -d`
