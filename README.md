# LINUX DESKTOP SETUP
Just a reminder for a new ubuntu 16.04 setup

---


# 1: Packages & softwares

 ## Quick install
  ````
  sudo apt update -y && sudo apt upgrade -y && sudo apt install -y terminator chromium-browser vim nano curl htop cron at font-manager bleachbit vlc indicator-multiload byobu unzip unrar git
  ````

  
 ## PhpStorm
   ````
   sudo snap install phpstorm --classic
   ````
 
   - Import theme and setings : https://github.com/John-Loup/setup-linux/raw/master/settings.jar
    

 # 2: Shell

  ## .bashrc
  ````
  sudo vim ~/.bashrc


  # prompt
  
  parse_git_branch() {
	     git rev-parse --abbrev-ref HEAD 2> /dev/null| awk '{print " (git::"$0")" }'
  }
  
  PS1="\[\033[38;5;2m\]\u\[$(tput sgr0)\]\[\033[38;5;15m\] : \[$(tput sgr0)\]\[\033[38;5;11m\]\w\[$(tput sgr0)\]\[\033[38;5;15m\] \n-> \[$(tput sgr0)\]"

  # ALIASES

  mkcd ()
  {
      mkdir -p -- "$1" &&
        cd -P -- "$1"
  }
  alias ctrash="gvfs-trash --empty"
  alias srm="gvfs-trash"
  alias aptclear="sudo rm /var/lib/apt/lists/* -vf"
  alias open="nautilus ."
  # cd
  alias ..1="cd ../"
  alias ..2="cd ../../"
  alias ..3="cd ../../../"
  # LXC
  alias cdeploy="sudo cdeploy"
  alias cremove="sudo cremove"
  alias cenable="sudo cenable"
  alias cdisable="sudo cdisable"
  # grep
  alias egrep='egrep --color=auto'
  alias fgrep='fgrep --color=auto'
  alias grep='grep --color=auto'
  # exa
  alias lsl='exa -ghil'
  alias lsr='exa -ghiR'
  alias lst='exa -ghiT'
  alias lslr='exa -ghiRl'
  alias lslt='exa -ghiTl'
  ````

 ## .inputrc
  ````
  sudo vim ~/.inputrc

  "\e[A": history-search-backward
  "\e[B": history-search-forward
  set show-all-if-ambiguous on
  set completion-ignore-case on
  ````
  
 ## vimrc
  ````
  sudo vim /etc/vim/vimrc
  ````
  
 ## Extras
  - https://github.com/BurntSushi/ripgrep#installation
  - https://the.exa.website/#installation
  - https://github.com/sharkdp/fd/releases
  

# 3: Custom desktop

 ## Cinnamon
 ````
  sudo apt install cinnamon
  ````


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
   
  ## Arc theme 
   - Theme : https://github.com/andreisergiu98/arc-flatabulous-theme
   
   
  ## Docky
  ````
  sudo apt install docky
  ````
   
   
  ## i3 Window Manager
   - https://i3wm.org/docs/repositories.html
   
   
  ## Create shortcuts manually
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

 
 # 4: Recovery
 
  ## Boot Repair
  ````
  sudo add-apt-repository ppa:yannubuntu/boot-repair && sudo apt-get update

  sudo apt-get install -y boot-repair && boot-repair &
  ````
  
  ## Repair NVIDIA GPU driver
  ````
  sudo apt purge nvidia-*
  
  sudo add-apt-repository ppa:graphics-drivers/ppa
  
  sudo apt update
  
  sudo apt full-upgrade
  
  sudo apt install nvidia-XXX
  
  sudo reboot
  ````
  
  ## Repair broken packages/dependencies
  ````
  sudo dpkg --configure -a
  
  sudo apt --fix-broken install
  ````
  
  ## Skip MySQL user verifications
  ````
  sudo systemctl set-environment MYSQLD_OPTS="--skip-grant-tables"
  ````
  

 # 5: Tools
 
  ## Code checkers
   - http://www.acseo.fr/utiliser-phpmd-phpcs-php-cs-fixer-pour-vos-projets-php/
   

