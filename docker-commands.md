docker network create mongo-network 

docker run -p 8081:8081 -d \
-e ME_CONFIG_MONGODB_ADMINUSERNAME=admin \
-e ME_CONFIG_MONGODB_ADMINPASSWORD=password \
-e ME_CONFIG_MONGODB_SERVER=mongodb \
--name mongo-express \
--net mongo-network \
mongo-express

docker run -p 27017:27017 -d \
-e MONGO_INITDB_ROOT_USERNAME=admin \
-e MONGO_INITDB_ROOT_PASSWORD=password \
--name mongodb \
--net mongo-network \
mongo

docker-compose -f docker-compose.yaml up
docker-compose -f docker-compose.yaml down

docker build -t my-app:1.0 .

#env

aws ecr get-login-password --region us-east-1 | docker login --username AWS --password-stdin 044545860366.dkr.ecr.us-east-1.amazonaws.com

docker build -t my-app:1.3 .

docker tag my-app:1.3 044545860366.dkr.ecr.us-east-1.amazonaws.com/my-app:1.3

docker push 044545860366.dkr.ecr.us-east-1.amazonaws.com/my-app:1.3

docker-compose -f docker-compose.yaml up
