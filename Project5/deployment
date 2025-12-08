#! /bin/bash

docker stop project5
docker rm project5
docker pull larryrsmith/project5:latest
docker run -d --restart always --name project5 -p 8080:80 larryrsmith/project5:latest
