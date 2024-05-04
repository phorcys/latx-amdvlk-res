# 说明
由于目前latx 缺少DRM SYNCOBJ 系列ioctl支持，且不支持 libvulkan.so直通
所以 latx 下vulkan无法正常工作
amdvlk保留有不使用syncobj的 legacy 支持，改动pagesize后可在latx下正常运行
详细见：https://bbs.loongarch.org/d/403-latx-144-amdvlk-wine-dxvk

此repo 发布 修改过可在latx下运行的 amdvlk二进制和其他资源

# amdvlk
amdvlk仅修改一处
https://github.com/GPUOpen-Drivers/pal/blob/2682a9122ca4b6b0d5875e41ea347b6377922e47/src/core/os/amdgpu/amdgpuDevice.cpp#L107
4096 => 16384

amdvlk-loong64-fixed-latx-1.5.0.tar.xz 包含 32位和64位，放入 latx runtime对应位置
不同发行版制作的runtime lib路径可能有不同，自行修改json文件使之对应。

如果要检查是否成功配置，运行 x64/x32版本的 vulkaninfo和 vkcube 测试并观察是否使用amdvlk驱动（可设置 VK_LOADER_DEBUG=info环境变量观测）

# linux 原生游戏
安装后可满足部分原生linux  vulkan游戏运行
例如 X4:Foundation

# wine

测试使用的wine版本：
wine-lutris-GE-Proton8-26-x86_64  https://github.com/GloriousEggroll/wine-ge-custom/releases/tag/GE-Proton8-26
wine-proton-8.0-5-amd64 https://github.com/Kron4ek/Wine-Builds/releases/tag/proton-8.0-5
wine-9.7-staging-tkg-amd64 https://github.com/Kron4ek/Wine-Builds/releases/tag/9.7

# dxvk

目前可以在 latx 1.4.4/1.5.0 下 运行 dxvk-1.10.3 
dxvk>2.0 因为latx缺少 SYNCOBJ 系列ioctl支持，且不支持 libvulkan.so直通，所以无法工作

wine prefix安装dxvk后，可以正常支持 dx9 dx10 dx11 应用运行

# vkd3d
DX12 (vkd3d/vkd3d-proton )因为缺少SYNCOBJ ，导致vulkan timeline_semaphore 扩展缺失，无法运行



# x86 runtime

lat-i386-20240504.tar.zst
lat-x86_64-20240504.tar.zst 
是根据 archloongarch的 runtime制作脚本 https://github.com/loongarchlinux/lat-runtime/ 制作的最新runtime
如果遇到发行版自带 runtime问题，可以尝试替换使用。
