+++
title = "Memasang Postgresql di ubuntu 18.04"
description = "Berikut merupakan cara singkat, bagaimana memasang Postgresql pada ubuntu 18.04Ketik perintah berikut pada terminal"
date = "2020-03-22"
tags = ["ubuntu","postgresql"]
categories = ["Teknologi"]
author = "Triyadi"
lokasi = "Banyumas"
image = "https://miro.medium.com/max/8640/0*jD8Zg8_87AA_3o2w"
comment = "aktif"
+++

Berikut merupakan cara singkat, bagaimana memasang Postgresql pada ubuntu 18.04

Ketik perintah berikut pada terminal

    sudo apt install postgresql postgresql-contrib

jalakan Postgresql dengan mengetikan perintah berikut

    sudo service postgresql start

<!--more-->
Masuk dengan perintah

    sudo -i -u postgres psql

Jika di terminal keluar " postgres=# " maka pemasangan berhasil.

Selanjutnya, antum bisa mencoba dengan menggunakan dbeaver atau adminer dengan catatan, jika antum menggunakan adminer, pastikan di komputer sudah terpasang webserver khususnya php.

## Ketemu Masalah
![Error pada adminer](/static/postimages/adminer.png)

Setelah pemasangan postgresql berhasil, ternyata postgresql belum bisa diakses dengan nyaman via database manager seperti DBeaver ataupun Adminer dengan keluar pesan seperti berikut.

```
Unable to connect to PostgreSQL server: FATAL: Peer authentication failed for user "postgres"
```

Cara mengatasinya sangatlah mudah, yaitu dengan memberikan hak akses tanpa login, terus bikin password untuk akun postgres selanjutnya login ulang deh (pasti bingung kan?)

### Berikut caranya :

Pertama, buka dan sunting file pg_hba.conf dengan mengetikan perintah

    sudo nano /etc/postgresql/10/main/pg_hba.conf

Cari kode berikut dan rubah

Dari
```
# Database administrative login by Unix domain socket
local   all             postgres                peer
```

Menjadi

```
# Database administrative login by Unix domain socket
local   all             postgres                trust
```

Simpan dan restart Postgresql dengan mengetik perintah

    sudo service postgresql restart

Selanjutnya, login dengan mengetikan perintah berikut
    
    psql -U postgres

Lalu, atur password baru dengan menggunakan perintah ini

    ALTER USER postgres with password ‘password-antum’;

Setelah itu, kembali buka dan sunting file pg_hba.conf dengan mengetikan perintah

    sudo nano /etc/postgresql/10/main/pg_hba.conf

Cari kode berikut dan rubah

Dari
```
# Database administrative login by Unix domain socket
local   all             postgres                trust
```
Menjadi
```
# Database administrative login by Unix domain socket
local   all             postgres                  md5
```
Simpan dan restart Postgresql dengan mengetik perintah

    sudo service postgresql restart

Sekarang kita coba dengan membuka postgresql dengan menggunakan adminer and tadaaa.

![Test pake adminer](/static/postimages/adminer.gif)

Semoga bermanfaat.