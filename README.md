# fluentd-kafka-to-splunk

Here are steps to run the Kafka, splunk and fluent servers.

1. Create a ec2 instance 
2. RUN docker image to host the kafka server on the ec2-machine.
        docker-compose up -f fluentd-kafka-to-splunk\Image\Kafka\Image\docker-compose.yaml -d
3. RUN docker image to host the Splunk and fluentd server on the ec2-machine. Port 8000 is exposed on this server.
        docker-compose up -f fluentd-kafka-to-splunk\Image\docker-compose.yaml -d
		Splunk server will be accessible after image creating.
		- https://<server>:8000

Once, all server are up and running. Push the logs into Kafka Producer and fluentd will pull the log from the broker which is added in the configuration file.

Before pushing a logs in the kafka server. Please create a topic and partitions.
Access the kafka image wth command docker exec -ti --user root <container_id> bash

Once you enter . Create a topic with the help below command 
kafka-topics --create --topic fluentd-poc --bootstrap-server localhost:39092

Push the logs and make sure to use the json data for this demo like {"data": 1,"purpose":"testing"}
kafka-console-producer --topic fluentd-poc --bootstrap-server localhost:39092
		
		