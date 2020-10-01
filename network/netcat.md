# **Nmap**

[Netcat](http://netcat.sourceforge.net/)

## **Deskripsi Singkat**

_Netcat_ (atau biasanya lebih sering disebut sebagai _nc_) merupakan sebuah _tool_ yang digunakan untuk menerima atau bahkan mengirim data melalui protokol TCP/IP. Pada ranah keamanan jaringan, _nc_ memiliki peran besar pada tahap _post exploitation_. Yaitu pada fase ketika _attacker_ sudah berhasil melakukan proses eksploitasi dan mendapat _limited access_ di server. Secara umum, _nc_ sangat berfungsi untuk berbagai hal berikut :

   * Melakukan tes koneksi ke _service_ target.
   * Melihat informasi _banner_ dari sebuah _service_.
   * Membuat koneksi dari perangkat _user_ ke _server_, dan sebaliknya (_listening_ atau _connecting_).
   * Men-transfer sebuah file antara _user_ dan _server_

## **_Cheatsheet_**

_Connect_ ke _service_ di _host_ lain.
```sh
$ nc [ip] [port]
```

Melihat apakah bisa terkoneksi ke _service_ yang ada di _host_ lain.
```sh
$ nc -vz [ip] [port]
```

Membuka koneksi pada port tertentu pada perangkat sendiri.

Linux
```sh
$ nc -lvvp [port]
```
MacOS
```sh
$ nc -l [port]
```

_Download_ file.
```sh
$ nc [ip] [port] > out
```

_Upload_ file.
```sh
$ cat filename | nc [destip] [destport]
```