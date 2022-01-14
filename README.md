JWT_KEYSTORE_PASSWORD=foobar;DATA_DOG_TAG_ENV=foobar;DATA_DOG_TAG_POD=foobar;DATA_DOG_TAG_IMAGE=foobar;JWT_AUTH=false;REDIS_CONSUMER_USE_TLS=false;REDIS_CONSUMER_LISTS=["devices:messages:quick-diagnostic-report"];REDIS_CONSUMER_NODES=["127.0.0.1:7000", "127.0.0.1:7001", "127.0.0.1:7002"];MONGO_USERNAME=foo;MONGO_PASSWORD=bar;MONGO_ENDPOINT=127.0.0.1:27017;MONGO_DATABASE_NAME=connectedroom;DB_USERNAME=root;DB_PASSWORD=foobar;CONNECTION_URL=jdbc:mysql://127.0.0.1:33060/diagnosticReports;MONGO_SSL_CERTIFICATE=;MONGO_CONNECTION_PARAMS=authSource=admin

brew install redis

docker run --detach --name=mysql-test --env="MYSQL_ROOT_PASSWORD=foobar" --env="MYSQL_ROOT_HOST=%" --publish 33060:3306 dockerhub.hilton.com/hilton/ms-mysql:11

docker run --name "redis-cluster-test" -e "IP=0.0.0.0" -e "SLAVES_PER_MASTER=0" -p 7000-7002:7000-7002 grokzen/redis-cluster:latest

docker run --name "mongo-test" -e MONGO_INITDB_ROOT_USERNAME=foo -e MONGO_INITDB_ROOT_PASSWORD=bar -e MONGO_INITDB_DATABASE=connectedroom -p 27017:27017 -d mongo:4.0.27

http://localhost:9006/events/connectedroom/messages

**quick diagnostic payload**

{
  "header": {
    "name": "quick-diagnostic-report",
    "version": "1",
    "namespace": "com.hilton.diagnostic",
    "timestamp": "2020-12-16T02:52:19Z",
    "from": "MSYOR:1:101:E81863519DDD"
  },
  "payload": [
    {
      "data": {
        "innCode": "MSYOR",
        "location": 0,
        "roomNumber": "1413"
      },
      "name": "Provision Info",
      "isError": 0,
      "timestamp": 1608087137
    },
    {
      "data": {
        "isWiFiConnected": 0,
        "isEthernetConnected": 1
      },
      "name": "Network Status",
      "isError": 0,
      "timestamp": 1608087137
    },
    {
      "data": {
        "isApiReachable": 1,
        "isSocketReachable": 1
      },
      "name": "Mission Control Status",
      "isError": 0,
      "timestamp": 1608087137
    },
    {
      "data": {
        "vendor": "GSM",
        "isConnected": 1,
        "isServiceRunning": 1
      },
      "name": "MPI Status",
      "isError": 0,
      "timestamp": 1608087137
    },
    {
      "data": {
        "currentLevel": "HDCP-2.2",
        "maximumLevel": "HDCP-2.2"
      },
      "name": "HDCP Status",
      "isError": 0,
      "timestamp": 1608087137
    },
    {
      "data": {
        "tvChannelCount": 40,
        "tvProgramCount": 1783
      },
      "name": "Live TV Status",
      "isError": 0,
      "timestamp": 1608087137
    },
    {
      "data": {
        "actualCount": 5,
        "expectedCount": 5
      },
      "name": "Streaming Apps Status",
      "isError": 0,
      "timestamp": 1608087137
    }
  ]
}
**
lineartvDiagnosticReports**


{
  "header": {
    "name": "lineartv-quick-diagnostic-report", or can be "lineartv-extended-diagnostic-report"
    "version": "1",
    "namespace": "com.hilton.diagnostic",
    "timestamp": "2020-12-16T02:52:14Z"
  },
  "payload": [
    {
      "data": {
        "channel": "SHO2",
        "signalLock": {
          "entries": [
            {
              "isError": 0,
              "timestamp": 1608087126,
              "hasSignalLock": 1
            },
            {
              "isError": 0,
              "timestamp": 1608087129,
              "hasSignalLock": 1
            },
            {
              "isError": 0,
              "timestamp": 1608087132,
              "hasSignalLock": 1
            }
          ],
          "errorPercentage": 0
        },
        "signalError": {
          "entries": [
            {
              "isError": 0,
              "timestamp": 1608087126,
              "signalError": 0
            },
            {
              "isError": 0,
              "timestamp": 1608087129,
              "signalError": 0
            },
            {
              "isError": 0,
              "timestamp": 1608087132,
              "signalError": 0
            }
          ],
          "errorPercentage": 0
        },
        "signalLevel": {
          "entries": [
            {
              "isError": 1,
              "timestamp": 1608087126,
              "signalLevel": 38
            },
            {
              "isError": 1,
              "timestamp": 1608087129,
              "signalLevel": 38
            },
            {
              "isError": 1,
              "timestamp": 1608087132,
              "signalLevel": 38
            }
          ],
          "errorPercentage": 100
        },
        "signalQuality": {
          "entries": [
            {
              "isError": 0,
              "timestamp": 1608087126,
              "signalQuality": 91
            },
            {
              "isError": 0,
              "timestamp": 1608087129,
              "signalQuality": 61
            },
            {
              "isError": 0,
              "timestamp": 1608087132,
              "signalQuality": 61
            }
          ],
          "errorPercentage": 0
        },
        "errorPercentage": 25
      },
      "name": "SHO2",
      "isError": 1,
      "timestamp": 1608087134
    }
  ]
}



