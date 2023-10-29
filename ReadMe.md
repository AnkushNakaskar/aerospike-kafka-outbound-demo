### Aerospike kafka connector
* This project explain Change listener demo like below
* Aerospike changes like , insert, update delete -> kafka
* Pre-requesite for this are : 
  * Need to install zookeeper, kafka, you can refer this : https://github.com/AnkushNakaskar/Apache_Kafka_Understanding/tree/main/installation
* Now we wil focus on Aerospike
  * We need three components mainly listed below.
  * Aerospike DB install
  * Aerospike <> Kafka connector
* Refer to config file and terminal outputs folder
  * Steps to follow
    * First install zookeeper
    * install kafka :
      * create topic name : aerospike, you can refer terminal output for each statement
    * install aerospike <> kafka outbound docker image
    * install aerospike DB
    * install aerospike AQL