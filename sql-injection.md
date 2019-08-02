# SQL injection

serangan ini biasanya memanfaatkan sebuah celah dimana kurangnya validasi sebuah web.
biasanya yang saya lakukan melakukan validasi sesuai dengan jenis tipe datanya. 

jika tipenya numeric : 

```
if (filter_var($int, FILTER_VALIDATE_INT)) {
    echo("Variable is an integer");
} else {
    echo("Variable is not an integer");
}
```

selain itu biasanya saya tambahkan preg_replace untuk menghilangkan karakter yang bukan numeric.

```
preg_replace('/\D/', '', int)
```

atau pun biasanya saya menambahkan object di dalam class : 

```
 function filter_spesial($string) {
       $string = str_replace(' ', '', $string); // Replaces all spaces with hyphens.
       return preg_replace('/[^A-Za-z0-9\-]/', '', $string); // Removes special chars.
    }
    function filter_data($data) {
        $data = htmlspecialchars(trim(htmlentities(strip_tags($data))));
        if (get_magic_quotes_gpc())
            $data = stripslashes($data);
            $data = $this->db->real_escape_string($data);
        return $data;
    }
    function filter_number($num){
        return preg_replace('/\D/', '', $num);
    }
    
 ```
