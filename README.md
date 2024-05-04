# latx-amdvlk-res
Latx 下 修改过的 amdvlk和其他资源

可以在 latx-1.5.0 下 运行 dxvk-1.10.3 （ dxvk>2.0 因为latx缺少 SYNCOBJ 系列ioctl支持，且不支持 libvulkan.so直通，所以无法工作）

DX12 (vkd3d-proton )因为缺少SYNCOBJ ，导致vulkan timeline_semaphore 扩展缺失，无法运行

测试使用的wine版本：
wine-lutris-GE-Proton8-26-x86_64
wine-proton-8.0-5-amd64
wine-9.7-staging-tkg-amd64
