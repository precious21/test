JWT_KEYSTORE_PASSWORD=foobar;DATA_DOG_TAG_ENV=foobar;DATA_DOG_TAG_POD=foobar;DATA_DOG_TAG_IMAGE=foobar;JWT_AUTH=false;REDIS_CONSUMER_USE_TLS=false;REDIS_CONSUMER_LISTS=["devices:messages:quick-diagnostic-report"];REDIS_CONSUMER_NODES=["127.0.0.1:7000", "127.0.0.1:7001", "127.0.0.1:7002"];MONGO_USERNAME=foo;MONGO_PASSWORD=bar;MONGO_ENDPOINT=127.0.0.1:27017;MONGO_DATABASE_NAME=connectedroom;DB_USERNAME=root;DB_PASSWORD=foobar;CONNECTION_URL=jdbc:mysql://127.0.0.1:33060/diagnosticReports;MONGO_SSL_CERTIFICATE=;MONGO_CONNECTION_PARAMS=authSource=admin

brew install redis

docker run --detach --name=mysql-test --env="MYSQL_ROOT_PASSWORD=foobar" --env="MYSQL_ROOT_HOST=%" --publish 33060:3306 dockerhub.hilton.com/hilton/ms-mysql:11

docker run --name "redis-cluster-test" -e "IP=0.0.0.0" -e "SLAVES_PER_MASTER=0" -p 7000-7002:7000-7002 grokzen/redis-cluster:latest

docker run --name "mongo-test" -e MONGO_INITDB_ROOT_USERNAME=foo -e MONGO_INITDB_ROOT_PASSWORD=bar -e MONGO_INITDB_DATABASE=connectedroom -p 27017:27017 -d mongo:4.0.27


