从 istio v1.15 版本开始，[使用 helm 安装](https://istio.io/zh/docs/setup/install/helm/)的方式已经废弃，需改用 [istioctl 安装](https://istio.io/zh/docs/setup/install/istioctl/)。

## 下载 istio

可在 [istio release](https://github.com/istio/istio/releases/tag/1.5.1) 页面下载与您操作系统匹配的压缩文件，该文件中包含：安装文件、示例和 istioctl 命令行工具。

使用如下命令来下载 istio：

`curl -L https://istio.io/downloadIstio | sh -`{{execute}}

下载的 istio 包名为 `istio-1.6.*`(istio 1.6 的最新版本)，包含：
- `install/kubernetes`：包含 Kubernetes 相关的 YAML 安装文件。
- `examples/`：包含示例应用程序。
- `bin/`：包含 istioctl 的客户端文件。

切换到 istio 包所在目录：
`cd istio-*/`{{execute}}

使用如下命令将 `istioctl` 客户端路径加入 $PATH 中：
`export PATH=$PATH:$(pwd)/bin`{{execute}}

截止目前，我们已经可以使用高度自定义 Istio 控制平面和数据平面的 `istioctl` 命令行工具。 该命令行工具具有用户输入校验功能，可以防止错误的安装和自定义选项。

使用如下命令，查看更多关于 `istioctl` 的信息：
`istioctl -h`{{execute}}
