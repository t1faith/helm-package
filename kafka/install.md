# 参考文档
https://artifacthub.io/packages/helm/bitnami/kafka

# 要求
- Kubernetes 1.19+
- Helm 3.2.0+
- PV provisioner support in the underlying infrastructure

# 添加仓库
```
helm repo add bitnami https://charts.bitnami.com/bitnami
```

# 安装
```
helm install my-release bitnami/kafka
```

# 卸载
```
helm delete my-release
```

# 指定参数安装
```
# Specify each parameter using the --set key=value[,key=value] argument to helm install. For example:
helm install my-release \
  --set replicaCount=3 \
  bitnami/kafka
```

# 指定values.yaml文件安装
```
helm install my-release -f values.yaml bitnami/kafka
```

# example
```
➜  helm-package git:(main) ✗ helm install kafka \
  --set replicaCount=3 \
  -n=hermes-chaos \
  bitnami/kafka
NAME: kafka
LAST DEPLOYED: Wed Jul 13 16:13:20 2022
NAMESPACE: hermes-chaos
STATUS: deployed
REVISION: 1
TEST SUITE: None
NOTES:
CHART NAME: kafka
CHART VERSION: 18.0.3
APP VERSION: 3.2.0

** Please be patient while the chart is being deployed **

Kafka can be accessed by consumers via port 9092 on the following DNS name from within your cluster:

    kafka.hermes-chaos.svc.cluster.local

Each Kafka broker can be accessed by producers via port 9092 on the following DNS name(s) from within your cluster:

    kafka-0.kafka-headless.hermes-chaos.svc.cluster.local:9092
    kafka-1.kafka-headless.hermes-chaos.svc.cluster.local:9092
    kafka-2.kafka-headless.hermes-chaos.svc.cluster.local:9092

To create a pod that you can use as a Kafka client run the following commands:

    kubectl run kafka-client --restart='Never' --image docker.io/bitnami/kafka:3.2.0-debian-11-r12 --namespace hermes-chaos --command -- sleep infinity
    kubectl exec --tty -i kafka-client --namespace hermes-chaos -- bash

    PRODUCER:
        kafka-console-producer.sh \

            --broker-list kafka-0.kafka-headless.hermes-chaos.svc.cluster.local:9092,kafka-1.kafka-headless.hermes-chaos.svc.cluster.local:9092,kafka-2.kafka-headless.hermes-chaos.svc.cluster.local:9092 \
            --topic test

    CONSUMER:
        kafka-console-consumer.sh \

            --bootstrap-server kafka.hermes-chaos.svc.cluster.local:9092 \
            --topic test \
            --from-beginning
```

# go kafka demo
https://docs.confluent.io/platform/current/tutorials/examples/clients/docs/go.html
