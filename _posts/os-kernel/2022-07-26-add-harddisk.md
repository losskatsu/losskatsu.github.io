---
title: "[리눅스] 우분투 하드 디스크 추가 마운트 하기" 
categories:
  - os-kernel
tags:
  - os
use_math: true
toc: true
toc_label: "My Table of Contents"
toc_icon: "cog"
sidebar:
  title: "AI Machine Learning"
  nav: sidebar-contents
---

# 우분투 하드 디스크 추가 마운트 하기

## 1. 물리 서버에 하드디스크가 설치가 되었는지 확인

물리 서버에 하드디스크가 설치 되었는지 ```sudo fdisk -l``` 명령어로 확인합시다.

```bash
$  sudo fdisk -l

Disk /dev/loop0: 46.98 MiB, 49233920 bytes, 96160 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop2: 67.25 MiB, 70508544 bytes, 137712 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop3: 61.95 MiB, 64933888 bytes, 126824 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop4: 67.83 MiB, 71106560 bytes, 138880 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop5: 46.98 MiB, 49242112 bytes, 96176 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop6: 61.98 MiB, 64966656 bytes, 126888 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 476.96 GiB, 512110190592 bytes, 1000215216 sectors
Disk model: Samsung SSD 860
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 6FF1EABD-9626-4744-BE66-6CF574D1654A


Disk /dev/sdb: 12.75 TiB, 14000519643136 bytes, 27344764928 sectors
Disk model: WDC  WUH721414AL
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: AE940DFF-E862-4657-BA85-0B6E1A6B0D9D

Device       Start         End     Sectors  Size Type
/dev/sdb1     2048        4095        2048    1M BIOS boot
/dev/sdb2     4096     3149823     3145728  1.5G Linux filesystem
/dev/sdb3  3149824 27344762879 27341613056 12.7T Linux filesystem


Disk /dev/mapper/ubuntu--vg-ubuntu--lv: 100 GiB, 107374182400 bytes, 209715200 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
```

위와 같은 결과를 보면 뭐가 설치 된게 굉장히 많은 것을 볼 수 있습니다. 

현재 디스크 사용량을 확인하면 다음과 같습니다.

```bash
$ df -h
Filesystem                         Size  Used Avail Use% Mounted on
udev                                32G     0   32G   0% /dev
tmpfs                              6.3G  2.2M  6.3G   1% /run
/dev/mapper/ubuntu--vg-ubuntu--lv   98G   75G   19G  80% /
tmpfs                               32G     0   32G   0% /dev/shm
tmpfs                              5.0M     0  5.0M   0% /run/lock
tmpfs                               32G     0   32G   0% /sys/fs/cgroup
/dev/loop0                          47M   47M     0 100% /snap/snapd/16010
/dev/loop4                          68M   68M     0 100% /snap/lxd/22753
/dev/loop3                          62M   62M     0 100% /snap/core20/1518
/dev/loop2                          68M   68M     0 100% /snap/lxd/21835
/dev/loop5                          47M   47M     0 100% /snap/snapd/16292
/dev/sdb2                          1.5G  209M  1.2G  16% /boot
/dev/loop6                          62M   62M     0 100% /snap/core20/1581
tmpfs                              6.3G     0  6.3G   0% /run/user/1000
```

그럼 앞선 결과와 비교하면 제가 추가적으로 설치해야할 것은 다음과 같습니다.

* /dev/sda
* /dev/sdb3

설치합시다. sda부터 하죠

```bash
$ sudo parted /dev/sda

(parted) mklabel gpt
Warning: The existing disk label on /dev/sda will be destroyed and all data on this disk will be lost. Do you want to continue?
Yes/No? y
(parted) unit TB
(parted) unit GB
(parted) mkpart primary 0.00GB 476.96GB
(parted) print
Model: ATA Samsung SSD 860 (scsi)
Disk /dev/sda: 512GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags:

Number  Start   End    Size   File system  Name     Flags
 1      0.00GB  477GB  477GB               primary
 
(parted) quit
Information: You may need to update /etc/fstab.
```
