+++
title = "Membuat Fungsi Di Bahasa R"
date = 2018-06-06T20:28:52+02:00
draft = false

# Tags and categories
# For example, use `tags = []` for no tags, or the form `tags = ["A Tag", "Another Tag"]` for one or more tags.
tags = ["fungsi"]
categories = ["R"]

# Featured image
# Place your image in the `static/img/` folder and reference its filename below, e.g. `image = "example.jpg"`.
# Use `caption` to display an image caption.
#   Markdown linking is allowed, e.g. `caption = "[Image credit](http://example.org)"`.
# Set `preview` to `false` to disable the thumbnail in listings.
[header]
image = "/headers/pexels-fungsi.jpeg"
caption = "Kredit gambar: [**pexels.com**](https://www.pexels.com/photo/office-working-app-computer-97077/)"
preview = true

+++

# Prinsip
Salah satu hal yang menyenangkan dari bahasa R adalah transisi dari pengguna menjadi pemrogram dapat dilakukan dengan cukup mudah. Hal dasar yang dilakukan seorang pemrogram R adalah membuat fungsi. Fungsi merupakan komponen terpenting dan unggulan dari R yang merupakan bahasa pemrograman fungsional (*functional programming language*).

> Jika Anda harus menulis dan menjalakkan suatu perintah lebih dari dua kali, maka buatlah suatu fungsi.

Membuat fungsi memiliki beberapa manfaat, diantaranya:

* Menghindari salin-tempel kode secara berulang.
* Membuat kode menjadi lebih jelas dengan cara memberikan nama fungsi.
* Lebih mudah untuk melakukan perbaikan atau perubahan kode.
* Menghindari kesalahan penulisan kode dan mengurangi panjang skrip kode secara keseluruhan.

# Struktur
Struktur fungsi di bahasa R terdiri atas beberapa komponen, sebagai berikut:

1. Nama fungsi. Nama fungsi sebaiknya singkat, jelas, dan dapat mendeskripsikan pengolahan yang dilakukan. Nama fungsi ditentukan sebelum tanda `<-`.
2. Argumen fungsi. Argumen dapat berupa masukan data yang akan diolah serta pengaturan lainnya yang diperlukan. Argumen fungsi terletak dalam bagian `function(...)`. 
3. Badan fungsi. Ini merupakan bagian terpenting dimana suatu pengolahan masukan data dilakukan untuk menghasilkan keluaran. Badan fungsi terletak dalam bagian `{...}`

Berikut merupakan struktur umum dari sebuah fungsi:

```r
nama <- function(argumen1, argumen2, ...){
   argumen1 + argumen2
}
```

atau

```
nama <- function(argumen1, argumen2, ...){
   hasil <- argumen1 + argumen2
   return(hasil)
}
```

Terdapat perbedaan antara struktur pertama dan kedua, yaitu pada penggunaan fungsi `return()`. Fungsi `return()` berguna untuk menentukan keluaran fungsi secara eksplisit. Meskipun keluaran dari kedua bentuk struktur fungsi diatas adalah sama, disarankan untuk menggunakan fungsi `return()` secara eksplisit untuk menghindari galat (*error*).

# Cara memanggil fungsi
Sebelum dapat digunakan, suatu fungsi harus dipanggil terlebih dahulu sehingga tersedia di *Global Environment*. Cara memanggil fungsi dapat dilakukan dengan cara sebagai berikut:

1. Fungsi dapat dipanggil secara langsung dengan cara menjalankan fungsi tersebut secara eksplisit. Misalnya anda menuliskan kode fungsi `jumlah` pada skrip `fungsi_baru.R`, maka anda dapat menjalankan kode dalam `fungsi_baru.R` sehingga fungsi `jumlah` menjadi tersedia di *Global Environment*.
2. Fungsi dapat dipanggil secara implisit dengan cara menyisipkan dokumen fungsi pada `source()`. Pertama, anda dapat menuliskan kode fungsi tersebut dalam skrip (contoh: `fungsi_baru.R`) kemudian menyimpannya dalam suatu direktori (contoh: ~/Dokumen/R/Fungsi). Kemudian, sisipkan perintah `source("~/Dokumen/R/Fungsi/fungsi_baru.R")` pada bagian awal skrip utama yang akan anda gunakan untuk bekerja. Maka fungsi `jumlah` akan tersedia di *Global Environment* dan dapat segera digunakan.

Jika anda membuat banyak fungsi, maka sebaiknya simpan masing-masing fungsi tersebut dalam dokumen skrip secara terpisah (contoh: jumlah.R, reskala.R, normalisasi.R, dan seterusnya). Hal ini bertujuan untuk mempermudah jika ada perubahan atau perbaikan kode yang harus dilakukan pada suatu fungsi tertentu. Apabila anda menyimpan skrip fungsi tersebut di dalam satu direktori yang sama, maka anda dapat memanggil semua fungsi tersebut secara sekaligus dengan cara menyisipkan perintah:

```
daftar_fungsi <- list.files("~/Dokumen/R/Fungsi", pattern = "\\.R$", full.names = TRUE)
invisible(lapply(daftar_fungsi, source))
```

Demikian merupakan cara membuat fungsi pada bahasa R. Anda dapat membuat dan menyesuaikan fungsi sesuai dengan kebutuhan analisis yang dilakukan. Selamat mencoba!
