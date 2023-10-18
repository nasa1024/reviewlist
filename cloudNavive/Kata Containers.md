# Kata Containers

## Kata Containers 中使用cgroup隔离进程
在Kata Containers中，cgroup (控制组) 通常用于限制分配给进程的资源。以下是使用cgroup在Kata Containers中隔离进程的一些相关信息：

### Kata Containers与Cgroup交互：
- Kata Containers 可以加载现有的 cgroup，并将所有与工作负载无关的进程移动到该 cgroup 中，或者允许 Kata Containers 创建一个名为 ***/kata_overhead*** 的 cgroup，并在稍后调整其大小​1​。

### 容器运行时与Cgroup交互：
- 在Linux上，cgroup用于限制分配给进程的资源。Kubernetes中的kubelet和底层容器运行时都需要对接cgroup来强制执行为Pod和容器管理资源，并为CPU、内存等资源设置请求和限制​2​。

# 结论
如果只是使用并不需要对*cgroup*进行特殊的配置，让运维配置好即可。


## refrerence

- [Kata Containers](https://katacontainers.io/)
- [Infoq](https://www.infoq.cn/article/dgbkj0dwftxeusp64dk9)
- [Kata GitHub](https://github.com/kata-containers/kata-containers)
- [K8s-katacontainer 实践](https://zhuanlan.zhihu.com/p/109256949)