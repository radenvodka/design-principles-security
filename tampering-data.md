## Tampering Data

Untuk menghindari serangan ini yang jelas dibutuhkan sebuah filter.


Contoh kasus yang saya temukan : 

Sebuah website memiliki sebuah opsi (misal pembayaran) , struktur dalam database : 

database : kategori_bank 

id,name

1  | BCA
2  | BRI
3  | BNI 

lalu kita membuat sebuah permintaan dengan id 4 yang tentu saja tidak ada di dalam database. 
data di database berhasil di update namun terjadi error web ***Whoops, looks like something went wrong.***
celah ini bisa di kategorikan low atau bisa juga bisa medium , semua tergantung dampak (misal : menaikan user level lebih tinggi).


Untuk melakukan Patch :  

- Pengecekan pada database apakah kategori tersebut ada atau tidak.
