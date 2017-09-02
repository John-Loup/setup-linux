TODO: old bash commands, phpstorm settings + theme

# LINUX SETUP
Just a reminder for a new linux setup


# 1: OS
Ubuntu 16.XX LTS
 - https://www.ubuntu.com/download/desktop
 
 
# 2: Terminal

## Terminator
````
sudo apt install terminator


# config

sudo gedit ~/.config/terminator/config
````

## .bashrc
````
sudo gedit ~/.bashrc


# prompt

PS1='\e[02;32m\u \e[m\e[00;33m\w\e[m \e[0;31m\n->\e[m '


# aliases

alias autorm="sudo apt autoremove"
alias update="sudo apt-get update"
alias upgrade="sudo apt upgrade"
alias ca='bc -l'
mkcd ()
{
    mkdir -p -- "$1" &&
      cd -P -- "$1"
}
alias ctrash="gvfs-trash --empty"
alias hrm="gvfs-trash"
alias localhost="cd ~/../../var/www/html"
alias open="nautilus ."
alias clean="sudo rm /var/lib/apt/lists/* -vf"
alias mirror="cd ~/docker-mirror"
````


# 3: Packages

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

sudo usermod -aG docker ${USER}


# Clean Docker

docker system prune -a
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
 - https://slack.com/downloads/linux
 
## Discord
 - https://discordapp.com/download

## PhpStorm
 - https://www.jetbrains.com/phpstorm/download/#section=linux

````
sudo gedit ~/.bashrc
````
Add this line
 - PATH="$PATH:[path_to_directory]/PhpStorm-171.4694.2/bin"

## Misc
````
sudo apt install curl

sudo apt install htop

sudo apt install font-manager

sudo apt install gnote

sudo apt install bleachbit

sudo apt install vlc

sudo apt install indicator-multiload
````


# 4: Setup a dev environment on docker

## Run an Ubuntu-LAMP container
````
docker run -d --name [name] -p 81:80 -v /home/${USER}/docker-mirror:/var/www/html nickistre/ubuntu-lamp
````

## Execute console
````
docker exec -it [container] bash
````

## Updates
````
apt-get update

apt-get upgrade

apt-get autoremove
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

## Change MySQL password
````
SET PASSWORD FOR '[user]'@'localhost' = PASSWORD('[password]');

FLUSH PRIVILEGES;
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


# 5: Custom desktop

## i3 Windows Manager
 - https://i3wm.org/docs/repositories.html
 
## Unity
 - CCSM
 ````
 sudo apt install compizconfig-settings-manager
 
 sudo apt install compiz-plugins
 
 sudo apt install compiz-plugins-extra
 ````
 
 - Unity Tweak Tool
 ````
 sudo apt install unity-tweak-tool
 ````
 
 - Theme : https://github.com/andreisergiu98/arc-flatabulous-theme
 
 
 # 6: Restore Booting
````
sudo add-apt-repository ppa:yannubuntu/boot-repair && sudo apt-get update

sudo apt-get install -y boot-repair && boot-repair &
````
