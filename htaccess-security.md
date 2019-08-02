# htaccess - Security default settings

melakukan beberapa tindakan untuk meminimalkan resiko keamanan.

Apa yang ada didalam konfigurasi .httaccess

- caching
- block xss
- block Frame

#### Source code (.htaccess): 

```
# Turn on Expires and set default expires to 3 days
ExpiresActive On
ExpiresDefault A259200

# Set up caching on media files for 1 month
<FilesMatch "\.(ico|gif|jpg|jpeg|png|flv|pdf|swf|mov|mp3|wmv|ppt)$">
  ExpiresDefault A2419200
  Header append Cache-Control "public"
</FilesMatch>
# Set up 2 Hour caching on commonly updated files
<FilesMatch "\.(xml|txt|js|css)$">
  ExpiresDefault A7200
  Header append Cache-Control "private, must-revalidate"
</FilesMatch>

# Force no caching for dynamic files
<FilesMatch "\.(php|cgi|pl|htm|html|php)$">
  ExpiresDefault A0
  Header set Cache-Control "no-store, no-cache, must-revalidate, max-age=0"
  Header set Pragma "no-cache"
</FilesMatch>

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
