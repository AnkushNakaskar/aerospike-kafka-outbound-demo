### Aerospike kafka connector
* This project explain Change listener demo like below
* Aerospike changes like , insert, update, delete -> kafka
* Pre-requesite for this are : 
  * Need to install zookeeper, kafka, you can refer this : 
    * https://github.com/AnkushNakaskar/Apache_Kafka_Understanding/tree/main/installation
* Now we will focus on Aerospike
  * We need three components mainly listed below.
  * Aerospike DB install
  * Aerospike <> Kafka connector
* Refer to config file and terminal outputs folder
  * Steps to follow
    * First install zookeeper
      * ``` 
        brew install zookeeper
    * install kafka :
      * ```
        brew install kafka
      
      * create topic name : aerospike, you can refer terminal output for each statement
    * install aerospike <> kafka outbound docker image
      * ```
         docker run -p 8080:8080 -v /var/tmp/aerospike/kafka-connect/aerospike-kafka-outbound.yml:/etc/aerospike-kafka-outbound/aerospike-kafka-outbound.yml aerospike/aerospike-kafka-outbound:5.1.2  
    * install aerospike DB
      * ```
        docker run --name aerospike  -v /var/tmp/aerospike/etc/:/opt/aerospike/etc/  -p 3000-3002:3000-3002 aerospike/aerospike-server-enterprise --config-file /opt/aerospike/etc/aerospike.conf
        ```
    * install aerospike AQL
      * ``` 
        docker run -it aerospike/aerospike-tools aql -h  $(docker inspect -f '{{.NetworkSettings.IPAddress}}' aerospike)

#### Example like below :  
  * if you try to insert like below :
  * ``` 
    aql> insert into test.demo (PK, tval) values (123, 'test-value-ankush-first') 
    ```
    * Output in kafka topic is like below :
    * ``` 
       {"metadata":{"namespace":"test","set":"demo","userKey":123,"digest":"WVp7Y+sYXb69hCVTpEgCsaMOwVk=","msg":"write","gen":1,"lut":1698586936461,"exp":1701178936},"tval":"test-value-ankush-first"}  
      ```