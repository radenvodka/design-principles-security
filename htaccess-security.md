# htaccess - Security default settings

melakukan beberapa tindakan untuk meminimalkan resiko keamanan

#### Source code (cors vulnerable): 

```
<IfModule mod_headers.c>
    #Header set Set-Cookie HttpOnly;Secure
    Header set x-recruiting "You woot bug ? report admin@example.com"
    Header set X-Frame-Options DENY
    Header set X-XSS-Protection "1; mode=block"
	  Header always set X-Frame-Options "SAMEORIGIN"
	  Header always set X-Content-Type-Options "nosniff"
	  #Header always set Referrer-Policy "same-origin"
	  #Header always set Feature-Policy "microphone 'none'; payment 'none'; sync-xhr 'self' https://example.org"
</IfModule>
```
