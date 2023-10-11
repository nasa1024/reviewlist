# Kata Containers

## Kata Containers 中使用cgroup隔离进程
在Kata Containers中，cgroup (控制组) 通常用于限制分配给进程的资源。以下是使用cgroup在Kata Containers中隔离进程的一些相关信息：

### Kata Containers与Cgroup交互：
- Kata Containers 可以加载现有的 cgroup，并将所有与工作负载无关的进程移动到该 cgroup 中，或者允许 Kata Containers 创建一个名为 ***/kata_overhead*** 的 cgroup，并在稍后调整其大小​1​。

### 容器运行时与Cgroup交互：
- 在Linux上，cgroup用于限制分配给进程的资源。Kubernetes中的kubelet和底层容器运行时都需要对接cgroup来强制执行为Pod和容器管理资源，并为CPU、内存等资源设置请求和限制​2​。

### Kata Containers架构：
Kata Containers的架构包括与OCI运行时规范兼容的runtime，以及与Kubernetes CRI进行无缝协作的能力。Kata为kubelet创建的Pod创建QEMU/KVM虚拟机。Kata Containers的入口点是containerd-shim-kata-v2 (shimv2)，它为Kata实现了Containered Runtime V2（Shim API）。在Kata Containers中，由kata-agent生成的容器进程在虚拟机内部作为守护程序运行，kata-agent使用VIRTIO串行或VSOCK接口在虚拟机中运行ttRPC服务器，该接口由QEMU生成一个Socket文件暴露给宿主机。shimv2使用ttRPC协议与代理进程进行通信，该协议允许运行时将容器管理命令发送到代理进程，并用于在容器和管理引擎（例如CRI-O或Containerd）之间承载I/O流（stdout，stderr，stdin）​​。



## refrerence

- [Kata Containers](https://katacontainers.io/)
- [Infoq](https://www.infoq.cn/article/dgbkj0dwftxeusp64dk9)
- [Kata GitHub](https://github.com/kata-containers/kata-containers)