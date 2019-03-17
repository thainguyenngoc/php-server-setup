sudo apt update
sudo apt upgrade

1. Install nvm
* curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.33.11/install.sh | bash
* close terminal
* new terminal
* command -v nvm

2. Install nginx

* sudo apt install nginx
* systemctl status nginx

3. Install mysql5.7

* sudo apt install mysql-server
* sudo systemctl status mysql
* sudo mysql_secure_installation

https://www.digitalocean.com/community/tutorials/how-to-install-mysql-on-ubuntu-18-04

4. Install php extension
  https://www.digitalocean.com/community/tutorials/how-to-install-linux-apache-mysql-php-lamp-stack-on-ubuntu

* sudo add-apt-repository ppa:ondrej/php
* sudo apt update
* sudo apt install php7.1
* sudo apt install php7.1-cli php7.1-common php7.1-curl php7.1-json php7.1-opcache php7.1-mysql php7.1-mbstring php7.1-mcrypt php7.1-zip php7.1-bcmath php7.1-gd php7.1-gmp php7.1-imagick php7.1-intl php7.1-simplexml php 7.1-dom

5. Install Composer
* cd ~
* curl -sS https://getcomposer.org/installer -o composer-setup.php
* sudo php composer-setup.php --install-dir=/usr/local/bin --filename=composer

6. Install Valet
* sudo chown -R $USER ~/.composer/
* sudo apt install network-manager libnss3-tools jq xsel
* composer global require cpriego/valet-linux
* valet install

7. Install Node
* nvm install 8.9
* nvm use node

8. Install yarn
* curl -sL https://deb.nodesource.com/setup_10.x | sudo -E bash -

* apt-get install -y nodejs

9. Install Git
* sudo apt install git
* git config --global user.name "Thai Nguyen"
* git config --global user.email "thai@manifera.com"
* git config --list

10. Backup ssh keys

* eval "$(ssh-agent -s)"
* ssh-add ~/.ssh/id_rsa


11. Install x-debug

* get php-debug from visual studio code
* php -i | grep xdebug
* sudo gedit /etc/php/7.1/cli/conf.d/20-xdebug.ini

  >>>
  [XDebug]
  xdebug.remote_enable = 1
  xdebug.remote_autostart = 1
  <<<

* valet restart

********* SOME BUGS *********

"Visual Studio Code is unable to watch for file changes in this large workspace" (error ENOSPC)#

* cat /proc/sys/fs/inotify/max_user_watches
* sudo gedit /etc/sysctl.conf

add to the end of file: fs.inotify.max_user_watches=524288

* sudo sysctl -p
