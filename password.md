## Password

Kita ketahui bahwa MD5 bukan lah pilihan yang tepat untuk sebuah web agar isinya tidak diketahui orang lain.
sudah banyak sekali key yang ditemukan.

Berikut ini yang yang sangat disarankan untuk mengenkripsi password, karena sulit didekripsi atau di-crack.

```
<?php echo password_hash("PetaniKode", PASSWORD_DEFAULT); ?>
```

```
<?php echo crypt("petanikode", "garam"); ?>
```

```
<?php echo hash("md5", "petanikode"); ?>
```

bisa baca di https://www.petanikode.com/php-fungsi-enkripsi/
