# 3rd_group
just a research

## 導覽
以下操作皆在Ubuntu 16.04環境下進行,並已接上GPU
在此系統都已抓取到GPU,且無其他錯誤回報
按照以下目錄操作

目錄待補
### 軟體環境安裝

由於需要安裝Nvidia自家的驅動,因此並不需要此預設的開源驅動,要先關閉他
```
sudo echo "blacklist nouveau" >> /etc/modprobe.d/blacklist-nouveau.conf
sudo echo "options nouveau modeset=0" >> /etc/modprobe.d/blacklist-nouveau.conf  
```

重新build kernel
```
sudo update-initramfs -u
```

抓取Nvidia Cuda 在這裡直接用wget,方便省事
```
wget https://developer.nvidia.com/compute/cuda/9.0/Prod/local_installers/cuda_9.0.176_384.81_linux-run
```

安裝,參數建議依自身需求去下
```
chmod +x cuda_9.0.176_384.81_linux-run
sudo ./cuda_9.0.176_384.81_linux-run --silent --driver --toolkit
```

安裝完後應該要有成功回報,然後把LIBRARY抓出來,把以下寫進.bashrc
```
export PATH=/usr/local/cuda/bin:$PATH
export LD_LIBRARY_PATH=/usr/local/cuda/lib64:$LD_LIBRARY_PATH
```

接著看你要重登或是
```
exec bash
```
然後檢查一下
```
cat /proc/driver/nvidia/version 或者 nvidia-smi -a
nvcc -V
```
都有與硬體資訊相同的話就大功告成


### 安裝Nvidia-docker 

參考[官方](https://github.com/NVIDIA/nvidia-docker)
