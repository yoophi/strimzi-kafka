- id:: 6237260a-a226-4f63-b9e1-d9b99270a25e
  ```sh
  helm repo add strimzi https://strimzi.io/charts/
  helm install strimzi/strimzi-kafka-operator
  ```
- 비고
	- 아래 명령을 수행해보았을 때, Quick Starts 의 manifests 를 실행했을 때 설치되는 CRD 들이 설치되지 않는 것 같다.
	- Helm
		- ```
		  $ helm template strimzi strimzi/strimzi-kafka-operator | yq '[.kind, .metadata.name] | join(".")'
		  
		  == output ==
		  ServiceAccount.strimzi-cluster-operator
		  ---
		  ConfigMap.strimzi-cluster-operator
		  ---
		  ClusterRole.strimzi-cluster-operator-namespaced
		  ---
		  ClusterRole.strimzi-cluster-operator-global
		  ---
		  ClusterRole.strimzi-kafka-broker
		  ---
		  ClusterRole.strimzi-entity-operator
		  ---
		  ClusterRole.strimzi-kafka-client
		  ---
		  ClusterRoleBinding.strimzi-cluster-operator
		  ---
		  ClusterRoleBinding.strimzi-cluster-operator-kafka-broker-delegation
		  ---
		  ClusterRoleBinding.strimzi-cluster-operator-kafka-client-delegation
		  ---
		  RoleBinding.strimzi-cluster-operator
		  ---
		  RoleBinding.strimzi-cluster-operator-entity-operator-delegation
		  ---
		  Deployment.strimzi-cluster-operator
		  ```
	- Quick Starts charts
		- ```sh
		  $ http 'https://strimzi.io/install/latest?namespace=kafka'  | yq '[.kind, .metadata.name] | join(".")'
		  
		  == output ==
		  RoleBinding.strimzi-cluster-operator-entity-operator-delegation
		  ---
		  CustomResourceDefinition.strimzipodsets.core.strimzi.io
		  ---
		  ClusterRole.strimzi-kafka-client
		  ---
		  CustomResourceDefinition.kafkausers.kafka.strimzi.io
		  ---
		  ClusterRoleBinding.strimzi-cluster-operator-kafka-broker-delegation
		  ---
		  ConfigMap.strimzi-cluster-operator
		  ---
		  CustomResourceDefinition.kafkas.kafka.strimzi.io
		  ---
		  ClusterRole.strimzi-cluster-operator-namespaced
		  ---
		  CustomResourceDefinition.kafkatopics.kafka.strimzi.io
		  ---
		  CustomResourceDefinition.kafkaconnects.kafka.strimzi.io
		  ---
		  CustomResourceDefinition.kafkabridges.kafka.strimzi.io
		  ---
		  CustomResourceDefinition.kafkaconnectors.kafka.strimzi.io
		  ---
		  ClusterRole.strimzi-entity-operator
		  ---
		  ClusterRole.strimzi-cluster-operator-global
		  ---
		  ClusterRoleBinding.strimzi-cluster-operator-kafka-client-delegation
		  ---
		  CustomResourceDefinition.kafkamirrormakers.kafka.strimzi.io
		  ---
		  ClusterRole.strimzi-kafka-broker
		  ---
		  CustomResourceDefinition.kafkamirrormaker2s.kafka.strimzi.io
		  ---
		  CustomResourceDefinition.kafkarebalances.kafka.strimzi.io
		  ---
		  ServiceAccount.strimzi-cluster-operator
		  ---
		  Deployment.strimzi-cluster-operator
		  ---
		  ClusterRoleBinding.strimzi-cluster-operator
		  ---
		  RoleBinding.strimzi-cluster-operator
		  ```