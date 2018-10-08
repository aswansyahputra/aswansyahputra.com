+++
title = "Membuat Situs Web Melalui Rstudio"
date = 2018-06-06T20:21:30+02:00
draft = false

# Authors. Comma separated list, e.g. `["Bob Smith", "David Jones"]`.
authors = ["Muhammad Aswan Syahputra"]

# Tags and categories
# For example, use `tags = []` for no tags, or the form `tags = ["A Tag", "Another Tag"]` for one or more tags.
tags = ["blogdown"]
categories = ["R", "RStudio"]

# Featured image
# Place your image in the `static/img/` folder and reference its filename below, e.g. `image = "example.jpg"`.
# Use `caption` to display an image caption.
#   Markdown linking is allowed, e.g. `caption = "[Image credit](http://example.org)"`.
# Set `preview` to `false` to disable the thumbnail in listings.
[header]
image = "/headers/pexels-situs-web.jpeg"
caption = "Kredit gambar: [**pexels.com**](https://www.pexels.com/photo/computer-keyboard-laptop-screen-109371/)"
preview = true

+++

# Pengantar
Dalam tulisan ini saya akan menjelaskan bagaimana cara membuat situs web dengan menggunakan RStudio. RStudio merupakan *Integrated Development Environment* (IDE) yang ditujukan khusus untuk bahasa R. Bahasan mengenai RStudio dan bahasa R akan saya sampaikan dalam tulisan lain. Sebagai informasi, situs web [aswansyahputra.com](https://aswansyahputra.com) dibuat dengan menggunakan metode ini.

Terdapat beberapa hal yang harus dipenuhi sebelum membuat situs web menggunakan metode ini, yaitu:

1. Aplikasi [R](cran.r-project.com) sudah terpasang
2. Aplikasi [RStudio](rstudio.com) sudah terpasang
3. Aplikasi [git](https://git-scm.com/) sudah terpasang
4. Membuat akun di  [GitHub](http://github.com)
5. Membuat akun di [Netlify](http://netlify.com)

# Pembuatan situs web
Setelah semua prasyarat tersebut dipenuhi, selanjutnya kita akan melakukan tahapan pembuatan situs web yang saya bagi dalam beberapa bagian.

## Memasang paket `blogdown`
Pertama kita harus memasang paket `blogdown` pada aplikasi `R`. Pada saat tulisan ini dibuat, versi terbaru `blogdown` adalah 0.5 dan  versi terbaru `R` adalah 3.43. Anda dapat memasang paket tersebut dengan menggunakan RStudio maupun GUI dari `R`, namun dalam tulisan ini pemasangan paket dilakukan mengggunakan RStudio.

Pemasangan paket `blogdown` dilakukan dengan cara mengeksekusi perintah berikut pada konsol RStudio:

```
install.packages("blogdown")
```
atau
```
if(!require("blogdown")){
  install.packages("blogdown")
}
```
atau dengan memilih menu '*Tools - Install Packages..*' kemudian isi bagian '*Packages (separate multiple with space or comma):*' dengan "blogdown" (tanpa tanda petik) dan klik 'Install'.

Anda dapat memeriksa apakah paket tersebut telah terpasang atau belum dengan cara mengeksekusi:
```
# Fungsi untuk memeriksa pemasangan paket
is.installed <- function(paket){
    is.element(paket, installed.packages()[,1])
} 

# Periksa apakah paket 'blogdown' telah terpasang
is.installed("blogdown")
```
Jika keluaran dari fungsi tersebut adalah `TRUE`, maka paket `blogdown` telah terpasang dengan baik pada `R`.

Kemudian lakukan instalasi Hugo dengan mengeksekusi perintah:
```
blogdown::install_hugo()
```

## Membuat proyek situs web
Selanjutnya kita membuat proyek `R` melalui RStudio, khususnya adalah proyek situs web menggunakan `blogdown`. Pada Rstudio, pilih menu '*File - New Project - Create New Directory* dan klik bagian '*Website using Blogdown*'. Silakan isi nama proyek dan lokasi penyimpanan pada komputer. Contoh pengisian seperti dibawah ini:

![](/img/post/proyek-situs-web.png)

Setelah klik '*Create Project*', pada konsol eksekusi perintah:
```
blogdown:::serve_site()
```
maka contoh situs web akan muncul pada *Viewer pane*. Sebagai catatan, pada contoh ini tema situs web yang digunakan adalah *Lithium Theme*. Anda dapat menyesuaikan atau mengganti tema situs sesuai preferensi dan melakukan pengaturan dengan cara mengubah isi dokumen config.toml.

![](/img/post/contoh-situs-web.png)


## Membuat tulisan
Anda dapat membuat tulisan dengan cara klik menu '*Addins*' dan pilih '*New Post*'. Kemudian akan muncul jendela untuk mengisi judul tulisan, nama penulis, kategori, label tulisan, dan lain lain. Anda dapat menggunakan ekstensi dokumen .md, .Rmd, dan .Rmarkdown untuk tulisan tersebut. Perbedaan mendasar antara ekstensi tersebut adalah fungsi R tidak dapat dijalankan dalam dokumen dengan ekestensi .md. 

Tayangan langsung akan muncul pada *Viewer pane* setelah anda menyimpan dokumen tulisan atau melalui perintah ```blogdown:::serve_site()```.

Sampai tahap ini Anda telah berhasil membuat situs web. Namun, situs web ini hanya berjalan secara lokal di komputer Anda. Tahap selanjutnya yang harus dilakukan adalah mengungah situs web Anda tersebut ke internet.

## Mengunggah situs web ke internet
Git dan GitHub akan digunakan untuk menggunggah situs web yang telah dibuat secara lokal ke internet. Sebelum melakukan tahap ini, pastikan Anda telah memasang Git pada komputer dan membuat akun GitHub. Pertama, Anda harus membuat repositori kosong pada akun GitHub. Dalam tulisan ini, saya membuat repositori kosong pada GitHub dengan nama "situs-web".

![](/img/post/github-situs-web.png)

Kemudian pada jendela RStudio tempat proyek situs web disimpan, klik '*Tools-Shell...*' dan eksekusi perintah:

```
git init
git add .
git commit -m "unggah situs web"
git remote add origin https://github.com/aswansyahputra/situs-web.git
git push -u origin master
```
*Catatan: silakan sesuaikan alamat repositori milik Anda*

Setelah repositori GitHub Anda terisi dengan dokumen lokal situs web, selanjutnya silakan Anda buka akun [Netlify](https://netlify.com) untuk menayangkan (*deploy*) situs web di internet. Anda dapat melakukan masuk atau melakukan registrasi dengan menggunakan akun GitHub yang dimiliki.

Pada laman pertama, silakan pilih '*New site from Git*'. Kemudian klik GitHub pada bagian '*Continous Deployment*', pilih repositori "situs-web", dan melakukan pengaturan seperti sebagai berikut:

![](/img/post/pengaturan-situs-web.png)

Setelah semua pengaturan sesuai, klik *Deploy site*.

Netlify akan memberikan nama domain secara acak, misalnya dalam contoh ini adalah "suspicious-nightingale-fb9365.netlify.com". Anda dapat mengganti nama domain tersebut dengan cara klik '*Domain setting*' dan memilih menu sebagai berikut:

![](/img/post/domain-situs-web.png)

Selamat! Kini situs web anda telah tayang di internet. Jangan lupa untuk mengubah 'baseurl' pada dokumen config.toml dengan 'nama-domain.netlify.com/'. Setelah Anda melakukan konfigurasi situs web atau membuat tulisan baru, lakukan '*Add, commit, push*' agar perubahan yang dilakukan dapat diolah oleh Netlify.

Anda dapat mengakses kode sumber di repositori [ini](https://github.com/aswansyahputra/situs-web) dan melihat contoh situs web yang dibuat dapat diakses pada tautan [berikut](https://contoh-situs-web.netlify.com/).

## Mengganti nama domain situs web (opsional)
Anda dapat mengganti alamat situs web dengan nama domain yang dimiliki dengan cara memilih '*Add custom domain*'. Netlify memiliki dan menawarkan **DNS Zone** untuk melakukan pengaturan DNS. Anda dapat menggunakan DNS dari Netlify dengan cara mengganti *nameservers* domain Anda dengan *nameservers* yang diberikan Netlify. Sebagai tambahan, Anda juga dapat mengaktifkan fitur *https* pada domain Anda tersebut.

Demikian tahapan membuat situs web dengan mengintegrasikan RStudio, GitHub, dan Netlify. Sebagai catatan, tahapan di atas bukan merupakan satu-satunya cara yang dapat dilakukan. Anda dapat melakukan eksperimen untuk mendapatkan alur kerja yang sesuai. Selamat mencoba!
