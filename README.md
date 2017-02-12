# WAMP_Remote_Update
//Remote connection and manual update instruction for WAMP Server 3.0.6+
//For proper readme style please enable raw mode

# Change this section in C:\wamp64\bin\apache\apache2.4.25\conf\extra\httpd-vhosts.conf

<Directory  "c:/wamp64/www/">
		Options +Indexes +Includes +FollowSymLinks +MultiViews
		AllowOverride All
		Require local
	</Directory>
  
  to this
  
  <Directory  "c:/wamp64/www/">
		Options +Indexes +Includes +FollowSymLinks +MultiViews
		AllowOverride All
		Require all granted
	</Directory>

# Change this section in C:\wamp64\alias\phpmyadmin.conf and adminer.conf
<Directory "C:/wamp64/apps/phpmyadmin4.6.6/">
	Options Indexes FollowSymLinks MultiViews
  AllowOverride all
  <ifDefine APACHE24>
		Require local
	</ifDefine>
	<ifDefine !APACHE24>
		Order Deny,Allow
    Allow from 127.0.0.1
	</ifDefine>

to this

<Directory "C:/wamp64/apps/phpmyadmin4.6.6/">
	Options Indexes FollowSymLinks MultiViews
  AllowOverride all
  <ifDefine APACHE24>
		Require all granted
	</ifDefine>
	<ifDefine !APACHE24>
		Order Deny,Allow
    Allow from all
	</ifDefine>
