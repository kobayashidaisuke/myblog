web: vendor/bin/heroku-php-apache2 public/

<IfModule mod_rewrite.c>

    RewriteCond %{HTTP:X-Forwarded-Proto} =http [OR]
    RewriteCond %{HTTP:X-Forwarded-Proto} =""
    RewriteCond %{HTTPS} !=on
    RewriteRule ^ https://%{HTTP_HOST}%{REQUEST_URI} [L,R=301]

</IfModule>
