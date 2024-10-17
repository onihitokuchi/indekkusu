Ubuntu (20.04, 22.04, and 24.04) 
```sh
sudo add-apt-repository ppa:ondrej/php

sudo apt update
```

Debian (10, 11, and 12) 
```sh
sudo apt install apt-transport-https
sudo curl -sSLo /usr/share/keyrings/deb.sury.org-php.gpg https://packages.sury.org/php/apt.gpg
sudo sh -c 'echo "deb [signed-by=/usr/share/keyrings/deb.sury.org-php.gpg] https://packages.sury.org/php/ $(lsb_release -sc) main" > /etc/apt/sources.list.d/php.list'

sudo apt update
```

```sh
sudo apt-get install -y php8.3 php8.3-cli php8.3-common php8.3-fpm php8.3-mysql php-sqlite3 php8.3-pgsql php8.3-zip php8.3-gd php8.3-mbstring php8.3-curl php8.3-xml php8.3-bcmath php8.3-tokenizer php8.3-gd php8.3-intl php8.3-zip php8.3-tidy php8.3-imagick php8.3-soap php8.3-zmq


sudo apt-get install -y apache2 libapache2-mod-php
```

```sh
php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
php -r "if (hash_file('sha384', 'composer-setup.php') === 'dac665fdc30fdd8ec78b38b9800061b4150413ff2e3b6f88543c636f7cd84f6db9189d43a81e5503cda447da73c7e5b6') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;"
php composer-setup.php
php -r "unlink('composer-setup.php');"


sudo mv composer.phar /usr/local/bin/composer

sudo chmod +x /usr/local/bin/composer
```

```sh
composer global require laravel/installer
```

```sh
composer global require genesisweb/valet-linux-plus --with-all-dependencies
```
    export PATH="$PATH:$HOME/.config/composer/vendor/bin"

