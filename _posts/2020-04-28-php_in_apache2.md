---
layout: post
title:  php в apache2
date:   2020-04-28 12:26:28 +0600
tag: server
---

Две и больше версий на сервере для разных виртуальных хостов и папок.
Собственно пример для папки...

##add-apt-repository ppa:ondrej/php
##apt update
##apt install php5.6 php5.6-cgi
##
## Должны быть запущены
##a2enconf serve-cgi-bin
##a2enmod cgi
##a2enmod actions
##
## Следующее по надобности
##apt install php5.6-mbstring php5.6-mysql php5.6-gd php5.6-curl
##            php5.6-intl php5.6-mcrypt php5.6-xml php5.6-zip
##
## Переключение общее на php5.6
##a2dismod php7.2
##a2enmod php5.6
##
##
Alias /testphp5 /var/www/php5
<Directory /var/www/php5>
#
AllowOverride All
## По умолчанию 20 разрешим больше
##php_value max_file_uploads 100

## Это собственно код заставляющий использовать php5.6
<FilesMatch \.php$>
    SetHandler application/x-httpd-php5
</FilesMatch>
AddHandler application/x-httpd-php5 .php
Action application/x-httpd-php5 /cgi-bin/php
##
</Directory>
##end

