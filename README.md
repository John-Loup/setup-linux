# Linux setup
Just a reminder for a new linux setup

# OS
Ubuntu 16.XX LTS
 - https://www.ubuntu.com/download/desktop

# Packages
List of packages to install

## Web browsers
````
sudo apt install chromium-browser

sudo apt install 
````

## Text editors
````
sudo apt install vim
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

## Misc
````
sudo apt install curl

sudo apt install discord

sudo apt install font-manager

sudo apt install gnote
````
