---
layout: post
title:  "Cara Instal SSL Let's Encrypt Nginx pada Centos 7"
author: wakhid
categories: [ centOS, Security, Server ]
image: "https://storage.wakhid.com/img/wakhidcom-cara-install-ssl-lets-encrypt-di-nginx-centos-7-000.png"
---

## Hasil Akhir
- Mendapatkan SSL Let's Encrypt secara gratis
- Menginstal SSL Let's Encrypt pada Nginx
- Membuat Cron untuk memperbarui SSL Let's Encrypt secara otomatis

## Menginstal Certbot
```bash
yum install python-certbot-nginx
```

## Mendapatkan Sertifikat SSL
Certbot menyediakan berbagai cara untuk mendapatkan sertifikat SSL melalui plugin, salah satunya adalah plugin Nginx yang digunakan pada catatan ini.

```bash
certbot --nginx -d namadomain.com -d www.namadomain.com
```
Perintah di atas untuk menjalankan certbot dengan plugin --nginx  dan -d untuk menentukan nama domain yang ingin kita buatkan SSL-nya.

Jika ini adalah pertama kalinya menjalankan certbot, pada proses selanjutnya akan diminta untuk memasukkan alamat email dan menyetujui persyaratan layanan. Setelah itu, certbot akan berkomunikasi dengan server Let's Encrypt untuk mendapatkan sertifikat SSL.

```bash
Enter email address (used for urgent renewal and security notices)
 (Enter 'c' to cancel): webmaster@wakhid.com
Please read the Terms of Service at
https://letsencrypt.org/documents/LE-SA-v1.2-November-15-2017.pdf. You must
agree in order to register with the ACME server. Do you agree?
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
(Y)es/(N)o: y
Would you be willing, once your first certificate is successfully issued, to
share your email address with the Electronic Frontier Foundation, a founding
partner of the Let's Encrypt project and the non-profit organization that
develops Certbot? We'd like to send you email about our work encrypting the web,
EFF news, campaigns, and ways to support digital freedom.
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
(Y)es/(N)o: n
Requesting a certificate for namadomain.com
Performing the following challenges:
http-01 challenge for namadomain.com
Waiting for verification...
Cleaning up challenges
Deploying Certificate to VirtualHost /etc/nginx/conf.d/namadomain.com.conf
Redirecting all traffic on port 80 to ssl in /etc/nginx/conf.d/namadomain.com.conf
Please choose whether or not to redirect HTTP traffic to HTTPS, removing HTTP access.
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
1: No redirect - Make no further changes to the webserver configuration.
2: Redirect - Make all requests redirect to secure HTTPS access. Choose this for
new sites, or if you're confident your site works on HTTPS. You can undo this
change by editing your web server's configuration.
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
Select the appropriate number [1-2] then [enter] (press 'c' to cancel):2
Jika berhasil, certbot akan memberikan pesan yang memberitahu bahwa proses berhasil dan di mana tempat sertifikat disimpan:

IMPORTANT NOTES:
 - Congratulations! Your certificate and chain have been saved at:
   /etc/letsencrypt/live/namadomain.com/fullchain.pem
   Your key file has been saved at:
   /etc/letsencrypt/live/namadomain.com/privkey.pem
   Your certificate will expire on 2022-06-26. To obtain a new or
   tweaked version of this certificate in the future, simply run
   certbot again with the "certonly" option. To non-interactively
   renew *all* of your certificates, run "certbot renew"
 - If you like Certbot, please consider supporting our work by:

   Donating to ISRG / Let's Encrypt:   https://letsencrypt.org/donate
   Donating to EFF:                    https://eff.org/donate-le
```

## Memperbarui Sertifikat SSL Let's Encrypt Secara Otomatis
Sertifikas Let's Encrypt hanya berlaku selama 90 hari. Manfaatkan service Cronjob atau Crontab di Centos 7 untuk menjalankan perintah memperbarui sertifikat SSL Let's Encrypt Secara Otomatis.

```bash
contab -e
```

Tambahkan baris perintah berikut di crontab untuk menjalankan perintah memperbarui sertifikat SSL Let's Encrypt pada jam 00:00 setiap hari.

```bash
0 0 * * * /usr/bin/certbot renew --quiet
```