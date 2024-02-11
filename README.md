# LEMP (Linux, NGINX, MySQL/MariaDB, PHP) setup guide

This guide will help you install and configure LEMP (Linux, NGINX, MySQL/MariaDB, PHP) on your server.

## 0. Getting started

Login to your server and run the following commands:

```sh
sudo apt update && sudo apt upgrade && sudo apt install software-properties-common
```

## 1. Install NGINX

Let's add `ondrej/nginx` repository so we can install latest NGINX version.

```sh
sudo add-apt-repository ppa:ondrej/nginx
```

Now we can install NGINX using the following commands:

```sh
sudo apt update
sudo apt install nginx
```

Let's start the NGINX service:

```sh
sudo service nginx start
```

Now enable the service to start on boot:

```sh
sudo systemctl enable nginx
```

Congratulations! You have successfully installed NGINX and enabled it to start on boot.

You can check the status of the service:

```sh
sudo systemctl status nginx
```

> Active: active (running)

Press `Ctrl+C` to stop.

💡 TIP: Whenever you made changes to the `NGINX` configuration file make sure the config is ok and then restart the service.

To test the NGINX config:

```sh
sudo nginx -t
```

Restart the NGINX service:

```sh
sudo service nginx restart
```

## 2. Install MySQL/MariaDB

We are going to install MariaDB on our server. You can use `MySQL` as well, the installation process is almost same.

```sh
sudo apt install mariadb-server mariadb-client
```

Start the service using the following command:

```sh
sudo systemctl start mariadb
```

Enable the service to start on boot:

```sh
sudo systemctl enable mariadb
```

We have successfully installed MariaDB and enabled it to start on boot but we need to configure it.

```sh
sudo mysql_secure_installation
```

Choose the options:

```sh
Enter current password for root (enter for none): enter
Set root password? [Y/n]: Y
Remove anonymous users? [Y/n]: Y
Disallow root login remotely? [Y/n]: Y
Remove test database and access to it? [Y/n]: Y
Reload privilege tables now? [Y/n]: Y
```

Now you can login to MariaDB with the following command:

```sh
mysql -u root -p
```

if no password is set:

```sh
mysql -u root
```

you will be prompted to enter the password.

```sh
mysql> exit;
```

## 3. Install PHP (specifically PHP-FPM)

The latest version of PHP is `8.3` as of now but we are going to use the version `8.2` for this guide.

As like NGINX, we need to add the `ondrej/php` repository so we can install latest PHP version.

```sh
sudo add-apt-repository ppa:ondrej/php
sudo apt update
```

Now we can install PHP using the following commands:

```sh
sudo apt install php8.3-fpm php8.3-common php8.3-mysql php8.3-curl php8.3-zip php8.3-gd php8.3-mbstring php8.3-xml php8.3-bcmath php8.3-intl php8.3-gmp
```

You can check the installed PHP version using:

```sh
php -v
```

and to see the modules/extensions installed:

```sh
php -m
```

Start the PHP-FPM service:

```sh
sudo systemctl start php8.3-fpm
```

Enable the service to start on boot:

```sh
sudo systemctl enable php8.3-fpm
```

Check the status of the service:

```sh
sudo systemctl status php8.3-fpm
```

> Active: active (running)

Press `Ctrl+C` to stop.

> [!SUCCESS]
> Your server is up and running.
