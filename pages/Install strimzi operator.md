- > 다양한 방법들이 있는데, 실서비스에 적용할 생각이라면, Strimzi release artifacts 를 다운로드하고 설치하는 걸 추천하는 것 같다.
- Deployment 개요
	- 다음의 순서로 배포가 이루어집니다.
		- Cluster Operator 배포
		- Kafka Cluster 및 ZooKeeper Cluster 배포.
			- Topic Operator 및 User Operator 배포.
		- 필요하다면 다음 항목들을 배포
			- 추가로 필요한 Topic Operator 및 User Operator.
			- Kafka Connect
			- Kafka MirrorMaker
			- Kafka Bridge
			- Metric 모니터링을 위한 추가 components
- 설치 방법
	- [[Using Installation artifacts]]
	- Using OperatorHub.io
	- Using Helm chart
	- {{embed ((6237260a-a226-4f63-b9e1-d9b99270a25e))}}
- 참고
	- 실습을 위한 가장 간단한 방법은 아래 [Quick Starts](https://strimzi.io/quickstarts/)을 이용하는 것이다.
	- ```sh
	  kubectl create namespace kafka
	  kubectl create -f 'https://strimzi.io/install/latest?namespace=kafka' -n kafka
	  kubectl apply -f https://strimzi.io/examples/latest/kafka/kafka-persistent-single.yaml -n kafka 
	  kubectl wait kafka/my-cluster --for=condition=Ready --timeout=300s -n kafka 
	  ```
- Links
	- https://strimzi.io/docs/operators/latest/deploying.html