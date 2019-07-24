
- que:
  - install ubuntu dose not respond
  - can not install ubuntu
  ans:
  - At startup selection screen, press F6, then unselect all the fork options.

- que:
  - how to modify screen brightness
  - how to change screen backlight
  ans:
  - xbacklight -set 40

- que:
  - linux chinese garbled
  ans:
  - iconv -f gb2312 -t utf-8 xx.txt> xx.tzt

- que:
  - unzip garbled
  ans:
  - unzip -O CP936 xx.zip

- que:
  - filename garbled
  - linux filename garbled
  - file name garbled
  - linux file name garbled
  ans: |
   convmv -r -f utf8 -t iso88591 * --notest --nosmart
   convmv -r -f gbk -t utf8 * --notest --nosmart

- que:
  - how to modify user name
  - how to change user name
  ans: |
   Edit 3 files, replace the name in the file
   sudo vi /etc/passwd
   sudo vi /etc/shadow
   sudo vi /etc/group
   Rename the home folder
   Reboot

- que:
  - how to tar
  - how to compress
  ans: |
   tar cvf xx.tar filename
   tar czf xx.tar.gz filename
   tar cjf xx.tar.bz2 filename

- que:
  - how to unzip
  - how to untar
  - how to uncompress
  ans: |
   tar xf
   unrar e *.rar
   unzip *.zip
   gzip -d *.gz

