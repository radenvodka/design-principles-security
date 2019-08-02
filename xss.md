# XSS

XSS merupakan singkatan yang digunakan untuk istilah cross site scripting. XSS merupakan salah satu jenis serangan injeksi code (code injection attack).

Untuk melakukan Patch XSS , kalian bisa mengunakan .htaccess (X-XSS-Protection) untuk perlindungan awal lalu di susul dengan beberapa filter karena jika hanya mengunakan .htaccess tidak menuntut kemungkinan bakal bisa di bypass.

Jika mengunakan Codeigniter (CI) : $config 'global_xss_filtering' = false jadikan true. 
Jika mengunakan php native :  htmlentities($data, ENT_QUOTES, 'UTF-8');


lebih baik untuk melakukan patching sebuah kerentanan walau pun kecil kita mengunakan perindungan berlapis-lapis.
