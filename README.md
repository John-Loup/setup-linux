TODO: bashrc, desktop, docker lamp

# LINUX SETUP
Just a reminder for a new linux setup


# 1) OS
Ubuntu 16.XX LTS
 - https://www.ubuntu.com/download/desktop
 
 
# 2) Terminal
## 2a) Get Terminator
````
sudo apt install terminator
````

## 2b) Config
````
sudo vi ~/.config/terminator/config
````

## .bashrc


# Packages
List of packages to install

## Web browsers
````
sudo apt install chromium-browser
````

## Text editors
````
sudo apt install vim

sudo apt install nano
````

## Docker
````
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -

sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"

sudo apt update

apt-cache policy docker-ce

sudo apt install -y docker-ce

sudo systemctl status docker
````

## OBS Studio
````
sudo apt-add-repository ppa:jon-severinsson/ffmpeg

sudo apt update

sudo apt install ffmpeg

sudo apt-add-repository ppa:obsproject/obs-studio

sudo apt install obs-studio

obs
````

## Slack
````
https://slack.com/downloads/linux
````

## PhpStorm
````
https://www.jetbrains.com/phpstorm/download/#section=linux
````

## Misc
````
sudo apt install curl

sudo apt install discord

sudo apt install font-manager

sudo apt install gnote

sudo apt install bleachbit

sudo apt install vlc
````


# Setup dev environment on docker
## Run a LAMP container
````
docker run -d --name lamp -p 81:80 -v /home/[USER]/docker-conts:/var/www/html nickistre/ubuntu-lamp
````

## Execute console
````
docker exec -it [container] bash
````

## Setup Adminer
````
mkdir /usr/share/adminer

wget "http://www.adminer.org/latest.php" -O /usr/share/adminer/latest.php

ln -s /usr/share/adminer/latest.php /usr/share/adminer/adminer.php

echo "Alias /adminer.php /usr/share/adminer/adminer.php" | tee /etc/apache2/conf-available/adminer.conf

a2enconf adminer.conf

service apache2 restart


# Update Adminer

wget "http://www.adminer.org/latest.php" -O /usr/share/adminer/latest.php


# Uninstall

a2disconf adminer.conf

service apache2 restart

rm /etc/apache2/conf-available/adminer.conf

rm -Rf /usr/share/adminer
````

## Setup Git
````
apt-get install git
````

## Add Vim & Nano
````
apt-get install vim

apt get install nano
````

## Clean docker
````
docker system prune -a
````


# Custom desktop
