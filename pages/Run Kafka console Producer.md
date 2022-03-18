- ```
  kubectl -n kafka run kafka-producer -ti \
    --image=quay.io/strimzi/kafka:0.28.0-kafka-3.1.0 \
    --rm=true --restart=Never \
    -- bin/kafka-console-producer.sh \
       --broker-list my-cluster-kafka-bootstrap:9092 \
       --topic my-topic
  
  ```
-
