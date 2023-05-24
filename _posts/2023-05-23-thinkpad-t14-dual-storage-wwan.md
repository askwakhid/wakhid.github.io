---
title: ThinkPad T14 Gen 1 Intel - Apakah Support Dual SSD NVME Storage ?
author: wakhid
date: 2023-05-23 12:32:00 -0500
categories: [Blogging, Review]
tags: [ThinkPad, Lenovo, Laptop]
---

Setelah beberapa waktu melakukan pencarian di Google dan membaca informasi di Forum Lenovo yang masih simpang siur tentang kompabilitas dual storage ThinkPad T14 Gen 1 (Intel), akhirnya Saya mencobanya sendiri.

Saya membeli sebuah Storage NMVE Gen3 x2 yang kompatible juga dengan ThinkPad seri sebelumnya (T480 dan T480s).

## Membeli NVME Yang Cocok (?)

Saya membeli sebuah NVME dengan spesifikasi sebagai berikut :
- Model : WD PC SN520
- Form Factor : M.2 2240 + 12MM =2242
- Interface : PCIe Gen 3 x2
- Capacity : 256GB
- Sequential Read up to 1,700 (MB/s)
- Sequential Write up to 1,400 (MB/s)
- Endurance (TBW) 300 TBW
- NVME ini juga bisa digunakan pada Slot WWAN T480 dan T480s.

Link pembelian : [https://tokopedia.link/AlLLtG6O3zb](https://tokopedia.link/AlLLtG6O3zb)

![WD SN520 2242](https://storage.wakhid.com/img/wakhidcom_thinkpad_t14_dual_storage_1.png)



## Proses Pemasangan NVME di ThinkPad T14 Gen 1

Proses pemasangan NVME di Slot WWAN ThinkPad T14 Gen 1 cukup mudah, Saya hanya perlu membuka Case bawah laptop dan memasangnya di Slot WWAN yang tersedia. Letaknya berdampingan persis bersebelahan dengan Slot NVME utama.

![Slot WWAN ThinkPad T14 Gen 1](https://storage.wakhid.com/img/wakhidcom_thinkpad_t14_dual_storage_2.png)


## NVME di Slot WWAN Terdeteksi
Setelah pemasangan selesai, Saya hidupkan laptop dan setelah login ke dalam OS Windows, hasilnya NVME di Slot WWAN terdeteksi dengan baik.

Setelah NVME terdeteksi di OS Windows, Saya mencoba melakukan Format NVME SN520 ini dan prosesnya bisa selesai dengan baik tanpa ada kendala. NVME bisa digunakan untuk menyimpan data.

![Dual Storage ThinkPad T14 Gen 1](https://storage.wakhid.com/img/wakhidcom_thinkpad_t14_dual_storage_3.png)

![Dual Storage ThinkPad T14 Gen 1](https://storage.wakhid.com/img/wakhidcom_thinkpad_t14_dual_storage_4.png)


## Ternyata Ada Pantangan (?)
Saya kira semua telah selesai, ternyata ada isu yang muncul. Meski bukan isu yang mengganggu, tapi Saya merasa ini perlu dituliskan juga.

**1. NVME di Slot WWAN hanya bisa terdeteksi bila laptop menyala setelah Shutdown**
Jadi, ketika kita selesai bekerja dan Shutdown laptop, maka saat laptop dihidupkan kembali, NVME di Slot WWAN akan terdeteksi dengan baik.

Namun, ketika laptop di Restart, maka saat laptop hidup kembali NVME di Slot WWAN tidak terdeteksi.

Solusinya, hanya perlu melakukan Shutdown dan hidupkan ulang laptopnya.


**2. NVME di Slot WWAN tidak terdeteksi di OS Linux dan Hackintosh**
Isu ini Saya temukan ketika Saya melakukan Instalasi Linux (Ubuntu/Fedora) dan Hackintosh. Setelah proses instalasi selesai NVME di Slot WWAN tidak terdeteksi sama sekali.

Saya belum sempat melakukan penelusuran lebih lanjut karena Saya harus segera menggunakan laptop ini untuk bekerja.

## Kesimpulan
Meski dual storage di ThinkPad T14 Gen 1 (Intel) ini tidak sempurna seperti pada ThinkPad T480/T480s, tetapi akhirnya Saya bisa mengetahui sejauh mana kompabilitas dual storage pada laptop ini.

Mungkin, bagi pembaca yang menggunakan OS Windows tidak risau dengan isu yang Saya sebutkan di atas. Sehingga layak untuk mempertimbangkan atau mencobanya.


