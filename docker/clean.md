# Cleaning

## Remove untagged docker images
docker rmi $(docker images |grep \<none\> |awk '{print $3}')<F37>

## Remove all exited containers
docker rm -fv $(docker ps -qa)
