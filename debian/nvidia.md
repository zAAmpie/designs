# Installing NVIDIA drivers

This is quite the ordeal, so here are some prerequisites.

## Download the relevant driver

Go to https://www.nvidia.com/download/index.aspx?lang=en-us and get the newest driver URL. You can then wget it on the host:

```
wget https://us.download.nvidia.com/XFree86/Linux-x86_64/550.67/NVIDIA-Linux-x86_64-550.67.run
```

## Run the installer first to disable neavoux driver and reboot

```
chmod +x NVIDIA-Linux-x86_64-550.67.run
sudo ./NVIDIA-Linux-x86_64-550.67.run
sudo reboot
```

It will complain that the previous driver is still installed. Accept to add the modprobe stuff and eventually rerun initrmfs.

## Install required kernel headers

The driver requires the kernel headers because it compiles into a kernel module. Install it for your linux kernel:

```
sudo apt install linux-headers-$(uname -r)
```

## Rerun the NVIDIA installer

Things should be in a slightly better state now (it will still complain a bunch about X not being installed etc.)

```
sudo ./NVIDIA-Linux-x86_64-550.67.run
```

## Test

If everything went well, you should be able to see the GPU using the following command and it should show something like this:

```
nvidia-smi
```

```
Thu Mar 21 16:15:50 2024
+-----------------------------------------------------------------------------------------+
| NVIDIA-SMI 550.67                 Driver Version: 550.67         CUDA Version: 12.4     |
|-----------------------------------------+------------------------+----------------------+
| GPU  Name                 Persistence-M | Bus-Id          Disp.A | Volatile Uncorr. ECC |
| Fan  Temp   Perf          Pwr:Usage/Cap |           Memory-Usage | GPU-Util  Compute M. |
|                                         |                        |               MIG M. |
|=========================================+========================+======================|
|   0  NVIDIA GeForce GTX 1070        Off |   00000000:02:00.0 Off |                  N/A |
| 33%   47C    P0             34W /  151W |       0MiB /   8192MiB |      2%      Default |
|                                         |                        |                  N/A |
+-----------------------------------------+------------------------+----------------------+

+-----------------------------------------------------------------------------------------+
| Processes:                                                                              |
|  GPU   GI   CI        PID   Type   Process name                              GPU Memory |
|        ID   ID                                                               Usage      |
|=========================================================================================|
|  No running processes found                                                             |
+-----------------------------------------------------------------------------------------+
```
