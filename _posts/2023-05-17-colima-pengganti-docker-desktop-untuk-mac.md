---
title: Colima, Pengganti Docker Desktop yang Efisien untuk Pengguna Mac
author: wakhid
date: 2023-05-17 12:32:00 -0500
categories: [Blogging, Docker]
tags: [Docker, macOS]
---

Kali ini Saya sedang belajar Docker. Sebagai pengguna Mac, Docker Desktop mungkin telah menjadi pilihan utama selama ini karena kemudahannya. Tetapi Saya merasakan bahwa Docker Desktop menggunakan resources yang cukup besar sehingga Saya tergerak untuk mencari alternatif yang menarik sebagai pengganti Docker Desktop.

Akhirnya, Saya mengenal [**Colima**](https://github.com/abiosoft/colima/). 

Colima, sebuah aplikasi yang dapat menggantikan Docker Desktop di platform Mac dengan efisiensi dan kemudahan penggunaan yang tinggi.

## Pengenalan tentang Colima
Colima adalah sebuah alat pengelola container yang dikembangkan untuk pengguna Mac (dan Linux). Dikembangkan oleh tim pengembang yang sama yang menciptakan Laravel Valet, Colima menawarkan solusi yang sederhana dan efisien untuk menjalankan container di lingkungan pengembangan lokal.

## Keunggulan Colima
Colima dirancang agar lebih hemat penggunaan sumber daya komputer, sehingga tidak membebani performa sistem Mac Saya seperti yang mungkin terjadi pada Docker Desktop.

Keunggulan lainnya :

- Intel and M1 Macs support
- Simple CLI interface
- Docker and Containerd support
- Port Forwarding
- Volume mounts
- Kubernetes
- Multiple instances

## Instalasi Docker CLI Dan Colima Dengan HomeBrew
  Di sini Saya akan melakukan instalasi Docker CLI, Docker Compose dan Colima menggunakan HomeBrew dengan satu baris perintah :

```
brew install docker docker-compose colima
```

Setelah proses instalasi selesai, maka Saya bisa menggunakan perintah Docker CLI melalui Terminal :

```
❯ docker --version
Docker version 23.0.6, build ef23cbc431
```

```
❯ docker-compose --version
Docker Compose version 2.17.3
```

```
❯ colima --version
colima version 0.5.4
```

Tetapi, Saya belum bisa bekerja menggunakan Docker Container :

```
❯ docker run hello-world
docker: Cannot connect to the Docker daemon at unix:///var/run/docker.sock. Is the docker daemon running?.
See 'docker run --help'.
```


## Menjalankan Colima

Docker Container belum bisa dipergunakan karena Docker daemon belum running, Saya harus menjalankan Colima dengan perintah :

```
colima start
```

Logs :
```
❯ colima start
INFO[0000] starting colima
INFO[0000] runtime: docker
INFO[0000] preparing network ...                         context=vm
INFO[0039] provisioning ...                              context=docker
INFO[0040] starting ...                                  context=docker
INFO[0045] done
```

Perintah tersebut akan menjalankan Docker Daemon di dalam VM yang dibuat oleh Colima dan juga mengkonfigurasi Docker CLI pada Host (Mac). 

Setelahnya, pengoperasian Docker pada macOS akan sama saja seperti kita menggunakan Docker Desktop dan semua perintah Dokcer CLI bisa digunakan juga.


## Menjalankan Docker Container

Sebagai pengujian, Saya akan membuat Docker Container bernama hello-world :

```
docker run hello-world
```

Logs :
```
❯ docker run hello-world
Unable to find image 'hello-world:latest' locally
latest: Pulling from library/hello-world
719385e32844: Pull complete
Digest: sha256:fc6cf906cbfa013e80938cdf0bb199fbdbb86d6e3e013783e5a766f50f5dbce0
Status: Downloaded newer image for hello-world:latest

Hello from Docker!
This message shows that your installation appears to be working correctly.

To generate this message, Docker took the following steps:
 1. The Docker client contacted the Docker daemon.
 2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
    (amd64)
 3. The Docker daemon created a new container from that image which runs the
    executable that produces the output you are currently reading.
 4. The Docker daemon streamed that output to the Docker client, which sent it
    to your terminal.

To try something more ambitious, you can run an Ubuntu container with:
 $ docker run -it ubuntu bash

Share images, automate workflows, and more with a free Docker ID:
 https://hub.docker.com/

For more examples and ideas, visit:
 https://docs.docker.com/get-started/
```

## Kesimpulan Saya
Colima adalah alternatif yang menarik untuk Docker Desktop bagi pengguna Mac. Dengan keunggulan penggunaan sumber daya yang lebih efisien dan instalasi yang mudah. 

Colima menyediakan solusi pengelolaan kontainer yang efisien dan mudah digunakan untuk pengembangan aplikasi di lingkungan lokal. Jika Anda mencari alternatif untuk Docker Desktop di Mac, Colima dapat menjadi pilihan yang tepat.

Selain itu, Saya masih perlu mempelajari Colima ini lebih lanjut lagi karena Saya meyakini masih ada banyak hal menarik lainnya.


