# Create a host for your project
- Do not need run 'php artisan serve' anymore in your laravel project.
# 1. Go to linux terminal and type 
```php
cd /etc/apache2/sites-available
```
 
	 
# 2. Now create a file name like 
```php
yourdomain.conf
```


# 3. Copy paste this codes and save
- To open file type terminal

```php
sudo nano yourdomain.conf
```
```php
<VirtualHost *:80>
	# The ServerName directive sets the request scheme, hostname and port that
	# the server uses to identify itself. This is used when creating
	# redirection URLs. In the context of virtual hosts, the ServerName
	# specifies what hostname must appear in the request's Host: header to
	# match this virtual host. For the default virtual host (this file) this
	# value is not decisive as it is used as a last resort host regardless.
	# However, you must set it for any further virtual host explicitly.

	ServerName yourservername.test   #Your Server Name
	ServerAdmin webmaster@localhost
	DocumentRoot /project_name/public #Project directory and add '/public' at the end of project name  


	<Directory "/project_name/public"> #Same as Project Directory and add '/public' at the end of project name  
         #Options Indexes MultiViews
    AllowOverride All
    Require all granted
    </Directory>
	
 
	# Available loglevels: trace8, ..., trace1, debug, info, notice, warn,
	# error, crit, alert, emerg.
	# It is also possible to configure the loglevel for particular
	# modules, e.g.
	#LogLevel info ssl:warn

	ErrorLog ${APACHE_LOG_DIR}/error.log
	CustomLog ${APACHE_LOG_DIR}/access.log combined

	# For most configuration files from conf-available/, which are
	# enabled or disabled at a global level, it is possible to
	# include a line for only one particular virtual host. For example the
	# following line enables the CGI configuration for this host only
	# after it has been globally disabled with "a2disconf".
	#Include conf-available/serve-cgi-bin.conf
</VirtualHost>
#vim: syntax=apache ts=4 sw=4 sts=4 sr noet
```

## Now edit this file few steps
- 'ServerName' as your server name like example 'yourservername' 
- 'DocumentRoot' as your Project Directory and add '/public' at the end of project name  
- 'Directory' same as 'DocumentRoot'

# 4. After that add the site to hosts
```php
  sudo nano /etc/hosts 
```
## In 127.0.1.1 line add your domain name 'yourservername', same as server name which, previously write and save it


# 5. Now, active site
```php
  sudo a2ensite yourdomain.conf
```
# 6. Type this to restart server
```php
  service apache2 reload
```
# 7. At last permission need to project 
```php
  sudo chmod -R 777 ~/project_url
```
