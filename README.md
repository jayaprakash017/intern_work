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

	$sudo docker rmi  ubuntu 

it will definately throw conflict error because have same name and even have same image id like these

Error response from daemon: conflict: unable to delete ce8f79aecc43 (must be forced) - image is referenced in multiple repositories

To overcome that we have to mention the tag name alog with  image name and check images

	$sudo dokcer rmi ubuntu:lts
	
	$sudo docker images
	
REPOSITORY   TAG       IMAGE ID       CREATED      SIZE
ubuntu       latest    ce8f79aecc43   6 days ago   78.1MB

------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
volume persistance

VOLUME_PERSISTENCE WITH POSTGRES_DB

AIM-The main aim of these task is whenever we delete a container the data inside the container will also deleted to overcome that we can use volume 

To know that follow the following steps :

Create a volume 

 $docker volume create pgdata_volume


Pull an image of postgres (optional)

$docker pull postgres


#So it will pull the postgres image from public dockerhub 

Create a container and attach volume that we created earlier with docker run command 

$docker  run -it --name postgresdb_container1 -e POSTGRES_USER=jaya -e POSTGRES_PASSWORD=keypass -e POSTGRES_DB=jaya_postgress_db -v postgres_volume:/var/lib/postgresql/data -p 5432:55432 postgres




#--name :it helps to create container with specific name 
#-e POSTGRES-USER=jaya :used to creat a database user to database
#-e POSTGRES_PASSWORD :set password to the database
#-e POSTGRES_DB :set database name
#-v postgres_volume:/var/lib/postgresql/data : set a path b/w volume to postgres default path
Postgres database and these is /var/lib/postgresql/data default postgres database path
#Postgres :image 

To attach to the database and insert the data 

$docker exec -it db_container1 psql -U jaya -d jaya_postgress_db 


After that insert the data into the database by using postgres query  after to quit from database use /q

Next stop & remove the container 

$docker stop db_container1
$docker rm db_container1


Now run a new container by attaching the same volume and check for the data

$docker  run -it --name db_container2 -e POSTGRES_USER=jaya -e POSTGRES_PASSWORD=passkey -e POSTGRES_DB=jaya_postgress_db -v postgres_volume:/var/lib/postgresql/data -p 5432:55432 postgres



To attach to the database and check the data 
$docker exec -it db_container2 psql -U jaya -d jaya_postgress_db 





























