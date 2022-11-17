---
layout: post
title:  "Baca Tulis NTFS di MacOS Tanpa Install Software"
author: wakhid
categories: [ centOS, Security, Server ]
image: "https://storage.wakhid.com/img/wakhidcom_bacatulis_nfts_mac_000.png"
---


Bagi Saya pengguna MacOS, pastinya pernah mengalami kendala saat perlu mengakses External Drive yang ber-format NTFS yang hanya bisa membaca tetapi tidak bisa menulis atau menambahkan file ke dalam partisi tersebut.

Format partisi disk NTFS ini dibuat oleh Microsoft untuk sistem operasi Windows. Karena NTFS adalah hak milik Microsoft, Apple memerlukan lisensi khusus untuk menggunakannya di Mac yang mereka jual.

Sebetulnya MacOS memiliki kemampuan untuk membaca dan menulis ke partisi NTFS, tapi saya kurang mengetahui mengapa MacOS memberikan akses ke partisi NTFS ini hanya sebatas membaca saja, Read-Only File System. Mungkin alasan lisensi atau alasan bisnis ?.

```bash
❯ cd /Volumes/My\ Book

/Volumes/My Book
❯ touch test-ntfs-mac
touch: test-ntfs-mac: Read-only file system
```

Ada beberapa cara untuk MacOS dapat menulis ke partisi NTFS, salah satunya menggunakan aplikasi pihak ketiga dan berbayar.

Tetapi karena saya tidak mau membayar, jadi saya putuskan untuk men-enable kemampuan menulis MacOS ke partisi NTFS dengan cara berikut :


## Mendapatkan ID Disk NTFS
Ketahui informasi ID Disk NTFS dengan perintah diskutil. Ketik perintah berikut di terminal  :

```bash
sudo diskutil list
```

```bash
/dev/disk2 (external, physical):
   #:                       TYPE NAME                    SIZE       IDENTIFIER
   0:     FDisk_partition_scheme                        *3.0 TB     disk2
   1:               Windows_NTFS My Book                 3.0 TB     disk2s1
```

## Mendapatkan UUID Disk NTFS
Disk ID saya adalah **disk2s1**. Lanjutkan dengan menampilkan informasi UUID disk2s1.

```bash
 sudo diskutil info disk2s1 | grep -i UUID
   Volume UUID:               5F78A9F2-23B7-409D-92DE-73C2B587936D
```

## Konfigurasi Fstab
Buat file /etc/fstab dan isikan dengan baris konfigurasi di bawah.

*UUID diubah dengan UUID yang didapatkan pada langkah sebelumnya.*

```bash
sudo nano /etc/fstab
UUID=5F78A9F2-23B7-409D-92DE-73C2B587936D none ntfs rw,auto,nobrowse
```

![](https://storage.wakhid.com/img/wakhidcom_bacatulis_nfts_mac_2.png)


Selanjutnya, Eject disk dan kemudian hubungkan ulang disk ke Mac. Setelah disk terhubung ke Mac, disk sudah bisa melakukan baca dan tulis ke partisi NTFS. Bisa dicoba dengan melakukan pembuatan file melalui Finder.

Di sini, saya mencoba membuat file baru ke partisi NTFS dan berhasil.

![](https://storage.wakhid.com/img/wakhidcom_bacatulis_nfts_mac_3.png)

