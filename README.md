# 3rd_group
just a research

## 導覽
以下操作皆在Ubuntu 16.04環境下進行,並已接上GPU
在此系統都已抓取到GPU,且無其他錯誤回報
按照以下目錄操作

目錄待補
### 關閉nouveau顯示驅動

由於需要安裝Nvidia自家的驅動,因此並不需要此預設的開源驅動,要先關閉他
```
echo "blacklist nouveau" >> /etc/modprobe.d/blacklist-nouveau.conf
echo "options nouveau modeset=0" >> /etc/modprobe.d/blacklist-nouveau.conf  
```
重新build kernel
```
sudo update-initramfs -u
```

抓取Nvidia Cuda 在這裡直接用wget,方便省事
```
wget https://developer.nvidia.com/compute/cuda/9.0/Prod/local_installers/cuda_9.0.176_384.81_linux-run
```
