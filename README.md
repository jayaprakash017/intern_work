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

it will definately throw conflict error because have same name and even have same image id 
To overcome that we have to mention the tag name alog with  image name and check images

	$sudo dokcer rmi ubuntu:lts 	
	
	$sudo docker images
	
REPOSITORY   TAG       IMAGE ID       CREATED      SIZE
ubuntu       latest    ce8f79aecc43   6 days ago   78.1MB
	
	
