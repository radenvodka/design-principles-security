# CROS - Cross Origin Resource Sharing

Untuk pengujian Cross Origin Resource Sharing

#### Source code (cors vulnerable): 

```
<?php
if ($_SERVER['REQUEST_METHOD'] === 'OPTIONS') {
    header('Access-Control-Allow-Origin: *');
    header('Access-Control-Allow-Methods: POST, GET, DELETE, PUT, PATCH, OPTIONS');
    header('Access-Control-Allow-Headers: token, Content-Type');
    header('Access-Control-Max-Age: 1728000');
    header('Content-Length: 0');
    header('Content-Type: text/plain');
    die();
}

header('Access-Control-Allow-Origin: *');
header('Content-Type: application/json');

$ret = [
    'username' => 'radenvodka',
    'github' => 'https://github.com/radenvodka',
    'phone_number' => '0877123456789',
    'password' => '1337##days3771te',
];
print json_encode($ret);
?>
```

#### Source code (Patch : cors vulnerable): 

```
<?php

$origin = $_SERVER['HTTP_ORIGIN'];
$allowed_domains = [
    'https://cilegontech.com',
    'https://www.cilegontech.com',
    'https://www.bughunter-id.org',
];

if ($_SERVER['REQUEST_METHOD'] === 'OPTIONS') {
    if (in_array($origin, $allowed_domains)) {
        header('Access-Control-Allow-Origin: ' . $origin);
    }
    header('Access-Control-Allow-Methods: POST, GET, DELETE, PUT, PATCH, OPTIONS');
    header('Access-Control-Allow-Headers: token, Content-Type');
    header('Access-Control-Max-Age: 1728000');
    header('Content-Length: 0');
    header('Content-Type: text/plain');
    die();
}
if (in_array($origin, $allowed_domains)) {
    header('Access-Control-Allow-Origin: ' . $origin);
}
header('Content-Type: application/json');

$ret = [
    'username' => 'radenvodka',
    'github' => 'https://github.com/radenvodka',
    'phone_number' => '0877123456789',
    'password' => '1337##days3771te',
];
print json_encode($ret);
?>
```

#### Test Cors:

- https://www.test-cors.org

Using Fetch : 
```
fetch('https://example.com/users')
.then(response=>response.json())
.then(data=>{ console.log(data); })
```

Using XHR  : 
```
var createCORSRequest = function(method, url) {
  var xhr = new XMLHttpRequest();
  if ("withCredentials" in xhr) {
    // Most browsers.
    xhr.open(method, url, true);
  } else if (typeof XDomainRequest != "undefined") {
    // IE8 & IE9
    xhr = new XDomainRequest();
    xhr.open(method, url);
  } else {
    // CORS not supported.
    xhr = null;
  }
  return xhr;
};

var url = 'https://cilegontech.com/cors.php';
var method = 'GET';
var xhr = createCORSRequest(method, url);

xhr.onload = function() {
  alert(xhr.response);
};

xhr.onerror = function() {
  alert("BLOCKED");
};

xhr.send();
```

