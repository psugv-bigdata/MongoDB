### MongoDB

This guide has two parts: start a mongodb container from docker hub and build a mongodb images locally.

Mongodb will be running on port 27017 inside the docker container and the host port to access it is 21117.

The MongoDB data directory will be /data/db.


##Using Docker Hub:

This is recommended as it's easy and portable.

1.Ensure that docker is installed on your host machine.

2.Pull the mongodb image from the docker hub by runing:

      sudo docker pull psugvbigdata/mongo-base
3.To run the mongodb image, run the following command:

      docker run -d -p 21117:27017 psugvbigdata/mongo-base /usr/bin/mongod --replSet "rs0"

This command will name the container as mongo and port the inner port(27017) to outside at 21117. 

4.You can try to connect to mongodb by:

      mongo --port 21117
      
5.If you want to mount host volumn in the contarin, add "-v" after "-d" in the step 3.

##Build the mongo image locally:

1.Ensure that docker is installed on your host machine.

2.Download the Dockerfile to your working directory, usually it would be /home.

3.Build the images by runing:

      sudo docker build -t psugvbigdata/mongo-base .
      
4.Never forget the "." in the end of last command. It stands for the default dockerfile name, "Dockerfile".

5.Follow the step 3 to step 5 in Using Docker Hub.
