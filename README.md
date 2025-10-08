# intern_work
7TH-OCT-2025

DEALING WITH TAGS 

1.pull a ubuntu image & to check the images that we created 

 	$sudo docker pull ubuntu 
	
	$sudo docker images
 

 REPOSITORY   TAG       IMAGE ID       CREATED      SIZE
ubuntu       latest    ce8f79aecc43   6 days ago   78.1MB

by default it will create a tag with the name of 'latest'
if you want do it manually then you canuse this commnd & check 

  $sudo docker tag ubuntu ubuntu:lts
  
  $sudo docker images 


REPOSITORY   TAG       IMAGE ID       CREATED      SIZE
ubuntu       latest    ce8f79aecc43   6 days ago   78.1MB
ubuntu       lts       ce8f79aecc43   6 days ago   78.1MB

Now if you want to delete the image we can use this command 

	$sudo docker rmi image ubuntu 

it will definately throw conflict error because have same name and even have same image id like these

Error response from daemon: conflict: unable to delete ce8f79aecc43 (must be forced) - image is referenced in multiple repositories

To overcome that we have to mention the tag name alog with  image name and check images

	$sudo dokcer rmi ubuntu:lts
	
	$sudo docker images
	
REPOSITORY   TAG       IMAGE ID       CREATED      SIZE
ubuntu       latest    ce8f79aecc43   6 days ago   78.1MB

------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
volume persistance

First udate the system

$sudo apt update  && sudo upgrade

pull the mongo image

$sudo docker pull mongo

Using default tag: latest
latest: Pulling from library/mongo
a1a21c96bc16: Already exists 
8481a729031f: Pull complete 
d183ce926b04: Pull complete 
5dac1b57d544: Pull complete 
09d333d29f76: Pull complete 
1f1cbb33527b: Pull complete 
0ef8bb939786: Pull complete 
43ec45d81e04: Pull complete 
Digest: sha256:ea783d8ac4dcac9f8a7ff236b26a52e36649fc1bdd1778ffb44ba5e4de776cda
Status: Downloaded newer image for mongo:latest
docker.io/library/mongo:latest

checking images

$sudo docker images
REPOSITORY   TAG       IMAGE ID       CREATED       SIZE
mongo        latest    e4ec68a273dd   5 days ago    916MB

create a volume & check

$sudo docker create volume  mongo_vol
$sudo docker volume ls

attach volume to mongo image which we created earlier 

$sudo docker run -it --name mongo_cont1 -p 21017:27017 -v mongo_vol:/data ubuntu /bin/bash

after that you are in the mongo_cont1 then insert the data for that

$cd data

there i create a file with 'mongodb_bakup' in that insert some data

$touch mongodb_backup
$cat >> mongodb_backup

Now stop the container and remove the container & list all containers

$sudo docker stop container-id
$sudo docker rm container-id
$sudo ps -a

now check the volume previously we attcjed to the mongo image
$sudo docker volume ls 

Now create another container by using mongo image and attach the mongo_vol too

$sudo docker run -it --name mongo_cont2 -p 21017:27017 -v mongo_vol:/data ubuntu /bin/bash

now check the data 

$cd data

there we can see that 'mongodb_bakup' file which we created.







 

