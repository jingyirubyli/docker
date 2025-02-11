# docker

由于本人一直使用mac book pro,从intel chip到apple silicon,配置各种环境时会遇到各种问题.

这个仓库存一些配置docker时的步骤和笔记.

基于mac book m3 pro: MacOS 15.3 Sequoia


- docker和GPU的问题，直接使用docker运行的容器是不能调用GPU的，因为docker的镜像是脱离硬件的，而cuda的安装必须依赖于硬件，所以在镜像中无法安装cuda。利用GPU处理图像的深度学习问题是高效的，而且每个深度学习的框架工具也是支持GPU模式的。为了解决这个问题，英伟达公司发布了nvidia-docker。

https://docs.nvidia.com/datacenter/cloud-native/container-toolkit/latest/install-guide.html

- Mac 上的 docker 实际上在 HyperKit 下运行的 LinuxKit VM 中运行。它首先会为 hyperkit 获取硬件直通，以便它识别 GPU。然后它会获取一个驱动程序来为 linuxkit 上的 gpu 运行，然后我认为它会传递一些 docker 标志，以便它能够获得与硬件通信的特权。

参考: https://github.com/NVIDIA/nvidia-docker/issues/758

- 最初的docker是不支持gpu的. 从docker 19版本之后，nvidia-docker成为了过去式。不需要单独去下nvidia-docker这个独立的docker应用程序，也就是说gpu docker所需要的Runtime被集成进docker中，使用的时候用–gpus参数来控制。

参考: https://blog.csdn.net/Castlehe/article/details/120194820
