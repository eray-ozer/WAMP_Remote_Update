# WAMP_Remote_Update
// Remote connection and manual update instruction for WAMP Server 3.0.6+
// For proper readme style please enable raw mode
// Updates has got their readme files.

# FIRST OF ALL
// You need to open and forward your ports in your routers or modem to your machine (wamp installed machine)
// You need to enable your ports in Windows Firewall with Advance Security/Inboud Rules
// If you want to access your server on internet (outside of your LAN), you can use your public ip address with your apache port. (80 or 8080 or whichever you choice)
// If you want to access your server outside of LAN everytime, you need a static IP adress or DDNS service. 

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
