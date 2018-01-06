# LINUX SETUP
Just a reminder for a new desktop setup

Full packages : 
````
sudo apt install -y terminator chromium-browser vim nano curl htop cron at font-manager bleachbit vlc indicator-multiload byobu unzip unrar git docky unity-tweak-tool compizconfig-settings-manager
````

# 1: OS
 Ubuntu 16.XX LTS
  - https://www.ubuntu.com/download/desktop
 
 
# 2: Packages

 ## Quick install
  ````
  sudo apt update -y && sudo apt upgrade -y && sudo apt install -y terminator chromium-browser vim nano curl htop cron at font-manager bleachbit vlc indicator-multiload byobu unzip unrar git
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

 ## Slack
   - https://slack.com/downloads/linux
 
 ## Discord
   - https://discordapp.com/download

 ## PhpStorm
   - https://www.jetbrains.com/phpstorm/download/#section=linux
 
   - Import theme and setings from "phpstorm-settings.tar.gz"
 
   - Add to ${PATH} (optional)
    ````
    sudo gedit ~/.bashrc
    ````
    PATH="$PATH:[path_to_directory]/PhpStorm-171.4694.2/bin"
    
  ## Firefox Developer
  - Download archive : https://www.mozilla.org/en-US/firefox/developer/
  
  - Extract in : /usr/local/firefox-dev/
  
  - Add launcher shortcut & icon :
  ````
  sudo vim ~/.local/share/applications/firefox-dev.desktop
  
  [Desktop Entry]
  Name=Firefox Developer
  GenericName=Firefox Developer Edition
  Exec=/usr/local/firefox-dev/firefox
  Terminal=false
  Icon=/usr/local/firefox-dev/browser/icons/mozicon128.png
  Type=Application
  Categories=Application;Network;X-Developer;
  Comment=Firefox Developer Edition Web Browser.
  ````

 # 2: Terminal

  ## .bashrc
  ````
  sudo vim ~/.bashrc


  # prompt
  
  parse_git_branch() {
	     git rev-parse --abbrev-ref HEAD 2> /dev/null| awk '{print " (git::"$0")" }'
  }
  
  PS1="\[\033[38;5;2m\]\u\[$(tput sgr0)\]\[\033[38;5;15m\] : \[$(tput sgr0)\]\[\033[38;5;11m\]\w\[$(tput sgr0)\]\[\033[38;5;15m\] \n-> \[$(tput sgr0)\]"

  # aliases

  alias ca='bc -l'
  mkcd ()
  {
      mkdir -p -- "$1" &&
        cd -P -- "$1"
  }
  alias ctrash="gvfs-trash --empty"
  alias srm="gvfs-trash"
  alias open="nautilus ."
  alias clean="sudo rm /var/lib/apt/lists/* -vf"
  alias rm="rm --preserve-root"
  alias ..="../"
  alias ...="../../"
  alias ....="../../../"
  alias cdeploy="sudo cdeploy"
  alias cremove="sudo cremove"
  alias cenable="sudo cenable"
  alias cdisable="sudo disable"
  ````

 ## .inputrc
  ````
  sudo gedit ~/.inputrc

  "\e[A": history-search-backward
  "\e[B": history-search-forward
  set show-all-if-ambiguous on
  set completion-ignore-case on
  ````

# 5: Setup a dev environment on docker

 ## Run an Ubuntu-LAMP container
  ````
  docker run -d --name [name] -p 81:80 -v /home/${USER}/docker-mirror:/var/www/html nickistre/ubuntu-lamp
  ````

 ## Execute the console
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
  
 ## Install Composer
 ````
 curl -sS https://getcomposer.org/installer | php
 
 sudo mv composer.phar /usr/local/bin/composer.phar
 
 vim ~/.bashrc
 alias composer='/usr/local/bin/composer.phar'
 
 source ~/.bashrc
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


# 6: Custom desktop

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
   
   
  ## Docky
  ````
  sudo apt install docky
  ````
   
   
  ## i3 Window Manager
   - https://i3wm.org/docs/repositories.html
 
 
 # 7: Restore Booting
 
  ## Boot Repair
  ````
  sudo add-apt-repository ppa:yannubuntu/boot-repair && sudo apt-get update

  sudo apt-get install -y boot-repair && boot-repair &
  ````
  
  ## Error after nvidia upgrade : tpm_crb MSFT0101:00: can't request region for resource
  ````
  sudo apt purge nvidia-*
  
  sudo add-apt-repository ppa:graphics-drivers/ppa
  
  sudo apt update
  
  sudo apt full-upgrade
  
  sudo apt install nvidia-378
  
  sudo reboot
  ````

 # 8: Tools
 
  ## Code checkers
   - http://www.acseo.fr/utiliser-phpmd-phpcs-php-cs-fixer-pour-vos-projets-php/
