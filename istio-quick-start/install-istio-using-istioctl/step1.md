本教程将自动帮您启动一个包含2个节点的 Kubernetes 集群（包含一个 master 节点，一个 worker 节点），Kubernetes 版本为 v1.14.0

#### 检查 Kubernetes 集群

使用前，检查 Kubernetes 集群状态：`kubectl cluster-info`{{execute}}

如果集群未启动，请执行：`launch.sh`{{execute}}

检查 `katacoda-cloud-provider`，这个会影响到环境是否能正常提供外部负载均衡:

`kubectl get deploy -n kube-system katacoda-cloud-provider`{{execute}}

还可以使用 `kubectl` 命令执行一些其他命令，检查 Kubernetes 集群的完整性。

正常启动了就可进入下一步了。
