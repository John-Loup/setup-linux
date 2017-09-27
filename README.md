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
  
  parse_git_branch() {
	     git rev-parse --abbrev-ref HEAD 2> /dev/null| awk '{print " (git::"$0")" }'
  }
  
  PS1="\[\033[38;5;2m\]\u\[$(tput sgr0)\]\[\033[38;5;15m\] : \[$(tput sgr0)\]\[\033[38;5;11m\]\w\[$(tput sgr0)\]\[\033[38;5;15m\]\$(parse_git_branch) \e[0;31m\n->\e[m \[$(tput sgr0)\]"

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
  alias srm="gvfs-trash"
  alias lh="cd /var/www/html"
  alias open="nautilus ."
  alias clean="sudo rm /var/lib/apt/lists/* -vf"
  alias mirror="cd ~/docker-mirror"
  ````

 ## .inputrc
  ````
  sudo gedit ~/.inputrc

  "\e[A": history-search-backward
  "\e[B": history-search-forward
  set show-all-if-ambiguous on
  set completion-ignore-case on
  ````

# 3: Web browsers

 ## Chromium
  ````
  sudo apt install chromium-browser
  ````
 
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


# 4: Packages

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
 
   - Import theme and setings from "phpstorm-settings.tar.gz"
 
   - Add to ${PATH} (optional)
    ````
    sudo gedit ~/.bashrc
    ````
    PATH="$PATH:[path_to_directory]/PhpStorm-171.4694.2/bin"

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
