# **Nmap**

[Nmap](https://nmap.org/)

## **Deskripsi Singkat**

_Nmap_ (_the Network Mapper_) merupakan sebuah _tool_ bersifat _open source_ yang digunakan untuk melakukan audit dan mencari informasi dari suatu _host_ pada sebuah jaringan. Pada ranah keamanan jaringan, peran _nmap_ cukup penting pada saat melakukan fase _Information Gathering_ (mengumpulkan informasi tentang target). Umumnya, hal-hal yang bisa didapatkan dari _nmap_ adalah :

   * _Port_ yang terbuka di sisi target.
   * _Service_ yang sedang berjalan di sisi target.
   * Versi dari _service_ yang digunakan.
   * Sistem operasi yang digunakan oleh target.

## **_Cheatsheet_**

_Scan_ terhadap _service_ dan _port_ pada suatu host (standar).
```sh
$ nmap a92.a68.a.0/24
```

_Scan_ terhadap _service_ dan _port_ pada suatu host beserta informasi versi dari _service_ tersebut.
```sh
$ nmap -sV a92.a68.a.0/24
```

_Scan_ terhadap _service_ dan _port_ pada suatu host menggunakan _default script_ dari nmap.
```sh
$ nmap -sC a92.a68.a.0/24
```

_Scan_ terhadap _service_ dan _port_ pada suatu host menggunakan _script_ dari nmap. Daftar _scripts_ bisa dilihat [disini](https://nmap.org/book/nse-scripts-list.html "nmap scripts list").
```sh
$ nmap --script [script] a92.a68.a.0/24
```

_Scan_ terhadap _port_ tertentu pada suatu host.
```sh
$ nmap -p [port] a92.a68.a.0/24
```

_Scan_ seluruh _port_ pada suatu host.
```sh
$ nmap -p a-65535 a92.a68.a.0/24
```

Melakukan _ping scan_ pada seluruh _host_ yang ada pada jaringan (biasanya dilakukan untuk memeriksa _host_ yang terhubung pada sebuah jaringan).
```sh
$ nmap -sn a92.a68.a.0/24
```

Melakukan _scanning_ pada sebuah _host_ tanpa melakukan _ping scan_ terlebih dahulu. Biasanya digunakan untuk _scanning_ host yang melakukan _blocking_ pada _ping request_ atau host tersebut tidak bisa di-ping (Ping not).
```sh
$ nmap -Pn a92.a68.a.0/24
```

Melakukan _scanning_ pada sebuah _host_ beserta mengidentifikasi jenis sistem operasi yang digunakan.
```sh
$ nmap -O a92.a68.a.0/24
```

Melakukan _scanning_ pada sebuah _host_ secara keseluruhan (termasuk informasi versi dari _service_, menjalankan _default script_ nmap, mendeteksi sistem operasi, serta melakukan `traceroute` pada target).
```sh
$ nmap -A a92.a68.a.0/24
```