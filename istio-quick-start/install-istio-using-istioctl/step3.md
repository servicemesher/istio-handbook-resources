使用 `demo` 配置快速安装一套 istio。

### 安装 demo 示例

使用 `demo` 配置安装 istio：

`istioctl manifest apply --set profile=demo`{{execute}}

检查 Kubernetes 服务是否部署正常，检查除 `jaeger-agent` 服务外的其他服务，是否均有正确的 `CLUSTER-IP`。

**注意**：这里要观察 `istio-ingressgateway` 的 `EXTERNAL-IP`，如果为 `<pending>`，则环境暂时不能正常提供外部负载均衡，无法使用 ingress gateway。 在这种情况下，可以等待一段时间，如果一段时间后还是 `<pending>` 状态，建议刷新页面，重新开启课程安装 istio：

`kubectl get svc -n istio-system`{{execute}}

检查相关 pod 是否部署成功，并且 `STATUS` 为 `Running`：

`kubectl get pods -n istio-system`{{execute}}

如果都正常部署，就可以部署自己的服务了。

### 后续步骤

部署成功后，就可以进入 Bookinfo 示例了，但这里不会展开介绍 Istio 的流量路由、故障注入、速率限制等功能，相关内容会在 Bookinfo 部分介绍，这里只做简单介绍。

