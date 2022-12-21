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


**참고링크**

| 운영체제 | 프론트엔드 | 백엔드 | 데이터베이스| 인프라 |
|:------:|:------:|:------:|:------:|:------:|
|[리눅스구조](https://losskatsu.github.io/os-kernel/os-linux-structure) | [js필터](https://losskatsu.github.io/frontend/js-map-reduce-filter/) | [아파치에러로그](https://losskatsu.github.io/it-infra/apache-error-log/) | [행삭제](https://losskatsu.github.io/it-infra/sqldelete/) | [아파치스쿱](https://losskatsu.github.io/it-infra/sqoop/) |
|[프로세스](https://losskatsu.github.io/os-kernel/os-process/) | [헬로월드](https://losskatsu.github.io/frontend/react-helloworld/) | [웹서버개념](https://losskatsu.github.io/it-infra/webserver/) | [ES기초](https://losskatsu.github.io/it-infra/es-basic/) | [로그분석](https://losskatsu.github.io/it-infra/log-anal/) |
|[네임스페이스](https://losskatsu.github.io/os-kernel/linux-redirection/) |[프로젝트생성](https://losskatsu.github.io/frontend/react-basic-setup/) | [아파치설치](https://losskatsu.github.io/it-infra/aws-apache/) | [MySQL기초](https://losskatsu.github.io/it-infra/mysql-index/) | [beeline](https://losskatsu.github.io/it-infra/beeline/) |
|[디렉토리](https://losskatsu.github.io/os-kernel/linux-directory/) |[헤더생성](https://losskatsu.github.io/frontend/react-category/) | [flask연동](https://losskatsu.github.io/it-infra/flask-nginx-uwsgi/) | [큐브리드](https://losskatsu.github.io/it-infra/cubrid-summary/) | [하둡기초](https://losskatsu.github.io/it-infra/hadoop-basic-concept/) |
|[리다이렉션](https://losskatsu.github.io/os-kernel/linux-redirection/) |[async-get](https://losskatsu.github.io/frontend/react-request-api-django/) | [장고MsSQL연결](https://losskatsu.github.io/it-infra/mssql-django-conn/) | [null공백](https://losskatsu.github.io/it-infra/db-null/) |  [나이파이](https://losskatsu.github.io/it-infra/nifi/) |
|[쓰레드](https://losskatsu.github.io/os-kernel/process-thread/) | [async-post](https://losskatsu.github.io/frontend/react-request-post/) | [장고MySQL연결](https://losskatsu.github.io/it-infra/mysql-django-conn/) | [MySQL설치(win)](https://losskatsu.github.io/it-infra/mysql-install-win/) | [백본](https://losskatsu.github.io/it-infra/backbone/) |
|[라즈베리파이설치](https://losskatsu.github.io/os-kernel/raspberry-vminstall/) | [로그인페이지](https://losskatsu.github.io/frontend/react-request-post/) | [장고inpectdb](https://losskatsu.github.io/it-infra/django-inspectdb/) | [MySQL테이블생성](https://losskatsu.github.io/it-infra/mysql-create-db/) | [제플린](https://losskatsu.github.io/it-infra/backbone/) |
|[OSI7계층소개](https://losskatsu.github.io/os-kernel/network-basic01/) | | [장고read](https://losskatsu.github.io/it-infra/django-read-data/)  |  | [SSL인증](https://losskatsu.github.io/it-infra/ssl-auth/)|
|[OSI1계층](https://losskatsu.github.io/os-kernel/network-basic02/) | | [장고insert](https://losskatsu.github.io/it-infra/django-post-data/)  | | [커버로스](https://losskatsu.github.io/it-infra/kerberos/) |
|[OSI2계층](https://losskatsu.github.io/os-kernel/network-basic03/) | | [장고put](https://losskatsu.github.io/it-infra/django-put-data/)  | | [도커개념](https://losskatsu.github.io/it-infra/docker00/) |
|[OSI3계층](https://losskatsu.github.io/os-kernel/network-basic04/) | | [장고del](https://losskatsu.github.io/it-infra/django-del-data/) | | [도커설치](https://losskatsu.github.io/it-infra/docker01/) |
|[OSI4계층](https://losskatsu.github.io/os-kernel/network-basic05/) | | [flask한글요청](https://losskatsu.github.io/programming/py-flask-korean/) | |[도커기초](https://losskatsu.github.io/it-infra/docker02/)|
|[OSI5,6,7계층](https://losskatsu.github.io/os-kernel/network-basic05/) | |  | | [도커이미지](https://losskatsu.github.io/it-infra/docker03/) |
|[DNS서버](https://losskatsu.github.io/os-kernel/etc-host-dns/) | |  | | [컨테이너네트워크](https://losskatsu.github.io/it-infra/docker04/) |
|[DHCP](https://losskatsu.github.io/os-kernel/dhcp/) | | | | [도커API](https://losskatsu.github.io/it-infra/docker05/) |
|[bashrc](https://losskatsu.github.io/os-kernel/bashrc/) | | | | [도커컴포즈](https://losskatsu.github.io/it-infra/docker06/) |
|[bash](https://losskatsu.github.io/os-kernel/bash/) | | | | [도커볼륨](https://losskatsu.github.io/it-infra/docker07/) |
|[ifconfig](https://losskatsu.github.io/os-kernel/ifconfig/) | | | | [장고이미지](https://losskatsu.github.io/it-infra/docker08/) |
|[소켓프로그래밍](https://losskatsu.github.io/os-kernel/network-socket/) | | | | [도커postgre](https://losskatsu.github.io/it-infra/docker09/) |
|[리눅스유저생성](https://losskatsu.github.io/os-kernel/linux-create-user/) | | | | [도커이미지삭제](https://losskatsu.github.io/it-infra/docker10/)|
|[netstat포트열기](https://losskatsu.github.io/os-kernel/port-open/) | | | |[도커Redis](https://losskatsu.github.io/it-infra/docker11/) |
|[컴파일러](https://losskatsu.github.io/os-kernel/compiler-interpreter/) | | | |[k8s구조](https://losskatsu.github.io/it-infra/kubernetes01/) |
|[운영체제vs커널](https://losskatsu.github.io/os-kernel/diff-kernel-os/) | | | | [k8s설치](https://losskatsu.github.io/it-infra/kubernetes02/) |
|[작업스케쥴링](https://losskatsu.github.io/os-kernel/crontab/) | | | |[k8s서비스배포](https://losskatsu.github.io/it-infra/kubernetes03/) |
|[디스크추가](https://losskatsu.github.io/os-kernel/add-harddisk/) | | | |[POD네트워크](https://losskatsu.github.io/it-infra/kubernetes04/) |
|[aws유저추가](https://losskatsu.github.io/os-kernel/aws-add-user/) | | | | [퍼시스턴트볼륨](https://losskatsu.github.io/it-infra/kubernetes05/)|
|[기초명령어](https://losskatsu.github.io/it-infra/ps-grep-pipe-redirect/) | | | | [k8s에러](https://losskatsu.github.io/it-infra/kubernetes06/)|
|[포트번호](https://losskatsu.github.io/it-infra/port/) | | | | |

## 1. 물리 서버에 하드디스크 직접 설치

이번 포스팅은 우분투 운영체제에서 물리서버에 추가된 하드디스크를 마운트 하는 실습을 해보겠습니다. 
이를 위한 전제 조건은 물리 서버에 하드디스크를 설치 했다고 가정하겠습니다. 

## 2. 물리 서버에 하드디스크가 설치가 되었는지 확인

실제로 물리 서버에 하드디스크가 설치 되었는지 확인하기 위해 ```sudo fdisk -l``` 명령어를 입력합니다.
```fdisk```명령어는 디스크 파티션을 관리 할 때 사용하는 명령어입니다. 

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

위와 같은 결과를 보면 설치된 디스크가 굉장히 많은 것을 볼 수 있습니다. 
위 디스크 중 일부는 실제 사용 중이고 일부는 사용 중이지 않습니다. 
위 디스크 중 사용 중이 디스크를 사용하기 위해서는 다음과 같이 ```df -h```명령어를 입력하면 됩니다.

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

앞선 ```fdisk``` 결과와 비교하면 sda와 sdb3가 사용중이지 않은 것을 알 수 있습니다.
따라서 제가 추가적으로 설치해야할 것은 다음과 같습니다.

* /dev/sda
* /dev/sdb3

## 3. sda 마운트 준비 

그럼 지금부터 sda를 마운트 하겠습니다. 
먼저 sda를 마운트(mount)할 디렉토리를 만들어줍니다.
이 때, 마운트(mount)란 저장 장치에 접근할 수 있는 경로를 디렉터리 구조에 연결시키는 작업을 말합니다.
쉽게 생각하면 윈도우에서 usb 사용하는 것을 생각하면 됩니다. 
윈도우 운영체제를 쓰면서 usb를 삽입하면 저절로 D드라이브가 생기는 것을 볼 수 있는데, 
이것이 usb가 마운트 된 것입니다.

```bash
$ sudo mkdir /mnt/sda
```

위 코드는 ```/mnt/sda``` 경로에 sda 디스크를 마운트하겠다는 의미입니다. 

우리가 마운트 해야할 sda의 용량은 약 500기가 입니다. 
참고로 ```fdisk```가 지원하는 용량은 2TB까지 이고 2TB이상은 GPT 파티션을 써야합니다. 
참고로 fdisk는 MBR(Master Boot Record)이며, parted는 GPT(Guid Partition Table)입니다. 
GPT는 parted를 이용하면 가능합니다. 
물론 2TB 미만도 parted로 파티션할 수 있습니다. 
이번 실습에서는 parted를 사용해서 해보겠습니다.

```bash
$ sudo parted /dev/sda

(parted) mklabel gpt
Warning: The existing disk label on /dev/sda will be destroyed and all data on this disk will be lost. Do you want to continue?
Yes/No? y
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

위 코드를 보면 첫줄에서 ```sudo parted /dev/sda```라고 써있는데 이는 ```dev/sda``` 디스크의 파티션을 생성하겠다는 의미입니다. 
첫줄을 입력하면 (parted) 모드로 진입합니다. 
그리고 ```mklabel gpt```는 디스크 라벨을 gpt로 설정하겠다는 의미입니다. 
레벨 타입에는 bsd, gpt, loop, mac, mips, msdos, pc98, sun이 있습니다. 
그리고 표시 단위를 기가 바이트로 하기 위해 ```unit GB```를 입력합니다. 
만약 테라 바이트를 단위로 하고 싶다면 ```unit TB```를 입력합니다. 
그리고 ```mkpart primary 0.00GB 476.96GB``` 명령어로 파티션을 나눕니다. 
명령어 순서는 ```mkpart 파티션타입 시작 끝```입니다. 
즉, 파티션 타입이 primary에 해당하며 시작은 0.00GB, 끝은 476.96GB라는 뜻입니다. 
참고로 파티션 타입에는 primary, logical, extened가 존재합니다. 
그리고 ```print```로 결과를 확인하고 ```quit```로 나갑니다. 
그러면 ```/etc/fstab```파일을 업데이트 하라는데 이 파일은 잠시후에 업데이트 하겠습니다. 

## 4. 디스크 포맷


그러면 본격적인 마운트 전에 디스크를 포맷해보겠습니다. 
다음 코드는 ext4 포맷으로 포맷하겠다는 것을 의미합니다.
이 때, ext4는 extended file system 4를 뜻 합니다. 

```bash
$ sudo mkfs.ext4 /dev/sda1
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

참고로 위 코드에서 mkfs는 Make File System의 약자입니다. 


## 5. uuid 확인

포맷하기 전에는 다음처럼 sda1의 UUID가 안보입니다.

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

그러나 포맷하면 다음처럼 짜잔하고 나타납니다.

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
/dev/sda1: UUID="2968a0cd-a585-4209-af44-b96c4c50e6a9" TYPE="ext4" PARTLABEL="primary" PARTUUID="33a1691f-1775-4cab-a842-71cf413dedb8"
/dev/sdb1: PARTUUID="849e2020-61eb-4399-952e-a46d47ef51ed"
```

UUID를 확인했다면 다음과 같이 fstab에 추가해줍니다.

```bash
$ sudo vim /etc/fstab

UUID=2968a0cd-a585-4209-af44-b96c4c50e6a9 /mnt/sda ext4 defaults 0 0
```

## 5. 마운트!

드디어 마운트!

```bash
$ sudo mount -a
```

끝났습니다. 디스크가 잘 추가 되었는지 확인해봅시다.

```bash
$ df -h
Filesystem                         Size  Used Avail Use% Mounted on
udev                                32G     0   32G   0% /dev
tmpfs                              6.3G  2.3M  6.3G   1% /run
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
/dev/sda1                          437G   73M  414G   1% /mnt/sda
```

## 6. 참고사항 - 마운트가 되어 있는데 안되어 있는 것 처럼 보이는 경우 

처음에 ```df -h``` 명령어로 디스크를 확인했는데, 
결과에 나오지 않는 디스크를 마운트 되지 않았다고 생각할 수 있는데, 
반드시 그런 것은 아닙니다. 
즉, ```sudo fdisk -l``` 명령어에서 나온 디스크가  
```df -h```결과에 나오지 않아도 마운트가 되어 있을수도 있어요. 
이걸 어떻게 알 수 있냐면 ```sudo blkid``` 명령어를 통해 
해당 디스크의 UUID가 나오는지를 보면 됩니다. 
즉, ```df -h``` 결과창에 안나와도 ```sudo blkid```에 UUID가 나오면 
해당 디스크는 마운트가 되어 있는 것이죠. 
그래서 이런 경우에는 바로 fstab에 추가해주고 마운트를 하면 됩니다. 
만약 이렇게 안하고 본 포스팅 가장 윗단계부터 강제 마운트, 포맷을 시도하려고 하면
"이미 파일이 쓰여지고 있는데 포맷할거임?"이라는 메시지가 뜨고 
그대로 진행할시 대참사가 날 수 있습니다. 
