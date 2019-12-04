# 2.2 调度原理
## 2.2.1 k8s rc

一个service会由多个rc管理的不同pod组成

pod的重启策略是always的时候，rc才会自动重启

kubectl 可以rolling-update 新建一个rc，然后逐步替换旧的rc版本

rc可以设置track实现不同版本的并存和区分
