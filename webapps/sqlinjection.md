# **SQL Injection**

[SQL Injection](https://www.owasp.org/index.php/SQL_Injection)

## **Deskripsi Singkat**

_SQL Injection_ (selanjutnya akan ditulis dengan _sqli_) merupakan kerentanan yang memungkinkan _attacker_ bermain-main pada struktur _database_ pada sebuah aplikasi. Melalui celah ini, _attacker_ bisa memanipulasi _query_ yang akan dikirimkan ke server. Dampak umum yang ditimbulkan lewat serangan _sqli_ adalah :

   * Melihat data-data yang ada pada _database_ aplikasi.
   * Melakukan transaksi data pada _database_ aplikasi (menambah data, merubah data, menghapus data).
   * Membaca isi dari _local file_ pada target.
   * Membuat file baru pada target.

## **Penyebab terjadinya SQL Injection**

Penyebab terjadinya serangan _sqli_ adalah adanya data inputan _user_ yang tidak divalidasi dan difilterisasi dengan baik. Sehingga semua inputan _user_ akan diterima dan diproses oleh server meskipun inputan tersebut berisi _query_ yang berbahaya untuk server. Contoh sederhana terjadinya serangan _sqli_ adalah :

```php
$id = $_GET["username"];
$sql = "SELECT * FROM user WHERE username = " + "'" + $id "'";
```

Apabila _user_ menginputkan `' or a=a-- -`, maka _query_ akan menjadi :

```sql
SELECT * FROM user WHERE username = '' or a=a-- -;
```

Maka ketika _query_ tersebut dijalankan akan menghasilkan nilai **true** tanpa kita perlu tahu data _username_ yang valid. Proses inilah yang dinamakan _SQL Injection_.

## **Jenis-jenis SQL Injection**

### **Union Based SQL Injection**

_Union based SQL Injection_ adalah jenis _sqli_ yang memungkinkan _attacker_ untuk menggabungkan _evil query_ dan _original query_ milik aplikasi itu sendiri dengan menggunakan command `UNION SELECT`. Hasil dari kedua _query_ tersebut akan ditampilkan pada aplikasi.

### **Error Based SQL Injection**

_Error based SQL Injection_ adalah jenis _sqli_ yang hasilnya akan muncul pada pesan _error_ pada suatu aplikasi/_query_s.

### **Blind Based SQL Injection**

_Blind based SQL Injection_ adalah jenis _sqli_ yang hasil _query injection_-nya tidak ditampilkan pada respon aplikasi. Ketika hendak menampilkan data hasil _injection_, biasanya digunakan acuan waktu dari respon aplikasi (_time based_).

## **_Cheatsheet_**

```txt
' or a=a-- -
' or' '='-- -
' and a=a-- -
' and true-- -
```