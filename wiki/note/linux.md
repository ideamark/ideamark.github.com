# Linux


> [knowledgeQA start]

## install ubuntu dose not respond
At startup selection screen, press F6, then unselect all the fork options.

## how to modify screen brightness
xbacklight -set 40

## linux chinese garbled
iconv -f gb2312 -t utf-8 xx.txt> xx.tzt

## unzip garbled
unzip -O CP936 xx.zip

## filename garbled
convmv -r -f utf8 -t iso88591 * --notest --nosmart
convmv -r -f gbk -t utf8 * --notest --nosmart

## how to modify user name
Edit 3 files, replace the name in the file
sudo vi /etc/passwd
sudo vi /etc/shadow
sudo vi /etc/group
Rename the home folder
Reboot

## how to tar
tar cvf xx.tar filename
tar czf xx.tar.gz filename
tar cjf xx.tar.bz2 filename

## how to unzip
tar xf
unrar e *.rar
unzip *.zip
gzip -d *.gz

## apt error
1. sudo rm -vf /var/lib/apt/lists/*
2. sudo apt update

## why can not use java
Check if the environment is correct
export JAVA_HOME={your_jdk_dir}
export JRE_HOME=${JAVA_HOME}/jre
export CLASSPATH=:.${JAVA_HOME}/lib:${JRE_HOME}/lib
export PATH=${JAVA_HOME}/bin:$PATH

## how to add boot items with xfce4
xfce4-session-settings

## filezilla can not upload
Try to refresh it.
FTP space may be full.

## how to merge audio
Install ffmpeg
Write a list for splicing files
file '/path/to/file1'
file '/path/to/file2'
file '/path/to/file3'
ffmpeg -f concat -i list -c copy output.mp3

## ubuntu can not start
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

## how to add environment value
export PATH=/usr/local/arm/2.95.3/bin:$PATH

## how to connect iscsi
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

## how to shutdown ports
View open ports: nmap 127.0.0.1
View system services: service --status-all
Close Service: sudo service xx stop

## how to turn off 631 port
sudo service cups stop

## how to disable boot animation
Modify /etc/default/grub
GRUB_CMDLINE_LINUX_DEFAULT = ''
sudo update-grub

## how to connect to samba on linux
sudo mount -t cifs //192.168.1.7/share -o username=your_PC_name, password='xx', iocharset=utf8 ~/share

## ubuntu can not shutdown
Modify /etc/default/grub
GRUB_CMDLINE_LINUX_DEFAULT="acpi=off apm power_off=1 quiet splash"
sudo update-grub

## how to set default browser
sudo update-alternatives --config x-www-browser

## how to install powertop
sudo apt install powertop
edit /etc/rc.local
powertop &&
exit 0

## how to echo numerical scale
echo "scale=2;1/3"|bc

## how to take mouse area screenshot
scrot -s

## can not open libstdc++.so.6
sudo apt install libstdc++6
sudo apt install lib32stdc++6

## how to connect wep on command line
Method 1
iwlist wlan0
sudo iwconfig wlan0 essid xx key xx
sudo dhclient wlan0 or sudo dhcpcd wlan0
Method 2
sudo iw dev wlan0
sudo iw dev wlan0 connect xx
sudo dhclient wlan0 or sudo dhcpcd wlan0
Note: If you set the essid iwconfig no response, sudo apt autoremove network-manager.

## how to connect wpa on command line
sudo wpa_supplicant -i wlan0 -c/etc/wpa_supplicant/wpa_supplicant.conf
sudo dhcpcd wlan0

## how to turn off gedit automatic backup
Open gedit, choose Edit->Preference->Editor, unselect "Create a backup copy of files before saving"

## how to display star wars movie on command line
telnet towel.blinkenlights.nl

## how to save error log
make>error 2>&1

## how to install lamp environment
sudo apt install apache2 php5 libapache2-mod-php5 mysql-server libapache2-mod-auth-mysql php5-mysql
sudo /etc/init.d/apache2 restart
Then enter this: sudo ls /etc/apache2/mods-enabled, see if there are php5.conf and php5.load, if not, try: sudo a2enmod php5

## how to install phpmyadmin
Download and unpack the phpmyadmin package.
sudo cp /var/www/phpmyadmin/config.sample.inc.php /var/www/phpmyadmin/config.inc.php
sudo vi /var/www/phpmyadmin/config.inc.php
Find "blowfish_secret" then enter any words behind it.
At last install php5-mcrypt
sudo apt install php5-mcrypt
sudo vi /etc/php5/apache2/php.ini
Modify like that:
extension php5-mcrypt.so

## how to delete more than one files
find -name "filename" -print|xargs rm

## how to change mysql data to sqlite data
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

## how to use mysql
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

## jre chinese garbled
http://blog.163.com/maaa_139/blog/static/31023991201051542321224/

## command x86_64-linux-gnu-gcc failed with exit status 1
sudo apt install libevent-dev

## how to calibrate touch screen
This operation must be under the X-window environment
First list all input devices, to find the touch screen id: xinput list
Then use the following command to adjust the touch screen parameters to my CF-19 notebook parameters as an example,
xinput set-prop 9 --type=float "Coordinate Transformation Matrix" 1.118 0 -0.09 0 1.16 -0.025 0 0 1
More: https://wiki.archlinux.org/index.php/Calibrating_Touchscreen

## how to install festival
sudo pacman festival festival-us

## can not find /dev/dsp
Add the following to HOME folder, save it as .festivalrc,
(Parameter.set 'Audio_Command' (aplay -q -c 1 -t raw -f s16 -r $SR $FILE))
(Parameter.set 'Audio_Method' Audio_Command)

## how to install wubi
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

## how to install xfce4
sudo pacman -S xfce4
startxfce4

## how to install x-window
First install the basic components: sudo pacman -S xorg-server xorg-xinit xorg-utils xorg-server_utils mesa
Then install window managers and terminal: sudo pacman -S xorg-twm xterm
Finally, enter the original X-window by: startx

## how to use mutt
First, install mutt: sudo pacman -S mutt
Then establish .mutt folder, to store data files
```
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
```
Finally, for safety, it is need to modify the configuration file permissions: sudo chmod 600 ~/.muttrc
References: http: //www.cnblogs.com/wangkangluo1/archive/2012/12/28/2837300.html

## how to install yaourt
First add yaourt source to /etc/pacman.conf,
```
[archlinuxcn]
#The Chinese Arch Linux communities packages.
SigLevel Optional TrustAll
Server http://repo.archlinuxcn.org/$arch
```
Then synchronize and install: sudo pacman -Syu yaourt

## how to install sound card
sudo pacman -S alsa-lib alsa-tools alsa-utils alsa-oss
Now you can use alsamixer command to adjust the volume
Note: Press m is for mute

## how to check battery
sudo pacman -S acpi
acpi power

## publickey permission deny
ssh-add yourkey "Not the .pub"

## how to modify git editor
git config --global core.editor vim

## git can not upload
1. Pull before push (Adviced)
git pull git@github.com:aaa/bbb.git master
git push -u git@github.com:aaa/bbb.git master
2. Force pushing (Danger)
git push -u git@github.com:aaa/bbb.git master -f

## git how to recall commit
git reset --soft HEAD^

## git how to reset
git log
git reset --hard <id>

## vim how to edit dos files
:e ++ff=dos

## vim how to delete same lines
:g/^\(.\+\)$\n\1/d

## vim how to get ascii
ga

## what is vim plugin folder mean
When Vim start, it will automatically execute the plugin folder, next it will execute the ftplugin(file type plugin) folder, autoload folder is used to store big *.vim files, only execute when function calls, it is used to make vim launch faster.

## how to make vim plug-in
First, in /etc/vimrc, "filetype plugin on" should be opened
Then in plugin, "au BufNewFile, BufRead, *.xx call set filetype=AAA" to set the file type
When open *.xx file, Vim will find AAA.vim and execute it.
In each *.vim file, function like filename#function() will call filename#function() in filename.vim
In plugin folder, "set syntax=BBB" will call BBB.vim in syntax folder to highlight the codes.

## vim how to flip pages
PageDown: Ctrl + f
PageUp: Ctrl + b

## vim how to match chinese
'[\u4e00-\u9fa5]'

## vim how to match english
'[\u0020-\u007E]'

## how to use vim historical views
Back: Ctrl + o
Forward: Ctrl + i

## how to find multiple files in vim
vimgrep /String/ ./*

## vim how to fold the code
First, add this in vimrc,
Set foldmethod=indent
Then, open the fold: l
Open all folds: zR
Close fold: zc
Close all folds: zM
Expand entire function: zO

## vim how to access system clipboard
Be sure to install the vim-gnome, otherwise you can not operate the system clipboard
sudo apt install vim-gnome
":reg" to see all clipboard contents in vim, the "+ is the system clipboard
Use command "+y to copied to the system clipboard, use command "+p to past from the system clipboard

## vim can not open plug-in help documentation
':helptags ~/.vim/doc'

## vim how to replace words
Replace a to b: :%s/a/b/g
Replace a to b from line n to line m: :n,ms/a/b/g

## vimwiki how to make a new line
Just type <br>

## vim how to read binary file
vi -b filename
:%!xxd

## gvim how to init
set guifont=Consolas::h12:cANSI
colorscheme darkblue
set nobackup
set encoding=utf-8

## how to init vim
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

## how to use nmap
nmap -sP 192.168.1.* Lists all online equipment segment
nmap -O 192.168.1.* detect operating system

## how to change mac address
If your net card is eth0
sudo ifconfig eth0 down
sudo ifconfig eth0 hw ether new_mac_address
sudo ifconfig eth0 up

## how to deal with jlink unknow device
Short connect the Erase pin and the TST pin longer.
It is less relationship to the order of short connection.

## how to install sdcc on ubuntu
sudo apt install sdcc
If it does not work, try this: sudo apt install gputils gputils-common gputils-doc sdcc sdcc-doc sdcc-libraries sdcc-ucsim

## cmu sphinx can not find libpocketsphinx.so.1
sudo apt install audacity
libpocketsphinx.so.1 problem will arise when you start pocketsphinx_continues. It mainly due to that sphinxbase did not be added to the library path environment variable
So we do: sudo vi/etc/ld.so.conf
Add this,
/Usr/local/lib
/Usr/local/lib/pkgconfig
Then, sudo ldconfig

## cmu sphinx failed to open audio device
sudo apt install pulseaudio

## cmu sphinx failed to calibrate voice activity detection
wake up the computer

## cmu sphinx pycapsule_getpointer called with invalid pycapsule object
install the new version, upper than 5prealpha

## python undefined symbol ps_update_lmset
sudo easy_install -m sphinxbase
sudo easy_install -m pocketsphinx

## expreval error when build coreseek
Edit sphinxexpr.cpp, line 1010, 1044, 1077, change T val ExprEval (this-> m_pArg, tMatch); to T val this-> ExprEval (this-> m_pArg, tMatch);
Note: the config file of sphinx does not support ~/but support/home/user

## how to install xml.vim
Copy xml.vim file to ~/.vim/ftplugin and then use ln -s command to create relationship between xml.vim and docbk.vim, xsl.vim, html.vim, xhtml.vim
Open ftplugin in vimrc
Tips,
Tag autocomplete: double-click > symbol
Auto new line: double-click ; symbol in INSERT mod
For more help, enter: help xml-plugin

## bochs dlopen failed for module x file not found
sudo apt install bochs-x

## libbx_x.so undefined symbol xpmcreatepixmapfromdata
added, display_library; sdl in bochsrc

## bochs error
If an error of bochsrc occured, the normal way is just comment the error line.
bochsrc use double quotes, not single quotes.
Use bximage to make image
sudo kpartx -a xx.img mount the image
sudo kpartx -d xx.img unmount the image

## how to mount qcow2
modprobe nbd max_part=63
qemu-nbd -c /dev/nbd0 image.img
mount /dev/nbd0p1 /mnt/image

## how to install ftp server on ubuntu
sudo apt install pure-ftpd

## git how to revert
git revert HEAD

## sqlite can not import data from text
Change text to sql file, then import.

## how to replace string in multiple files
sed -i 's/old/new/g' filename

## kvm how to use snapshot
Create snapshot: qemu-img snapshot -c snapshot_name image.qcow2
Show all the snapshot: qemu-img snapshot -l image.qcow2
Revert snapshot: qemu-img snapshot -a snapshot_name image.qcow2
Delete snapshot: qemu-img snapshot -d snapshot_name image.qcow2

## how to use lftp
Login: lftp name@site:port
Command: ls, cd, get, put, mirror -R

## how to sudo when boot up ubuntu
Just write sudo in /etc/rc.local, cause rc.local is executed by root.

## openwrt how to install ftp server
opkg update
opkg install vsftpd

## pico cms can not open sub page
Make sure the .htaccess file is in the main folder.
sudo vi /etc/apache2/apache2.conf, change "AllowOverride None" to "AllowOverride FileInfo Options"

## kvm how to create image
sudo qemu-img create -f qcow2  image.img 60G

## how to install kvm
sudo apt install qemu-kvm virt-manager bridge-utils libvirt-bin

## how to install vnc server
sudo apt install vnc4server
vncpasswd
sudo apt install xfce4
vi ~/.vnc/xstartup, annotate the old config, add new config,
```
#x-terminal-emulator -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" & 
#x-window-manager & 
sesion-manager & xfdesktop & xfce4-panel & 
xfce4-menu-plugin & 
xfsettingsd & 
xfconfd & 
xfwm4 & 
```
Start server: vncserver :1
Stop server: vncserver -kill :1

## how to wake up remote pc
wakeonlan -i ip_address mac_address

## how to mount raw
sudo fdisk -lu image.raw, find the first start number n,
echo $((n*512)), get N,
sudo mount -o loop,offset=N image.raw folder/

## can not use tab on terminal
vi ~/.config/xfce4/xfconf/xfce-perchannel-xml/xfce4-keyboard-shortcuts.xml
Change line <property name="<Super>Tab" type="string" value="switch_window_key"/> to <property name="<Super>Tab" type="empty"/>
sudo reboot

## vim how to save word in regular expression
:%s/\(str_1\) xx \(str_2\)/\2 or \1/

## vim how to remove duplicate rows
:sort
:g/^\(.*\)$\n\1$/d

## vim how to mismatch
'[^(your_regex)]'

## vim how to convert case
:%s/\(xx\)/\L\1/g (Lower)
:%s/\(xx\)/\U\1/g (Upper)

## how to install vim-markdown
Download and unzip vim-markdown
Edit /etc/vimrc, add,
set noncompatible
filetype plugin on

## how to remove encryption on ubuntu
First, backup: sudo cp -rp /home/your_name /home/your_name.bk
Then, reboot and login by root
rm -rf /home/your_name
mv /home/your_name.bk /home/your_name
rm -rf /home/.ecryptfs
rm -rf /home/your_name/.ecryptfs
rm -rf /home/your_name/.Private
sudo apt autoremove ecryptfs-utils libecryptfs0

## how to redirect the domain to github pages
Add CNAME file in github main folder, the context is the domain.
Then, the domain, add the github A Record,
192.30.252.153
192.30.252.154

## how to install chrome flash plugin on ubuntu
sudo apt install pepperflashplugin-nonfree
sudo update-pepperflashplugin-nonfree --install

## how to install firefox flash plugin on ubuntu
sudo apt install flashplugin-nonfree

## how to install a trash on ubuntu
sudo apt install trash-cli
Edit /usr/local/bin/trash-rm,
```
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
```
sudo chmod +x /usr/local/bin/trash-rm
Finally, add 'alias rm="trash-rm"' to ~/.bashrc
source ~/.bashrc

## can not find cdrom when install ubuntu
1. enter the command line when install
2. mount the U-disk
3. cd into U-disk then mount ubuntu.iso to /cdrom
At last, exit and continue install.

## kvm vnc can not connect
Edit the domain file of the virtual machine, modify 127.0.0.1 to 0.0.0.0, like that,
<graphics type='vnc' port='-1' autoport='yes' listen='0.0.0.0'>
<listen type='address' address='0.0.0.0'/>
</graphics>

## kvm how to clone
virt-clone -o {old_kvm_name} -n {new_kvm_name} -f {new_kvm_image_address}

## how to change terminal language
Edit /etc/default/locale,
LANG="en_US.UTF-8"
LANGUAGE="en_US:en"
Reboot.

## vim how to paste
:set paste
:set nopaste

## php can not write files
chmod

## how to transfer files through ssh
sudo mount -t cifs //ip_address/folder -o username=xx,password='xx',iocharset=utf8 ~/folder

## git how to check the difference
git diff (tree vs index)
git diff -cached (index vs commit)
git diff HEAD (tree vs commit)

## python how to install tkinter
sudo apt install python3-tk

## how to make system disk on linux
sudo dd if=system.iso, of=/dev/sdc

## centos can not connect to network
vi /etc/sysconfig/network-scripts/ifcfg-eth0
/etc/init.d/network restart

## vim how to edit multiple files
:args *.txt
:argdo %s/old/new/g | update

## how to unbind ip
ip addr del <ip> dev eth0

## how to run program on background
nohup <command> &

## how to show the dos break
:e ++ff=unix %

## how to create requirements.txt
pip freeze

## how to solve coding problem of python3
Str = Str.encode('unicode-escape').decode()

## what is forward compatibility and backward compatibility
Forward compatibility means forward version support current version, based on forward version.
Backward compatibility means current version support forward version, based on current version.

## how to make code easy to read
Just make it like nature language.

## how to quick develop
prepare a lot of modules, can help the conceptual product development become more quickly
a lot of equivalent alternative conditions can help locating and fixing the faults
rapid prototype development: I think focing on the special stage function and the speed is very important
rapid prototype development: do before speak!
do not keep coding for a long time, it will finally become very low effective. leave the computer for enough time will make it much better
without communication, without quick development

## how to cheat in half life
sv_cheat 1
god (God mode), impulse 101 (All weapons)

## can not printf on stm32 mdk
Target -> Use MicroLIB must be selected.

## how to install gstc-isp on ubuntu
When I run ./configure, there're some errors, so I did,
sudo apt install gnome-core-devel
sudo apt install gawk
When make, there are errors, too. So I did,
sudo apt install libvte-dev
Then edit src/main.c, alter the line to _#include <vte-0.0/vte/vte.h>_

## what is the meaning of flex
A lower power and upgraded timer or bus.

## dxp how to automatically check the pcb layout error
reports -> board information -> report

## what is dummy
It means virtual, null pointer.

## where to put the switch
Put in the positive pole, not GND, or the MCU will reboot again and again.

## ls can not work
Make sure the folder have "x" authority.

## which folders need backup
/boot
/etc
/home
/root
/usr/local
/opt
/srv
/var

## which folders do not need backup
/dev
/proc
/mnt
/media
/tmp

## how to copy with attributes
cp -a

## how to scp
scp local_file root@xx.xx.xx.xx:remote_folder

## what is pam
modules for linux security
auth: pam_securetty.so -> /etc/securetty -> pam_env.so -> pam_unix.so -> pam_secceed_if.so -> if not, pam_deny.so
account: pam_nologin.so -> /etc/nologin -> pam_unix.so -> pam_succeed_if.so -> if ok, pam_permit.so
password: pam_cracklib.so -> pam_unix.so -> md5, shadow -> if not, pam_deny.so
session: close pam_selinux.so -> pam_limits.so -> pam_loginuid.so -> open pam_selinux.so

## how to create account
vi /etc/group
grpconv
vi /etc/passwd
pwconv
passwd user
cp -a /etc/skel /home/user
chown -R usergroup /home/user

## how to distribute disk
use Quota or LVM

## how to mount
sudo mount dev folder

## linux kernel function
System call interface
Process control
Memory management
File System management
Device drivers

## how to make empty file
dd if=/dev/zero of=xx bs=100M count=1

## python simple http server
python -m SimpleHTTPServer 80

## how to reset time
date +"%Y%m%d %H%m" --set="20170101 1830"

## how to kill user
pkill -kill -t pts/x

## how to rm every file
find . -name "xx" | xargs rm -f

## how to release port
lsof -i :8000
kill -9 <pid>

## how to update pip
pip install -U pip

## how to mount ntfs
sudo mount -t ntfs /dev/sda1 /mnt

## how to modify apt source
sudo vi /etc/apt/source.list

## how to get memory status
free -h

## how to check ubuntu version
lsb_release -a

## how to combine files
cat file1 file2 > file

## how to split file
split -b 10k filename

## how to rename multiple files
rename 's/old/new/g' *.txt

## vim how to open multiple files
vi -o file1, file2, file3

## vim how to edit multiple files
:args *.txt
:argdo %s/old/new/g

## how to clean git log
git checkout --orphan xx
git add -A
git commit -am "clean"
git branch -D master
git branch -m master
git push -f

## how to set ssh timeout
edit /etc/profile, modify TMOUT=0
source /etc/profile

## vim how to format json
:%!python -m json.tool

## python how to format json
json.dump(dict, fp, indent=4)

## how to awk
awk -F ',' '{print $4}'

## shell how to count lines
wc -l

## linux how to check badblocks
badblocks -v /dev/sdb

## vim how to search multiple keywords
/aaa\|bbb\|ccc

## how to auto lock ubuntu
sudo apt install xscreensaver

## how to enable rc.local on ubuntu
ln -fs /lib/systemd/system/rc-local.service /etc/systemd/system/rc-local.service
touch /etc/rc.local
chmod 755 /etc/rc.local

## how to find files on linux
find -type d -name xx -user mark -perm 775 -regex ‘^.*$’ -size +10k -mtime +60

## how to shutdown on linux
shutdown -h now
shutdown -r now
shutdown -h 23:30
shutdown -h +15

## how to know the current user on linux
who
who am i

## how to create a shortcut on linux
ln -s file link

## how to cut
cut -d ':' -f 1

## how to check memory on linux
free -h

## how to replace string by tr
cat xx | tr "aa" "bb"

## how to delete string by tr
cat xx | tr -d "xx"

## how to combine files on linux?
cat xx* > out.txt

## how to show user info on linux?
finger username

## how to set selinux?
sestatus
getenforce
setenforce 0/1

## how to split a file on linux?
chsh -l
chsh

## how to write strings to other terminals on linux?
write user pts/2

## how to check user last login on linux?
lastlog -u username

## how to change line break on linux?
unix2dos -k filename
dos2unix -k filename

## where is the linux password files?
etc/passwd
etc/shadow
etc/group
etc/gshadow

## how to set the cli welcome page on linux?
vi /etc/issue

## where is the doc files on linux?
usr/share/doc/

## how to check the kill signal?
kill -l

## kill command can not work
try "kill -9"

## how to check bootup services on linux?
service --status-all

## how to block url by iptables?
iptables -I INPUT -p tcp -m string --string "xx.com" --algo bm -j DROP
iptables -I INPUT -p udp -m string --string "xx.com" --algo kmp -j DROP

## how to copy only newer files on linux?
cp -u

## how to copy without links on linux?
cp -d

## how to copy multiple files on linux?
cp a b c 

## how to show the partition info on linux?
parted /dev/sda print

## how to make iso on linux?
mkisofs -r -v -o xx.img folder

## how to cut strings on linux?
cut -d , -f 3 filename

## how to sort lines on linux?
sort filename

## how to delete the same lines on linux?
uniq filename

## how to show current user on linux?
users

## how to show current group on linux?
groups

## how to check virtual memory on linux?
vmstat

## how to check file attributes on linux?
stat filename

## how to check current tty on linux?
tty

## how to set group on linux?
groupadd group
groupmod -g 201 -n group2 group1
gpasswd group
gpasswd -A user group 
gpasswd -a user group
groupdel group

## how to set user on linux?
useradd user
useradd -u 755 -g users xx
useradd -r xx 
usermod -c This is xx user
usermod -e 2020-12-31 user
userdel -r user

## how to cleanup iptables?
iptables -F
iptables -X
iptables -Z

## how to backup and restore iptables?
iptables-save > txt
iptables-restore < txt

## how to get system boot up time?
systemd-analyze

## how to get host info?
hostnamectl

## how to compress video by ffmpeg
ffmpeg -i input.mp4 -s 1280x720 -vcodec libx264 -b 800000 out.mp4

## how to set sudo without passwd
sudo update-alternatives --config editor
sudo visudo
Under line %sudo, add "name ALL=(ALL) NOPASSWD:ALL"

## how to check all cpus in top command
press "1"

## dpkg how to remove multiple pkgs
dpkg -l | grep "<your_keyword>" | cut -d' ' -f3 | sudo xargs dpkg --purge

## how to enable rc.local on ubuntu18
ln -fs /lib/systemd/system/rc-local.service /etc/systemd/system/rc-local.service
touch /etc/rc.local
chmod 755 /etc/rc.local

## how to fix apt
sudo rm /var/lib/dpkg/info/*

## apt not fully installed
dpkg --remove xxx

## how to show graphics card on linux
sudo lshw -c display

## how to ln
ln -s file link

## how to remove bazel
rm -fr ~/.bazel ~/.bazelrc

## python how to not match
[^xx]* (must contain *)

## python regex how to save middle string
use (.*)

## how to run python in git bash
winpty python

## how to change hostname on ubuntu
Edit /etc/cloud/cloud.cfg, set preserve_hostname to true.
sudo hostnamectl set-hostname xxx

## how to list files in tar
tar -tf xx

## pip how to use china origin
-i https://pypi.tuna.tsinghua.edu.cn/simple

## how to get domain ip
host google.cn

## how to use tcpdump
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

## how to change vim theme?
colorscheme xxx

## python how to get object size
sys.getsizeof(xx)

## selenium can not find xpath
watch the page source if there is the element

> [knowledgeQA end]
