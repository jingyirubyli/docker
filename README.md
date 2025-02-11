# docker

由于本人一直使用mac book pro,从intel chip到apple silicon,配置各种环境时会遇到各种问题.

这个仓库存一些配置docker时的步骤和笔记.

基于mac book m3 pro: MacOS 15.3 Sequoia


docker和GPU的问题，直接使用docker运行的容器是不能调用GPU的，因为docker的镜像是脱离硬件的，而cuda的安装必须依赖于硬件，所以在镜像中无法安装cuda。利用GPU处理图像的深度学习问题是高效的，而且每个深度学习的框架工具也是支持GPU模式的。为了解决这个问题，英伟达公司发布了nvidia-docker。

https://docs.nvidia.com/datacenter/cloud-native/container-toolkit/latest/install-guide.html
