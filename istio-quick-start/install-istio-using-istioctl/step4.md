
为 `default` 命名空间打上 `istio-injection=enabled` 标签，将该命名空间设置为自动注入 Sidecar：

`kubectl label namespace default istio-injection=enabled`{{execute}}

## 部署应用

`kubectl apply -f samples/bookinfo/platform/kube/bookinfo.yaml`{{execute}}

确认所有服务和 pod 都已经正常启动了，请耐心等待：

`kubectl get services`{{execute}}

`kubectl get pods`{{execute}}

确认 Bookinfo 正常运行：

`kubectl exec -it $(kubectl get pod -l app=ratings -o jsonpath='{.items[0].metadata.name}') -c ratings -- curl productpage:9080/productpage | grep -o "<title>.*</title>"`{{execute}}

## 部署 ingress

定义 Ingress 网关：

`kubectl apply -f samples/bookinfo/networking/bookinfo-gateway.yaml`{{execute}}

确认网关成功创建：

`kubectl get gateway`{{execute}}

设置 ingress IP：

`export INGRESS_HOST=$(kubectl -n istio-system get service istio-ingressgateway -o jsonpath='{.status.loadBalancer.ingress[0].ip}')`{{execute}}

设置 ingress 端口：

`export INGRESS_PORT=$(kubectl -n istio-system get service istio-ingressgateway -o jsonpath='{.spec.ports[?(@.name=="http2")].port}')`{{execute}}

设置 `GATEWAY_URL`：

`export GATEWAY_URL=$INGRESS_HOST:$INGRESS_PORT`{{execute}}

## 确认访问

可以用 curl 命令来确认是否能够从集群外部访问 Bookinfo 应用程序：

`curl -s http://${GATEWAY_URL}/productpage | grep -o "<title>.*</title>"`{{execute}}

可以点击下面的连接查看：

https://[[HOST_SUBDOMAIN]]-80-[[KATACODA_HOST]].environments.katacoda.com/productpage

## 卸载 istio

卸载程序将删除 `RBAC` 权限、`istio-system` 命名空间和所有相关资源。可以忽略那些不存在的资源的报错，因为它们可能已经被删除掉了。

`istioctl manifest generate --set profile=demo | kubectl delete -f -`{{execute}}