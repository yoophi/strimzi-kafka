- ```
  kubectl -n kafka run kafka-consumer -ti \
    --image=quay.io/strimzi/kafka:0.28.0-kafka-3.1.0 \
    --rm=true --restart=Never \
    -- bin/kafka-console-consumer.sh \
      --bootstrap-server my-cluster-kafka-bootstrap:9092 \
      --topic my-topic \
      --from-beginning
  
  ```