- que:
  - apt error
  - apt source error
  - how to deal with apt error
  ans: |
   sudo rm -vf /var/lib/apt/lists/*
   sudo apt update

- que:
  - why can not use java
  ans: |
   Check if the environment is correct
      export JAVA_HOME={your_jdk_dir}
      export JRE_HOME=${JAVA_HOME}/jre
      export CLASSPATH=:.${JAVA_HOME}/lib:${JRE_HOME}/lib
      export PATH=${JAVA_HOME}/bin:$PATH

- que:
  - how to add boot items with xfce4
  ans:
  - xfce4-session-settings

- que:
  - filezilla can not upload
  ans: |
   Try to refresh it.
   FTP space may be full.

- que:
  - how to merge audio
  - how to combine audio
  ans: |
   Install ffmpeg
   Write a list for splicing files
      file '/path/to/file1'
      file '/path/to/file2'
      file '/path/to/file3'
   ffmpeg -f concat -i list -c copy output.mp3

- que:
  - ubuntu can not start
  ans: |
   Enter this commands on grub
      grub rescue> ls
      grub rescue> ls (hd0, X)/boot/grub "if it shows something, it means that linux is installed in this partition."
      grub rescue> set root=(hd0, X)
      grub rescue> set prefix=(hd0, X)/boot/grub
      grub rescue> insmod /boot/grub/normal.mod
      grub rescue> normal
   After enter ubuntu system, enter,
      sudo update-grub
      sudo grub-install /dev/sda

- que:
  - how to add environment value
  ans:
  - export PATH=/usr/local/arm/2.95.3/bin:$PATH

- que:
  - how to connect iscsi
  ans: |
   First, make sure you have open-iscsi
   Modify /etc/iscsi/iscsid.conf
     node.startup automatic
   Find iSCSI host "This step can be omitted"
   Login iSCSI: sudo iscsiadm --mode discovery --type sendtargets --portal 192.168.87.125 -D --login
   sudo fdisk -l
   sudo mount /dev/sdb1/mnt/iscsi
   If the disk is not formatted,
   sudo fdisk /dev/sdb
   sudo mkfs.ext4 /dev/sdb1

- que:
  - how to shutdown ports
  - how to shutdown services
  ans: |
   View open ports: nmap 127.0.0.1
   View system services: service --status-all
   Close Service: sudo service xx stop

- que:
  - how to turn off 631 port
  ans:
  - sudo service cups stop

- que:
  - how to disable boot animation
  - how to close boot animation
  - how to turn off boot animation
  ans: |
   Modify /etc/default/grub
      GRUB_CMDLINE_LINUX_DEFAULT = ''
   sudo update-grub

- que:
  - how to connect to samba on linux
  ans:
  - sudo mount -t cifs //192.168.1.7/share -o username=your_PC_name, password='xx', iocharset=utf8 ~/share

- que:
  - ubuntu can not shutdown
  ans: |
   Modify /etc/default/grub
     GRUB_CMDLINE_LINUX_DEFAULT="acpi=off apm power_off=1 quiet splash"
   sudo update-grub

- que:
  - how to set default browser
  ans:
  - sudo update-alternatives --config x-www-browser

- que:
  - how to install powertop
  ans: |
   sudo apt install powertop
   edit /etc/rc.local
     powertop &&
     exit 0

- que:
  - how to echo numerical scale
  - how to display numerical scale
  ans:
  - echo "scale=2;1/3"|bc

- que:
  - how to take mouse area screenshot
  ans:
  - scrot -s

- que:
  - can not open libstdc++.so.6
  ans: |
   sudo apt install libstdc++6
   sudo apt install lib32stdc++6

- que:
  - how to connect wep on command line
  ans: |
   Method 1
   iwlist wlan0
   sudo iwconfig wlan0 essid xx key xx
   sudo dhclient wlan0 or sudo dhcpcd wlan0
   Method 2
   sudo iw dev wlan0
   sudo iw dev wlan0 connect xx
   sudo dhclient wlan0 or sudo dhcpcd wlan0
   Note: If you set the essid iwconfig no response, sudo apt autoremove network-manager.

- que:
  - how to connect wpa on command line
  ans: |
   sudo wpa_supplicant -i wlan0 -c/etc/wpa_supplicant/wpa_supplicant.conf
   sudo dhcpcd wlan0

- que:
  - how to turn off gedit automatic backup
  - how to turn off gedit backup
  ans:
  - Open gedit, choose Edit->Preference->Editor, unselect "Create a backup copy of files before saving"

- que:
  - how to display star wars movie on command line
  ans:
  - telnet towel.blinkenlights.nl

- que:
  - how to save error log
  ans:
  - make>error 2>&1

- que:
  - how to install lamp environment
  - how to install lamp
  ans: |
   sudo apt install apache2 php5 libapache2-mod-php5 mysql-server libapache2-mod-auth-mysql php5-mysql
   sudo /etc/init.d/apache2 restart
   Then enter this: sudo ls /etc/apache2/mods-enabled, see if there are php5.conf and php5.load, if not, try: sudo a2enmod php5

- que:
  - how to install phpmyadmin
  ans: |
   Download and unpack the phpmyadmin package.
   sudo cp /var/www/phpmyadmin/config.sample.inc.php /var/www/phpmyadmin/config.inc.php
   sudo vi /var/www/phpmyadmin/config.inc.php
     Find "blowfish_secret" then enter any words behind it.
   At last install php5-mcrypt
   sudo apt install php5-mcrypt
   sudo vi /etc/php5/apache2/php.ini
   Modify like that:
     extension php5-mcrypt.so

- que:
  - how to delete more than one files
  - how to delete multiple files
  ans:
  - find -name "filename" -print|xargs rm

- que:
  - how to change mysql data to sqlite data
  - how to migrate mysql data to sqlite
  - how to move mysql data to sqlite
  ans: |
   First, export the data into a sql file by mysql
   Then modified the file as follows,
   Remove CREATE and INSERT statements,
   Modify every "\'" to "''",
   Edit the main key to "id INTEGER PRIMARY KEY",
   Edit the current time to "time TIMESTAMP NOT NULL DEFAULT (datetime('now','localtime'))",
   Edit the mysql ENUM to "CHECK(xx IN ('A','B'))",
   Delete all the statements like "PRIMARY KEY ('id')",
   Delete all the statements like "ENGINE=InnoDB AUTO_INCREMENT=5 DEFAULT_CHARSET=utf8",
   At last, import this file into sqlite database.

- que:
  - how to use mysql
  ans: |
   Start mysql server: sudo service mysql start
   Stop mysql server: sudo service mysql stop
   Change passwd: mysqladmin -u username -p
   Into a database: use db_name;
   Add database: create database db_name;
   Delete database: drop database db_name;
   Input sql files: mysql < xx.sql or mysql db_name < xx.sql
   Backup: mysqldump -u username -p db_name > filename
   Recover: mysql -u username -p db_name < filename
   Select the editor: pager vim

- que:
  - jre chinese garbled
  - jre garbled
  ans:
  - http://blog.163.com/maaa_139/blog/static/31023991201051542321224/

- que:
  - command x86_64-linux-gnu-gcc failed with exit status 1
  ans:
  - sudo apt install libevent-dev

- que:
  - how to calibrate touch screen
  ans: |
   This operation must be under the X-window environment
   First list all input devices, to find the touch screen id: xinput list
   Then use the following command to adjust the touch screen parameters to my CF-19 notebook parameters as an example,
     xinput set-prop 9 --type=float "Coordinate Transformation Matrix" 1.118 0 -0.09 0 1.16 -0.025 0 0 1
   More: https://wiki.archlinux.org/index.php/Calibrating_Touchscreen

- que:
  - how to install festival
  ans:
  - sudo pacman festival festival-us

- que:
  - can not find /dev/dsp
  ans: |
   Add the following to HOME folder, save it as .festivalrc,
     (Parameter.set 'Audio_Command' (aplay -q -c 1 -t raw -f s16 -r $SR $FILE))
     (Parameter.set 'Audio_Method' Audio_Command)

- que:
  - how to install wubi
  ans: |
   First install basic components: sudo pacman -S ibus ibus-table
   Then download ibus-table-wubi source package from the Internet, we need a data file inside the Wubi
   cd ibus-table-wubi/tables
   ibus-table-createdb -s wubi86.txt
   sudo cp wubi86.db /usr/share/ibus-table/tables
   Add the environment variable to .bashrc,
     export XMODIFIERS="@im=ibus"
     export GTK_IM_MODULE=ibus
     export QT_IM_MODULE=ibus
   ibus-daemon -drx
   Log off and then log back
   After ibus-setup "terminal command" add Wubi, press Ctrl+Space to launch Wubi.

- que:
  - how to install xfce4
  ans: |
   sudo pacman -S xfce4
   startxfce4

- que:
  - how to install x-window
  ans: |
   First install the basic components: sudo pacman -S xorg-server xorg-xinit xorg-utils xorg-server_utils mesa
   Then install window managers and terminal: sudo pacman -S xorg-twm xterm
   Finally, enter the original X-window by: startx

- que:
  - how to use mutt
  - how to use mail client on terminal
  ans: |
   First, install mutt: sudo pacman -S mutt
   Then establish .mutt folder, to store data files
   mkdir -p ~/.mutt/cache/headers
   mkdir ~/.mutt/cache/bodies
   touch ~/.mutt/certificates
   Add the following to ~/.muttrc file, modify according to their own circumstances,
     # A basic .muttrc for use with Gmail
     set imap_user "your_email@gmail.com"
     set imap_pass "your_email_password"
     set smtp_url "smtp://your_email@smtp.gmail.com:587/"
     set smtp_pass "your_email_password"
     set from "your_email@gmail.com"
     set realname "your_name"
     set editor "vim"
     # Basic config, you can leave this as is
     set folder "imaps://imap.gmail.com:993"
     set spoolfile "+INBOX"
     set imap_check_subscribed
     set hostname gmail.com
     set mail_check 120
     set timeout 300
     set imap_keepalive 300
     set postponed "+[GMail]/Drafts"
     set record "+[GMail]/Sent Mail"
     set header_cache = ~/.mutt/cache/headers
     set message_cachedir = ~/.mutt/cache/bodies
     set certificate_file = ~/.mutt/certificates
     set move no
     set include
     set sort 'threads'
     set sort_aux 'reverse-last-date-received'
     set auto_tag yes
     ignore "Authentication-Results:"
     ignore "DomainKey-Signature:"
     ignore "DKIM-Signature:"
     hdr_order Date From To Cc
     alternative_order text/plain text/html *
     auto_view text/html
     bind editor <Tab> complete-query
     bind editor ^T complete
     bind editor <space> noop
     # Gmail-style keyboard shortcuts
     macro index,pager y "<enter-command>unset trash\n <delete-message>" "Gmail archive message"
     macro index,pager d "<enter-command>set trash=\"imaps://imap.googlemail.com/[GMail]/Bin\"\n <delete-message>" "Gmail delete message"
     macro index,pager gi "<change-folder>=INBOX<enter>" "Go to inbox"
     macro index,pager ga "<change-folder>=[Gmail]/All Mail<enter>" "Go to all mail"
     macro index,pager gs "<change-folder>=[Gmail]/Starred<enter>" "Go to starred messages"
     macro index,pager gd "<change-folder>=[Gmail]/Drafts<enter>" "Go to drafts"
   Finally, for safety, it is need to modify the configuration file permissions: sudo chmod 600 ~/.muttrc
   References: http: //www.cnblogs.com/wangkangluo1/archive/2012/12/28/2837300.html

- que:
  - how to install yaourt
  ans: |
   First add yaourt source to /etc/pacman.conf,
     [archlinuxcn]
     #The Chinese Arch Linux communities packages.
     SigLevel Optional TrustAll
     Server http://repo.archlinuxcn.org/$arch
   Then synchronize and install: sudo pacman -Syu yaourt

- que:
  - how to install sound card
  - how to install sound card driver
  ans: |
   sudo pacman -S alsa-lib alsa-tools alsa-utils alsa-oss
   Now you can use alsamixer command to adjust the volume
   Note: Press m is for mute

- que:
  - how to check battery
  ans: |
   sudo pacman -S acpi
   acpi power

- que:
  - publickey permission deny
  ans:
  - ssh-add yourkey "Not the .pub"

- que:
  - how to modify git editor
  - how to change git editor
  ans:
  - git config --global core.editor vim

- que:
  - git can not upload
  - git can not push
  ans: |
   1.Pull before push (Adviced)
      git pull git@github.com:aaa/bbb.git master
      git push -u git@github.com:aaa/bbb.git master
   2.Force pushing (Danger)
      git push -u git@github.com:aaa/bbb.git master -f

- que:
  - vim how to edit dos files
  ans:
  - :e ++ff=dos

- que:
  - vim how to delete same lines
  ans:
  - :g/^\(.\+\)$\n\1/d

- que:
  - vim how to get ascii
  ans:
  - ga

- que:
  - what is vim plugin folder mean
  - what is the meaning of vim plugin folder
  ans:
  - When Vim start, it will automatically execute the plugin folder, next it will execute the ftplugin(file type plugin) folder, autoload folder is used to store big *.vim files, only execute when function calls, it is used to make vim launch faster.

- que:
  - how to make vim plug-in
  ans: |
   First, in /etc/vimrc, "filetype plugin on" should be opened
   Then in plugin, "au BufNewFile, BufRead, *.xx call set filetype=AAA" to set the file type
   When open *.xx file, Vim will find AAA.vim and execute it.
   In each *.vim file, function like filename#function() will call filename#function() in filename.vim
   In plugin folder, "set syntax=BBB" will call BBB.vim in syntax folder to highlight the codes.

- que:
  - vim how to flip pages
  ans: |
   PageDown: Ctrl + f
   PageUp: Ctrl + b

- que:
  - vim how to match chinese
  ans:
  - '[\u4e00-\u9fa5]'

- que:
  - vim how to match english
  ans:
  - '[\u0020-\u007E]'

- que:
  - how to use vim historical views
  - how to view vim history
  ans: |
   Back: Ctrl + o
   Forward: Ctrl + i

- que:
  - how to find multiple files in vim
  - vim how to find multiple files
  ans:
  - vimgrep /String/ ./*

- que:
  - vim how to fold the code
  ans: |
   First, add this in vimrc,
     Set foldmethod=indent
   Then, open the fold: l
   Open all folds: zR
   Close fold: zc
   Close all folds: zM
   Expand entire function: zO

- que:
  - vim how to access system clipboard
  ans: |
   Be sure to install the vim-gnome, otherwise you can not operate the system clipboard
   sudo apt install vim-gnome
   ":reg" to see all clipboard contents in vim, the "+ is the system clipboard
   Use command "+y to copied to the system clipboard, use command "+p to past from the system clipboard

- que:
  - vim can not open plug-in help documentation
  ans:
  - ':helptags ~/.vim/doc'

- que:
  - vim how to replace words
  ans: |
   Replace a to b: :%s/a/b/g
   Replace a to b from line n to line m: :n,ms/a/b/g

- que:
  - vimwiki how to make a new line
  ans:
  - Just type <br>

- que:
  - vim how to read binary file
  ans: |
   vi -b filename
   :%!xxd

- que:
  - gvim how to init
  ans: |
   set guifont=Consolas::h12:cANSI
   colorscheme darkblue
   set nobackup
   set encoding=utf-8

- que:
  - how to init vim
  ans: |
   nmap <C-H> <C-W>h
   nmap <C-J> <C-W>j
   nmap <C-K> <C-W>k
   nmap <C-L> <C-W>l
   set tabstop=4
   set softtabstop=4
   set expandtab
   set shiftwidth=4
   set autoindent
   set cindent
   set cinoptions={2,1s,t0,n-2,p2s,(03s,=.5s,>1s,=1s,:1s
   imap kk <ESC>

- que:
  - how to use nmap
  ans: |
   nmap -sP 192.168.1.* Lists all online equipment segment
   nmap -O 192.168.1.* detect operating system

- que:
  - how to change mac address
  - how to modify mac address
  ans: |
   If your net card is eth0
   sudo ifconfig eth0 down
   sudo ifconfig eth0 hw ether new_mac_address
   sudo ifconfig eth0 up

- que:
  - how to deal with jlink unknow device
  - jlink unknow device
  ans: |
   Short connect the Erase pin and the TST pin longer.
   It is less relationship to the order of short connection.

- que:
  - how to install sdcc on ubuntu
  - how to install sdcc
  ans: |
   sudo apt install sdcc
   If it does not work, try this: sudo apt install gputils gputils-common gputils-doc sdcc sdcc-doc sdcc-libraries sdcc-ucsim

- que:
  - cmu sphinx can not find libpocketsphinx.so.1
  ans: |
   sudo apt install audacity
   libpocketsphinx.so.1 problem will arise when you start pocketsphinx_continues. It mainly due to that sphinxbase did not be added to the library path environment variable
   So we do: sudo vi/etc/ld.so.conf
   Add this,
     /Usr/local/lib
     /Usr/local/lib/pkgconfig
   Then, sudo ldconfig

- que:
  - cmu sphinx failed to open audio device
  - pocketsphinx_continues failed to open audio device
  ans:
  - sudo apt install pulseaudio

- que:
  - cmu sphinx failed to calibrate voice activity detection
  - pocketsphinx_cintinues failed to calibrate voice activity detection
  ans:
  - wake up the computer

- que:
  - cmu sphinx pycapsule_getpointer called with invalid pycapsule object
  ans:
  - install the new version, upper than 5prealpha

- que:
  - python undefined symbol ps_update_lmset
  ans: |
   sudo easy_install -m sphinxbase
   sudo easy_install -m pocketsphinx

- que:
  - expreval error when build coreseek
  ans: |
   Edit sphinxexpr.cpp, line 1010, 1044, 1077, change T val ExprEval (this-> m_pArg, tMatch); to T val this-> ExprEval (this-> m_pArg, tMatch);
   Note: the config file of sphinx does not support ~/but support/home/user

- que:
  - how to install xml.vim
  ans: |
   Copy xml.vim file to ~/.vim/ftplugin and then use ln -s command to create relationship between xml.vim and docbk.vim, xsl.vim, html.vim, xhtml.vim
   Open ftplugin in vimrc
   Tips,
   Tag autocomplete: double-click > symbol
   Auto new line: double-click ; symbol in INSERT mod
   For more help, enter: help xml-plugin

- que:
  - bochs dlopen failed for module x file not found
  ans:
  - sudo apt install bochs-x

- que:
  - libbx_x.so undefined symbol xpmcreatepixmapfromdata
  ans:
  - added, display_library; sdl in bochsrc

- que:
  - bochs error
  ans: |
   If an error of bochsrc occured, the normal way is just comment the error line.
   bochsrc use double quotes, not single quotes.
   Use bximage to make image
   sudo kpartx -a xx.img mount the image
   sudo kpartx -d xx.img unmount the image

- que:
  - how to mount qcow2
  - how to mount qcow2 image
  ans: |
   modprobe nbd max_part=63
   qemu-nbd -c /dev/nbd0 image.img
   mount /dev/nbd0p1 /mnt/image

- que:
  - how to install ftp server on ubuntu
  ans:
  - sudo apt install pure-ftpd

- que:
  - git how to revert
  ans:
  - git revert HEAD

- que:
  - sqlite can not import data from text
  - sqlite can not import text
  ans:
  - Change text to sql file, then import.

- que:
  - how to replace string in multiple files
  - how to replace text in multiple files
  - how to replace in multiple files
  - how to sed
  ans:
  - sed -i 's/old/new/g' filename

- que:
  - kvm how to use snapshot
  ans: |
   Create snapshot: qemu-img snapshot -c snapshot_name image.qcow2
   Show all the snapshot: qemu-img snapshot -l image.qcow2
   Revert snapshot: qemu-img snapshot -a snapshot_name image.qcow2
   Delete snapshot: qemu-img snapshot -d snapshot_name image.qcow2

- que:
  - how to use lftp
  ans: |
   Login: lftp name@site:port
   Command: ls, cd, get, put, mirror -R

- que:
  - how to sudo when boot up ubuntu
  ans:
  - Just write sudo in /etc/rc.local, cause rc.local is executed by root.

- que:
  - openwrt how to install ftp server
  - how to install ftp server on openwrt
  ans: |
   opkg update
   opkg install vsftpd

- que:
  - pico cms can not open sub page
  ans: |
   Make sure the .htaccess file is in the main folder.
   sudo vi /etc/apache2/apache2.conf, change "AllowOverride None" to "AllowOverride FileInfo Options"

- que:
  - kvm how to create image
  - how to create kvm image
  ans:
  - sudo qemu-img create -f qcow2  image.img 60G

- que:
  - how to install kvm
  ans:
  - sudo apt install qemu-kvm virt-manager bridge-utils libvirt-bin

- que:
  - how to install vnc server
  ans: |
   sudo apt install vnc4server
   vncpasswd
   sudo apt install xfce4
   vi ~/.vnc/xstartup, annotate the old config, add new config,
     #x-terminal-emulator -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" & 
     #x-window-manager & 
     sesion-manager & xfdesktop & xfce4-panel & 
     xfce4-menu-plugin & 
     xfsettingsd & 
     xfconfd & 
     xfwm4 & 
   Start server: vncserver :1
   Stop server: vncserver -kill :1

- que:
  - how to wake up remote pc
  - how to wake up remote computer
  ans:
  - wakeonlan -i ip_address mac_address

- que:
  - how to mount raw
  - how to mount raw image
  ans: |
   sudo fdisk -lu image.raw, find the first start number n,
   echo $((n*512)), get N,
   sudo mount -o loop,offset=N image.raw folder/

- que:
  - can not use tab on terminal
  - can not use tab on command line
  - terminal can not use tab
  - command line can not use tab
  ans: |
   vi ~/.config/xfce4/xfconf/xfce-perchannel-xml/xfce4-keyboard-shortcuts.xml
   Change line <property name="<Super>Tab" type="string" value="switch_window_key"/> to <property name="<Super>Tab" type="empty"/>
   sudo reboot

- que:
  - vim how to save word in regular expression
  - vim how to save words in regular expression
  - vim how to save string in regular expression
  ans:
  - :%s/\(str_1\) xx \(str_2\)/\2 or \1/

- que:
  - vim how to remove duplicate rows
  - vim how to delete duplicate rows
  ans: |
   :sort
   :g/^\(.*\)$\n\1$/d

- que:
  - vim how to mismatch
  ans:
  - '[^(your_regex)]'

- que:
  - vim how to convert case
  - vim how to change case
  ans: |
   :%s/\(xx\)/\L\1/g (Lower)
   :%s/\(xx\)/\U\1/g (Upper)

- que:
  - how to install vim-markdown
  ans: |
   Download and unzip vim-markdown
   Edit /etc/vimrc, add,
     set noncompatible
     filetype plugin on

- que:
  - how to remove encryption on ubuntu
  - how to remove main folder encryption on ubuntu
  ans: |
   First, backup: sudo cp -rp /home/your_name /home/your_name.bk
   Then, reboot and login by root
   rm -rf /home/your_name
   mv /home/your_name.bk /home/your_name
   rm -rf /home/.ecryptfs
   rm -rf /home/your_name/.ecryptfs
   rm -rf /home/your_name/.Private
   sudo apt autoremove ecryptfs-utils libecryptfs0

- que:
  - how to redirect the domain to github pages
  - how to redirect domain to github
  ans: |
   Add CNAME file in github main folder, the context is the domain.
   Then, the domain, add the github A Record,
     192.30.252.153
     192.30.252.154

- que:
  - how to install chrome flash plugin on ubuntu
  ans: |
   sudo apt install pepperflashplugin-nonfree
   sudo update-pepperflashplugin-nonfree --install

- que:
  - how to install firefox flash plugin on ubuntu
  ans:
  - sudo apt install flashplugin-nonfree

- que:
  - how to install a trash on ubuntu
  ans: |
   sudo apt install trash-cli
   Edit /usr/local/bin/trash-rm,
     #!/bin/bash
     # command name: trash-rm
     shopt -s extglob
     recursive=1
     declare -a cmd
     ((i = 0))
     for f in "$@"
     do
     case "$f" in
     (-*([fiIv])r*([fiIv])|-*([fiIv])R*([fiIv]))
     tmp="${f//[rR]/}"
     if [ -n "$tmp" ]
     then
     #echo "\$tmp == $tmp"
     cmd[$i]="$tmp"
     ((i++))
     fi
     recursive=0 ;;
     (--recursive) recursive=0 ;;
     (*)
     if [ $recursive != 0   -a  -d "$f" ]
     then
     echo "skipping directory: $f"
     continue
     else
     cmd[$i]="$f"
     ((i++))
     fi ;;
     esac
     done
     trash-put "${cmd[@]}"
   sudo chmod +x /usr/local/bin/trash-rm
   Finally, add 'alias rm="trash-rm"' to ~/.bashrc
   source ~/.bashrc

- que:
  - can not find cdrom when install ubuntu
  ans: |
   First, enter the command line when install
   Second, mount the U-disk
   Third, cd into U-disk then mount ubuntu.iso to /cdrom
   At last, exit and continue install.

- que:
  - kvm vnc can not connect
  ans: |
   Edit the domain file of the virtual machine, modify 127.0.0.1 to 0.0.0.0, like that,
     <graphics type='vnc' port='-1' autoport='yes' listen='0.0.0.0'>
     <listen type='address' address='0.0.0.0'/>
     </graphics>

- que:
  - kvm how to clone
  - how to clone kvm image
  ans:
  - virt-clone -o {old_kvm_name} -n {new_kvm_name} -f {new_kvm_image_address}

- que:
  - how to change terminal language
  - how to modify terminal language
  ans: |
   Edit /etc/default/locale,
     LANG="en_US.UTF-8"
     LANGUAGE="en_US:en"
   Reboot.

- que:
  - vim how to paste
  ans: |
   :set paste
   :set nopaste

- que:
  - php can not write files
  ans:
  - chmod

- que:
  - how to transfer files through ssh
  - how to transfer files by cifs
  ans:
  - sudo mount -t cifs //ip_address/folder -o username=xx,password='xx',iocharset=utf8 ~/folder

- que:
  - git how to check the difference
  - git how to diff
  ans: |
   git diff (tree vs index)
   git diff -cached (index vs commit)
   git diff HEAD (tree vs commit)

- que:
  - python how to install tkinter
  ans:
  - sudo apt install python3-tk

- que:
  - how to make system disk on linux
  ans:
  - sudo dd if=system.iso, of=/dev/sdc

- que:
  - centos can not connect to network
  ans: |
   vi /etc/sysconfig/network-scripts/ifcfg-eth0
   /etc/init.d/network restart

- que:
  - vim how to edit multiple files
  ans: |
   :args *.txt
   :argdo %s/old/new/g | update

- que:
  - how to unbind ip
  - how to delete ip
  ans:
  - ip addr del <ip> dev eth0

- que:
  - how to run program on background
  - how to run command on background
  ans:
  - nohup <command> &

- que:
  - how to show the dos break
  - how to display the dos break
  ans:
  - :e ++ff=unix %

- que:
  - how to create requirements.txt
  ans:
  - pip freeze

- que:
  - how to solve coding problem of python3
  ans:
  - Str = Str.encode('unicode-escape').decode()

- que:
  - what is forward compatibility and backward compatibility
  - what is the differents between forward compatibility and backward compatibility
  ans: |
   Forward compatibility means forward version support current version, based on forward version.
   Backward compatibility means current version support forward version, based on current version.

- que:
  - how to make code easy to read
  - how to read code better
  ans:
  - Just make it like nature language.

- que:
  - how to quick develop
  - how to develop software fast
  ans: |
   prepare a lot of modules, can help the conceptual product development become more quickly
   a lot of equivalent alternative conditions can help locating and fixing the faults
   rapid prototype development: I think focing on the special stage function and the speed is very important
   rapid prototype development: do before speak!
   do not keep coding for a long time, it will finally become very low effective. leave the computer for enough time will make it much better
   without communication, without quick development

- que:
  - how to cheat in half life
  ans: |
   sv_cheat 1
   god (God mode), impulse 101 (All weapons)

- que:
  - can not printf on stm32 mdk
  ans:
  - Target -> Use MicroLIB must be selected.

- que:
  - how to install gstc-isp on ubuntu
  ans: |
   When I run ./configure, there're some errors, so I did,
   sudo apt install gnome-core-devel
   sudo apt install gawk
   When make, there are errors, too. So I did,
   sudo apt install libvte-dev
   Then edit src/main.c, alter the line to _#include <vte-0.0/vte/vte.h>_

- que:
  - what is the meaning of flex
  ans:
  - A lower power and upgraded timer or bus.

- que:
  - dxp how to automatically check the pcb layout error
  ans:
  - reports -> board information -> report

- que:
  - what is dummy
  - what is the meaning of dummy
  ans:
  - It means virtual, null pointer.

- que:
  - where to put the switch
  ans:
  - Put in the positive pole, not GND, or the MCU will reboot again and again.

- que:
  - ls can not work
  ans:
  - Make sure the folder have "x" authority.

- que:
  - which folders need backup
  - which dirs need backup
  ans: |
   /boot
   /etc
   /home
   /root
   /usr/local
   /opt
   /srv
   /var

- que:
  - which folders do not need backup
  - which dirs do not need backup
  ans: |
   /dev
   /proc
   /mnt
   /media
   /tmp

- que:
  - how to copy with attributes
  ans:
  - cp -a

- que:
  - how to scp
  ans:
  - scp local_file root@xx.xx.xx.xx:remote_folder

- que:
  - what is pam
  ans: |
   modules for linux security
   auth: pam_securetty.so -> /etc/securetty -> pam_env.so -> pam_unix.so -> pam_secceed_if.so -> if not, pam_deny.so
   account: pam_nologin.so -> /etc/nologin -> pam_unix.so -> pam_succeed_if.so -> if ok, pam_permit.so
   password: pam_cracklib.so -> pam_unix.so -> md5, shadow -> if not, pam_deny.so
   session: close pam_selinux.so -> pam_limits.so -> pam_loginuid.so -> open pam_selinux.so

- que:
  - how to create account
  ans: |
   vi /etc/group
   grpconv
   vi /etc/passwd
   pwconv
   passwd user
   cp -a /etc/skel /home/user
   chown -R usergroup /home/user

- que:
  - how to distribute disk
  ans:
  - use Quota or LVM

- que:
  - how to mount
  ans:
  - sudo mount dev folder

- que:
  - linux kernel function
  ans: |
   System call interface
   Process control
   Memory management
   File System management
   Device drivers

- que:
  - how to make empty file
  - how to dd
  ans:
  - dd if=/dev/zero of=xx bs=100M count=1

- que:
  - python simple http server
  ans:
  - python -m SimpleHTTPServer 80

- que:
  - how to reset time
  ans:
  - date +"%Y%m%d %H%m" --set="20170101 1830"

- que:
  - how to kill user
  ans:
  - pkill -kill -t pts/x

- que:
  - how to rm every file
  - how to rm all the files
  ans:
  - find . -name "xx" | xargs rm -f

- que:
  - how to release port
  - how to kill port
  - how to close port
  ans: |
   lsof -i :8000
   kill -9 <pid>

- que:
  - how to update pip
  ans:
  -  pip install -U pip

- que:
  - how to mount ntfs
  ans:
  -  sudo mount -t ntfs /dev/sda1 /mnt

- que:
  - how to modify apt source
  ans:
  -  sudo vi /etc/apt/source.list

- que:
  - how to get memory status
  - how to get ram status
  ans:
  -  free -h

- que:
  - how to check ubuntu version
  ans:
  -  lsb_release -a

- que:
  - how to combine files
  ans:
  - cat file1 file2 > file

- que:
  - how to split file
  ans:
  - split -b 10k filename

- que:
  - how to rename multiple files
  ans:
  - rename 's/old/new/g' *.txt

- que:
  - vim how to open multiple files
  ans:
  - vi -o file1, file2, file3

- que:
  - vim how to edit multiple files
  ans: |
   :args *.txt
   :argdo %s/old/new/g

- que:
  - how to clean git log
  ans: |
   git checkout --orphan xx
   git add -A
   git commit -am "clean"
   git branch -D master
   git branch -m master
   git push -f

- que:
  - how to set ssh timeout
  ans: |
   edit /etc/profile, modify TMOUT=0
   source /etc/profile

- que:
  - vim how to format json
  ans:
  - :%!python -m json.tool

- que:
  - python how to format json
  ans:
  - json.dump(dict, fp, indent=4)

- que:
  - how to awk
  ans:
  - awk -F ',' '{print $4}'

- que:
  - shell how to count lines
  ans:
  - wc -l

- que:
  - linux how to check badblocks
  ans:
  - badblocks -v /dev/sdb

- que:
  - vim how to search multiple keywords
  ans:
  - /aaa\|bbb\|ccc

- que:
  - how to auto lock ubuntu
  ans:
  - sudo apt install xscreensaver

- que:
  - how to enable rc.local on ubuntu
  ans: |
   ln -fs /lib/systemd/system/rc-local.service /etc/systemd/system/rc-local.service
   touch /etc/rc.local
   chmod 755 /etc/rc.local

- que:
  - how to find files on linux
  ans:
  - find -type d -name xx -user mark -perm 775 -regex ‘^.*$’ -size +10k -mtime +60

- que:
  - how to shutdown on linux
  ans: |
   shutdown -h now
   shutdown -r now
   shutdown -h 23:30
   shutdown -h +15

- que:
  - how to know the current user on linux
  ans: |
   who
   who am i

- que:
  - how to create a shortcut on linux
  ans:
  - ln -s file link

- que:
  - how to cut
  ans:
  - cut -d ':' -f 1

- que:
  - how to check memory on linux
  ans:
  - free -h

- que:
  - how to replace string by tr
  ans:
  - cat xx | tr "aa" "bb"

- que:
  - how to delete string by tr
  ans:
  - cat xx | tr -d "xx"

- que:
  - how to combine files on linux?
  ans:
  - cat xx* > out.txt

- que:
  - how to show user info on linux?
  ans:
  - finger username

- que:
  - how to set selinux?
  ans: |
   sestatus
   getenforce
   setenforce 0/1

- que:
  - how to split a file on linux?
  ans: |
   split -b 300k filename (by size)
   split -l 10 filename (by line)

- que:
  - how to show the calendar on linux?
  ans:
  - cal 11 12 2017

- que:
  - how to calculate on linux?
  ans:
  - bc

- que:
  - how to find a file fast on linux?
  ans:
  - locate filename

- que:
  - how to make multiple dirs on linux?
  ans:
  - mkdir -p a/b/c/d

- que:
  - how to mkdir with mode setting?
  ans:
  - mkdir -m 775 xx

- que:
  - how to ls dir itself on linux?
  ans:
  - ls -d

- que:
  - how to list children dirs on linux?
  ans:
  - ls -R

- que:
  - how to show the user password info?
  ans:
  - chage -l user

- que:
  - how to change user info on linux?
  ans:
  - chfn

- que:
  - how to set default shell on linux?
  ans: |
   chsh -l
   chsh

- que:
  - how to write strings to other terminals on linux?
  ans:
  - write user pts/2

- que:
  - how to check user last login on linux?
  ans:
  - lastlog -u username

- que:
  - how to change line break on linux?
  ans: |
   unix2dos -k filename
   dos2unix -k filename

- que:
  - where is the linux password files?
  ans: |
   etc/passwd
   etc/shadow
   etc/group
   etc/gshadow

- que:
  - how to set the cli welcome page on linux?
  ans:
  - vi /etc/issue

- que:
  - where is the doc files on linux?
  ans:
  - usr/share/doc/

- que:
  - how to check the kill signal?
  ans:
  - kill -l

- que:
  - how to check bootup services on linux?
  ans:
  - service --status-all

- que:
  - how to block url by iptables?
  ans: |
   iptables -I INPUT -p tcp -m string --string "xx.com" --algo bm -j DROP
   iptables -I INPUT -p udp -m string --string "xx.com" --algo kmp -j DROP

- que:
  - how to copy only newer files on linux?
  ans:
  - cp -u

- que:
  - how to copy without links on linux?
  ans:
  - cp -d

- que:
  - how to copy multiple files on linux?
  ans:
  - cp a b c 

- que:
  - how to show the partition info on linux?
  ans:
  - parted /dev/sda print

- que:
  - how to make iso on linux?
  ans:
  - mkisofs -r -v -o xx.img folder

- que:
  - how to cut strings on linux?
  ans:
  - cut -d , -f 3 filename

- que:
  - how to sort lines on linux?
  ans:
  - sort filename

- que:
  - how to delete the same lines on linux?
  ans:
  - uniq filename

- que:
  - how to show current user on linux?
  ans:
  - users

- que:
  - how to show current group on linux?
  ans:
  - groups

- que:
  - how to check virtual memory on linux?
  ans:
  - vmstat

- que:
  - how to check file attributes on linux?
  ans:
  - stat filename

- que:
  - how to check current tty on linux?
  ans:
  - tty

- que:
  - how to set group on linux?
  ans: |
   groupadd group
   groupmod -g 201 -n group2 group1
   gpasswd group
   gpasswd -A user group 
   gpasswd -a user group
   groupdel group

- que:
  - how to set user on linux?
  ans: |
   useradd user
   useradd -u 755 -g users xx
   useradd -r xx 
   usermod -c This is xx user
   usermod -e 2020-12-31 user
   userdel -r user

- que:
  - how to cleanup iptables?
  ans: |
   iptables -F
   iptables -X
   iptables -Z

- que:
  - how to backup and restore iptables?
  ans: |
   iptables-save > txt
   iptables-restore < txt

- que:
  - how to get system boot up time?
  ans:
  - systemd-analyze

- que:
  - how to get host info?
  ans:
  - hostnamectl

- que:
  - how to compress video by ffmpeg
  ans:
  - ffmpeg -i input.mp4 -s 1280x720 -vcodec libx264 -b 800000 out.mp4

- que:
  - how to set sudo without passwd
  - how to set sudo nopasswd
  ans: |
   sudo update-alternatives --config editor
   sudo visudo
   Under line %sudo, add "name ALL=(ALL) NOPASSWD:ALL"

- que:
  - how to check all cpus in top command
  ans:
  - press "1"

- que:
  - dpkg how to remove multiple pkgs
  ans:
  - dpkg -l | grep "<your_keyword>" | cut -d' ' -f3 | sudo xargs dpkg --purge

- que:
  - how to enable rc.local on ubuntu18
  ans: |
   ln -fs /lib/systemd/system/rc-local.service /etc/systemd/system/rc-local.service
   touch /etc/rc.local
   chmod 755 /etc/rc.local

- que:
  - how to fix apt
  ans:
  - sudo rm /var/lib/dpkg/info/*

- que:
  - how to show graphics card on linux
  ans:
  - sudo lshw -c display

- que:
  - how to ln
  ans:
  - ln -s file link

- que:
  - how to remove bazel
  ans:
  - rm -fr ~/.bazel ~/.bazelrc

- que:
  - python how to not match
  ans:
  - [^xx]* (must contain *)

- que:
  - python regex how to save middle string
  ans:
  - use (.*)

- que:
  - how to change hostname on ubuntu
  ans: |
   Edit /etc/cloud/cloud.cfg, set preserve_hostname to true.
   sudo hostnamectl set-hostname xxx

- que:
  - how to list files in tar
  ans:
  - tar -tf xx

- que:
  - pip how to use china origin
  ans:
  - -i https://pypi.tuna.tsinghua.edu.cn/simple

- que:
  - how to get domain ip
  ans:
  - host google.cn

- que:
  - how to use tcpdump
  ans: |
   tcpdump
   tcpdump -i eth0
   tcpdump -XX (more detail)
   tcpdump -w saved_file
   tcpdump -r saved_file
   tcpdump -c 10
   tcpdump 'udp'
   tcpdump 'dst port 22 or dst port 80'
   tcpdump 'host www.baidu.com'
   tcpdump 'port ftp'
   more filter, see "man pcap-filter"

- que:
  - how to change vim theme?
  ans:
  - colorscheme xxx

- que:
  - python how to get object size
  ans:
  - sys.getsizeof(xx)
