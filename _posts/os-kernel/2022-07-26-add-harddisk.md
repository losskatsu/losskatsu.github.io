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

포맷합시다.

```bash
$ mkfs.ext4 /dev/sda1
mke2fs 1.45.5 (07-Jan-2020)
Could not open /dev/sda1: Permission denied
dlit@ubuntu:/mnt$ sudo mkfs.ext4 /dev/sda1
mke2fs 1.45.5 (07-Jan-2020)
Discarding device blocks: done
Creating filesystem with 116445184 4k blocks and 29114368 inodes
Filesystem UUID: 2968a0cd-a585-4209-af44-b96c4c50e6a9
Superblock backups stored on blocks:
        32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208,
        4096000, 7962624, 11239424, 20480000, 23887872, 71663616, 78675968,
        102400000

Allocating group tables: done
Writing inode tables: done
Creating journal (262144 blocks): done
Writing superblocks and filesystem accounting information: done
```



## uuid 확인

```bash
$ sudo blkid
/dev/sdb2: UUID="ba60a0a0-43b4-41f9-8387-a065d5e10ee5" TYPE="ext4" PARTUUID="e7a14476-9786-4bc6-b228-75715cc63ce1"
/dev/sdb3: UUID="iB4KjP-hKXU-STam-O7Ar-i1eV-K2Hk-iasW6g" TYPE="LVM2_member" PARTUUID="606a155d-4b5f-4d6c-b340-ca8af40b5a89"
/dev/mapper/ubuntu--vg-ubuntu--lv: UUID="bf14c884-986e-46fe-8c30-f28e2626329e" TYPE="ext4"
/dev/loop0: TYPE="squashfs"
/dev/loop2: TYPE="squashfs"
/dev/loop3: TYPE="squashfs"
/dev/loop4: TYPE="squashfs"
/dev/loop5: TYPE="squashfs"
/dev/loop6: TYPE="squashfs"
/dev/sda1: PARTLABEL="primary" PARTUUID="33a1691f-1775-4cab-a842-71cf413dedb8"
/dev/sdb1: PARTUUID="849e2020-61eb-4399-952e-a46d47ef51ed"
```

```bash
$ sudo mkdir /mnt/sda
```
