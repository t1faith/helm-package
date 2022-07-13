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
