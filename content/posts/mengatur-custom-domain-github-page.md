+++
title = "Mengatur Custom Domain Github Page"
description = "Iseng-iseng nyari domain murah, ternyata nemu nih domain dengan harga 10k. Karena cocok dengan kantong ana, langsung aja ana coba beli untuk 2 tahun (kurangnya untuk pembayaran via virtual account,  pake biaya lagi ndak kaya tetangga yang gratis) dengan total 25k."
date = "2020-03-25"
tags = ["domain","github page","custom domain   "]
categories = ["Teknologi"]
author = "Triyadi"
lokasi = "Banyumas"
image = "https://images.unsplash.com/photo-1522542550221-31fd19575a2d"
comment = "aktif"
+++

Iseng-iseng nyari domain murah, ternyata nemu nih domain dengan harga 10k. Karena cocok dengan kantong ana, langsung aja ana coba beli untuk 2 tahun (kurangnya untuk pembayaran via virtual account,  pake biaya lagi ndak kaya tetangga yang gratis) dengan total 25k.Kebetulan ana sedang seneng dengan github page, jadi sekalian deh buat bikin custom domain dengan domain abuuwais.my.id.

Ok langsung saja, pertama pastikan antum beli domainnya dulu (afwan ana ndak berani nyebut nama providernya kerna takut iklan gratis atau malah salah paham, jadi kalo butuh info providernya teman-teman bisa chat ana via kontak yang sudah disediakan).

#### Bahan yang dibutuhkan
    1. Lumbung/Repository Github untuk membuat github page (namaakun.github.io)
    2. Domain yang akan menjadi custom domain (namadomain.id)
    3. Cloudflare

#### 1. Membuat account dan menambahkan situs kita pada cloudflare


Jika antum belum memiliki akun cloudflare, maka buat terlebih dahulu dan jika sudah maka langsung login saja. Setelah login, maka pilih menu **add site**, dan masukan alamat/domain antum misal namadomain.id.

Selanjutnya, antum akan diberi pilihan paket dan karena ana seneng yang gratis jadi ana pilih **Free** dan klik **"confirm plan"** tunggu cloudflare mencari domain antum. 

Selanjutnya, antum diperintahkan untuk menambah **DNS record** baru. Buat 2 DNS baru dengan type **A**, name **nama custom domain antum**, dan TTL **auto**, dengan Content sebagai berikut :

    > 192.30.252.153
    > 192.30.252.154
    
Dan buat 1 DNS record dengan type **CNAME**, name **www**, TTL **auto** dan Content **alamat github page** (namaakun.github.io), setelah itu klik **Continue**, jika berhasil maka cloudflare akan menyarankan untuk mengganti nameserver bawaan penyedia domain menjadi nameserver milik cloudflare.

Selanjutnya, kita akan mengatur **Security and Speed** pada cloudflare. Pilih **Full** pada **encryption mode**, Aktifkan atau switch **On** pada **Always Use HTTPS** lalu klik tombol **done**.

#### 2. Mengatur nameserver pada Custom Domain

Kembali ke laman client pada provider domain antum, pilih menu **My Domain**, pilih domain yang akan diatur nameservernya, dan pilih menu **Manage Nameservers**. Selanjutnya, pilih **Use custom nameservers** dan masukan nameservers yang disarankan oleh **Cloudflare** tadi, klik **Change Nameservers**.

#### 3. Pengaturan custom domain pada repo github

Masuk ke halaman github dan pilih repo yang akan dijadikan laman/github page. Pilih menu **Settings**, gulir laman ke bawah dan cari **Github Pages** dan pada **custom domain**, masukan custom domain yang sudah antum beli tadi contoh **namadomain.id** dan klik tombol **save**.

Setelah tahapan-tahapan tadi kita lakukan, mari kita kunjungi laman github kita dan jika redirect ke custom domain, berarti pengaturan custom domain di laman github antum sudah berhasil dan jika tidak coba tenang dan baca ulang dan pahami setiap tahap demi tahapnya hehehe...

Semoga bemanfaat...


