#关于Calico

Calico为容器和虚拟机工作负载提供安全的网络连接。

Calico创建并管理平面第3层网络，为每个工作负载分配完全可路由的IP地址。工作负载可以在没有IP封装或网络地址转换的情况下进行通信，以实现裸机性能，简化故障排除和更好的互操作性。在需要覆盖的环境中，Calico使用IP-in-IP隧道技术，或者可以与flannel等其他覆盖网络配合使用。

Calico还提供网络安全规则的动态实施。使用Calico的简单策略语言，您可以实现对容器，虚拟机工作负载和裸机主机端点之间通信的控制。

Calico v3.1经过大规模生产验证，与Kubernetes，OpenShift和OpenStack集成。

###这个怎么运作

![avatar](https://docs.projectcalico.org/images/calico-arch-gen-v3.1.svg)

Calico利用Linux内核原生的路由和iptables防火墙功能。进出各个容器，虚拟机和主机的所有流量都会在路由到目标之前遍历这些内核规则。

calicoctl：允许您从简单的命令行界面实现高级策略和网络。

orchestrator插件：提供与各种流行协调器的紧密集成和同步。

key / value store：保存Calico的策略和网络配置状态。

calico / node：在每个主机上运行，​​从键/值存储读取相关的策略和网络配置信息，并在Linux内核中实现它。

