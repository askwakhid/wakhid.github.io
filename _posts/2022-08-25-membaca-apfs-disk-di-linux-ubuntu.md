---
layout: post
title:  "Cara Membaca APFS macOS Disk Volume di Linux Ubuntu"
author: wakhid
categories: [ macOS, Linux, Ubuntu]
image: "https://storage.wakhid.com/img/wakhidcom_baca_apfs_linux_000.png"
---
Saat ini saya bekerja menggunakan macOS Monterey dan Linux Ubuntu 22.04. Ada salah satu external disk saya yang masih berformat APFS sehingga disk tersebut tidak bisa diakses di Linux Ubuntu.

Setelah mencari solusinya, akhirnya saya menemukan project Open Sources yang dapat mengatasi kendala ini. Project tersebut bernama [APFS FUSE Driver for Linux](https://github.com/sgan81/apfs-fuse).

## Apa itu APFS ?
Apple File System (APFS) adalah proprietary file system yang dibuat oleh Apple Inc. APFS mulai digunakan sebagai default file system untuk komputer Mac sejak dirilisnya macOS 10.13.

Karena Apple belum memberikan informasi ke publik terkait spesifikasi APFS volume format, mengakibatkan disk dengan format APFS tidak bisa dibuka secara langsung di sistem operasi lain seperti Windows, Linux dan sistem operasi lainnya.


## Proses Instalasi APFS FUSE Driver for Linux

1. Instal Libraries yang diperlukan
    ```bash
    sudo apt install libicu-dev bzip2 cmake libz-dev libbz2-dev fuse3 libfuse3-3 libfuse3-dev clang git libattr1-dev
    ```

2. Clone Repository APFS FUSE Driver
    ```bash
    git clone https://github.com/sgan81/apfs-fuse.git
    cd apfs-fuse
    git submodule init
    git submodule update
    ```

3. Compile APFS FUSE Driver
    ```bash
    mkdir build
    cd build
    cmake ..
    make
    ```

4. Setelah proses compile selesai, salin binary APFS FUSE Driver ke /user/local/bin agar bisa diakses dari path mana pun
    ```bash
    sudo cp apfs-* /usr/local/bin
    ```

5. Melihat disk yang terdeteksi di komputer untuk mengetahui yang mana disk dengan format volume APFS
    ```bash
    sudo fdisk -l
    ```

6. Pada komputer saya, APFS volume terdeteksi berada di /dev/sdb2
    ```bash
    Disk /dev/sdb: 223,57 GiB, 240057409536 bytes, 468862128 sectors
    Disk model: USB3.0          
    Units: sectors of 1 * 512 = 512 bytes
    Sector size (logical/physical): 512 bytes / 4096 bytes
    I/O size (minimum/optimal): 4096 bytes / 4096 bytes
    Disklabel type: gpt
    Disk identifier: 0353AC9D-1802-4656

    Device      Start       End   Sectors   Size Type
    /dev/sdb1      40    409639    409600   200M EFI System
    /dev/sdb2  411648 468860927 468449280 223,4G Apple APFS
    ```

7. Buat folder baru di /media sebagai target mounting APFS volume nantinya.
    ```bash
    sudo mkdir -p /media/$USERNAME/macExt
    ```

8. Mounting APFS volume ke folder yang sudah dibuat di langkah ke-6
    ```bash
    sudo apfs-fuse -o allow_other /dev/sdb2 /media/$USERNAME/macExt
    ```

9. Buka file manager untuk mengakses APFS volume yang sudah berhasil ter-mounting di direktori /media/$USERNAME/macExt

![Membaca APFS Disk di Linux Ubuntu](https://storage.wakhid.com/img/wakhidcom_baca_apfs_linux_2.png)


![Membaca APFS Disk di Linux Ubuntu](https://storage.wakhid.com/img/wakhidcom_baca_apfs_linux_3.png)

---