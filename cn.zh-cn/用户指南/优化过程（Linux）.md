# 优化过程（Linux）<a name="zh-cn_topic_0047501133"></a>

XEN虚拟化类型的弹性云服务器正逐渐转变为KVM虚拟化类型，因此XEN实例类型的的私有镜像，通常需要同时支持XEN虚拟化和KVM虚拟化。也建议您优化KVM虚拟化类型的私有镜像，避免最终发放的弹性云服务器出现一些不可预知的异常。

Linux弹性云服务器的正常运行需依赖于xen-pv驱动、virtio驱动等。因此，需要确保Linux私有镜像已完成相关配置，包括安装驱动、修改UUID等。

## 准备工作<a name="section88217277111"></a>

1.  将待优化的Linux镜像[创建](https://support.huaweicloud.com/qs-ecs/ecs_02_0010.html)弹性云服务器，并开机登录。
2.  查看Linux操作系统云服务器虚拟化类型。

    具体操作请参见[查看Linux操作系统云服务器虚拟化类型](查看Linux操作系统云服务器虚拟化类型.md)。

    请根据虚拟化类型选择对应的优化操作，不同的虚拟化类型优化过程略有不同。


## 私有镜像优化过程<a name="section862461118288"></a>

1.  为了成功安装原生的XEN和KVM驱动，需要先卸载弹性云服务器操作系统中安装的PV Driver。

    具体操作请参见[在Linux系统中卸载PV driver](在Linux系统中卸载PV-driver.md)。

    >![](public_sys-resources/icon-note.gif) **说明：** 
    >KVM虚拟化类型请忽略此步骤。

2.  修改grub文件磁盘标识方式为UUID。

    具体操作请参见[修改grub文件磁盘标识方式为UUID](修改grub文件磁盘标识方式为UUID.md)。

3.  修改fstab文件磁盘标识方式为UUID。

    具体操作请参见[修改fstab文件磁盘标识方式为UUID](修改fstab文件磁盘标识方式为UUID.md)。

4.  安装原生的驱动。
    -   对于XEN虚拟化类型，请安装原生的XEN驱动和KVM驱动。具体操作请参见[怎样安装原生的XEN和KVM驱动](怎样安装原生的XEN和KVM驱动.md)。
    -   对于KVM虚拟化类型，请安装原生的KVM驱动。具体操作请参见[安装原生的KVM驱动](安装原生的KVM驱动.md)。

5.  清除日志文件、历史记录等，关闭云服务器。

    具体操作请参见[清除日志文件](清除日志文件.md)。

6.  通过弹性云服务器创建Linux私有镜像。

