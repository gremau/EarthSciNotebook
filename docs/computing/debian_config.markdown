DebianConf.markdown
===================

This documents my maintenance routines and personal configurations of Debian and other software on this laptop. Useful web documents are listed in each section, and additional information is available in the main reference and other support documents.

## Debian references
* Ref manual: <http://www.debian.org/doc/manuals/debian-reference/index.en.html>
* Debian FAQ: <http://www.debian.org/doc/FAQ>
* Debian wiki: <http://wiki.debian.org>
* Index of other support: <http://www.debian.org/support>

## SOURCES
Currently tracking testing. Not using the name (jessie)

Other entries in sources.list:

    # The liquorix kernel
    deb http://liquorix.net/debian sid main - for liquorix kernel

    # The experimental debian repo - used for a few packages
    deb http://ftp.debian.org/debian/ experimental main contrib non-free

REMEMBER: After updating sources.list, run `apt-get update`


## KERNELS, LIQUORIX and others

Excellent resources for Debian Kernels:

* <http://kernel-handbook.alioth.debian.org>
* <http://www.debian.org/doc/FAQ/ch-kernel.en.html>
* <http://wiki.debian.org/KernelFAQ - for general info>

The kernel installed by default in the netinst installation is a somewhat generic(not optimized) kernel, so it may be useful to replace it. Though the debian installer installed the correct kernel for my architecture, in some cases one may want to look at other options in the repositiories.

`apt-cache search linux-image` (or `-headers`) should list the available kernels for your achitecture, as well as additional kernels with special featuresets. Install both the linux-headers and the linux-image package you desire.

The Debian kernel was replaced with the "high performance" liquorix kernel package. Liquorix is a Debian repository for Zen-kernel builds.

See: <http://www.liquorix.net> & <http://zen-kernel.org>

1. Place `deb http://liquorix.net/debian/ sid main`in sources.list
2. Run `apt-get update` and install liquorix-keyrings package.
3. Look at current kernel version: `uname -r`
4. To find newer liquorix kernel: `apt-cache search liquorix`
5. Install headers and image for 2.6.xx-0.dmz-liquorix-amd64 (should take a while).

The first time I did this binutils, gcc, and a couple of libs were pulled in.

Liquorix kernels can also be installed and upgraded with the smxi script (smxi.org)

Kernels from Debian or other repos can be customised using the kernel-package program. See <http://www.debian.org/doc/FAQ/ch-kernel.en.html>

## VPN configuration

OpenConnect is the open source project allowing connection to Cisco AnyConnect networks, but there are other vpn options. Installing the package below installes the openconnect package and the NetworkManager plugin. 

<https://github.com/cboettig/berkeley-linux-config/blob/master/vpn.md>

    apt-get install network-manager-openconnect-gnome

You can also use openconnect on the commandline, for example:

    openconnect ucbvpn.berkeley.edu

## KERNEL MODULES

Upon startup, UDEV detects hardware and loads needed modules into the kernel. These loaded modules can be viewed with `lsmod` and loaded manually (removed) with "modprobe (-r)"

It is possible to force or prevent the loading of a module by listing the name of these modules in one of these files:

* /etc/modules-version (version is the kernel version)
* /etc/modules-major (major is the major kernel version - 2.6)
* /etc/modules

Modules can also have parameters and arguments passed to them with these files.
The SMXI script also has a procedure for adding and removing particular modules.

###INSTALLED KERNEL MODULES:
 
`hdaps` - advanced harddrive protection for thinkpads.
(tp-smapi no longer supported by new thinkpads, see: <http://www.thinkwiki.org/wiki/Tp_smapi>)

1. Liquorix kernels come with `tp_smapi` and `hdaps` modules compiled

2. Load now with `modprobe -a tp_smapi hdaps`, OR

        $echo 'tp_smapi' >> /etc/modules
        $echo 'hdaps' >> /etc/modules

3. Add these lines to /etc/modprobe.conf/local.conf

        options thinkpad_ec force_io=1
        options hdaps invert=1

4. Set charging threshholds, `tp_smapi` needs sysfsutils

        $ apt-get install sysfsutils

5. AND add these lines to sysfs.conf:

        devices/platform/smapi/BAT0/start_charge_thresh = 30
        devices/platform/smapi/BAT0/stop_charge_thresh = 85

6. Also install hdapsd to run HDAPS from userspace. This will pull in `tp-smapi-dkms` and `dkms` (debian versions of these modules), but I subsequently removed `tp-smapi-dkms`. 

## UPDATES and UPGRADES

Generally, use apt-get (not apt-get):

    apt-get update
    apt-get safe-upgrade  # OR dist-upgrade (same as full-upgrade)

The reference suggests that apt-get dist-upgrade may be more suited to major upgrades (between releases, stable to testing, etc)
<http://www.debian.org/doc/FAQ/ch-uptodate.en.html>

## Google Drive

Use the drive package here: <https://github.com/odeke-em/drive>

Someone has made a Debian package for this, see: <https://github.com/odeke-em/drive/blob/master/platform_packages.md>
	
## SMXI.org MAINTENANCE SCRIPTS

See SMXI.org and <http://techpatterns.com/forums/forum-34.html>

Install scripts using:

    cd /usr/local/bin && wget -Nc smxi.org/smxi.zip && unzip smxi.zip && smxi

Upon installing and running the script it asks a bunch of configuration questions. Add these options:

1. Use liquorix kernel
2. Use apt-get
3. Set distribution to testing 
4. Use full-upgrade instead of safe

These options can be reset by erasing `/etc/smxi.conf`

Upon reaching the main menu (after upgrades), there are several options:

1. Install packages (non-free stuff, large packages, etc)
2. Remove packages (remove unneeded packages  - bluetooth, gnomemeeting, etc)
3. Clean up stuff
4. Miscellaneous tweaks (tweaks to mozilla, change script config, etc)
5. Virtual machine installer
6. Kernel options (install new kernels, add/remove modules)
7. Continue to graphics installer
8. Restart X/desktop
9. Stop Script 

So far have done these actions:

* apt cleanups
* removed unneeded xorg modules
* installed google-earth

##  SUDO 
Sudo is installed by default. Privileges are granted through the `/etc/sudoers` file, which must be edited with visudo. I added these lines to the sudoers file:

    User_Alias	ADMINS = greg   # Under 'User alias specification'
    ADMINS ALL = ALL            # Under 'User privilege specification'

To create a list of administrator accounts and grant myself sudo access to all commands.

### Other options

* Aliases to individual commands can be added with `Cmnd_Alias` statements and these can be added to User privilege specifications also (instead of ALL)
* To maintian syntax highlighting when using sudo from the terminal I used 2 approaches:

    1. Add these to sudoers file (with visudo):

            Defaults        env_keep += "HOME COLORFGBG LS_COLORS"
            Defaults        env_reset

    2. create `.bash_aliases` file and add `alias sudo='sudo '` to it.


##  CONNECT TO DATA PARTITION (sda5)

Add this line to fstab:

    # mount /dev/sda5 as /home/greg/data
    UUID=79faee16-4164-4fcc-b19c-499084c3764f /home/greg/data ext4 defaults 0 2


## CONNECT TO NETWORK DRIVE (NAS)

A NAS drive can be browsed and edited a variety of ways. Note that there are a number of users using the <share-name> share. Mounting the drive with CIFS can be done with these steps:

1. Create the `/media/nas_name/` directory

2. This command (as root) should mount the drive:

        mount -t cifs //<ip-address>/<share-name> /media/<mntpt-name> -o nounix,user=greg,file_mode=0777,dir_mode=0777

3. There is a script (`~scripts/mount_nas.sh`) that can be run with sudo to mount the drive.

4. Unmount with:

        sudo umount /<mntpt-name>/

5. This drive is also available by ssh using:

        ssh -l <username> <ip-address>

Network drives can also be mounted with gvfs, as long as `gvfs-backends` is 
installed (this contains a gvfs-smb package).

Rsyncs to this drive can be done through ssh for backups.

## PRINTING to NETWORK PRINTERS

See: <http://wiki.debian.org/SystemPrinting>, cups help screens in <http://localhost:631>

1. Install cups, cups-client, and foomatic printer driver packages (these should most likely already be here)
2. Start cups with `/etc/init.d/cups start`
3. Navigate to http://localhost:631/

    There should be a web interface to cups here where it should be possible to add a printer.

    1. Administration(login as root)-->Add Printer-->
    2. HP LaserJets are usually on AppSocket protocol using port 9100, so select this option from the bottom of this list (below network printers).
    3. Enter `socket://<ip-address>:9100/` for the URI connection
    4. Name the printer with human readable identifiers.
    5. Select make and driver (HP LaserJet4250 Foomatic/Postscript for BowlingLJ).
    6. Add printer.
    7. Set Default options (two sided, etc)
    8. You can now set this printer as default if desired.

## SSH

`openssh-client` should be installed for ssh access to remote hosts. For added security, it is best to use public/private keys during ssh sessions. To do this:

1. Generate a public/private ssh key pair with `ssh-keygen -t rsa -b 4096 -C "email address"`
   
    This will put a public/private key pair in the `~/.ssh` directory. You will be asked for a passphrase, which will be needed when sending the public key to a host computer.

2. Copy the public key to a remote host using `ssh-copy-id user@hostid`, or by manually appending the public key to the hosts `.ssh/authorized_keys` file, like:

    cat ~/.ssh/id_rsa.pub | ssh user@server 'cat >> .ssh/authorized_keys'

3. `ssh-agent` can save the passphrase for your public key, just use `ssh-add ~/.ssh/id_rsa`. Ive never gotten this to work in XFCE. Needs to be done at the creation of the desktop or bash session, but I'm not sure how this works. Try using `keychain`, `seahorse`, etc for this. Or read this -> <https://wiki.archlinux.org/index.php/SSH_Keys> or the GitHub tutorial.

4. Make a list of hostnames and ips in `/etc/hosts` for easier access to frequenly accessed hosts.

## THUNDERBIRD

1. Install thunderbird
2. run `icedove -profilemanager`, create a profile and point it to the profile in `~/data/thunderbird-profiles/pu3xvoh`
    - alternatively, just move the profile folder into `~/.thunderbird` and edit the `profiles.ini` file to point to that folder (pu3xvoh.default)

## Python for data analysis

Download miniconda from here: <https://conda.io/miniconda.html> and run with

    bash <miniconda-file-name>

Conda is the package manager and `conda install <package-name> will install packages. To keep conda install small by cleaning out tarballs and old packages use `conda clean -tp`.

The anaconda distribution also includes pandoc, which plays well with the system Tex distribution.

## R

Install with apt. There are other ways, as with conda, but this seems easier. Conda does not have all the packages I need.

    sudo apt-get install r-base r-base-dev

To run R in Jupyter notebooks install [IRKernel](https://irkernel.github.io/installation/#linux-panel) using the linux source method (libzmq3-dev first).

Then use install.packages('xxx') to get packages, and remember that R updates will require package reinstallation.

Often R complains about missing Debian packages (curl, ssl) and may fail if miniconda/anaconda is already installed (may want to change dir name).

Common packages: tidyverse, xts, rgdal, data.table, automap

## MATLAB

Matlab installer for linux is pretty straightforward these days. MATLAB can be installed in /usr/local/ unless there is not enough space (3-6 GB depending on toolboxes).

To get a desktop launcher in the menu (with icon), do:

	sudo wget http://upload.wikimedia.org/wikipedia/commons/2/21/Matlab_Logo.png -O /usr/share/icons/matlab.png

then make a matlab.desktop file in /usr/share/applications/ that points to the icon and executes `matlab -desktop`

## GDAL

May be required for rgdal and other stuff (qgis should bring this in I think).

sudo apt-get install libproj-dev libgdal-dev

## TeX

I install the `texlive` package from debian repositories. It is smaller than `texlive-full`, but still very functional. For use with pandoc I also install...

## WIFI

See <http://wiki.debian.org/WiFi> , <http://wiki.debian.org/iwlagn> , and <http://wiki.debian.org/WiFi/HowToUse>

1. Need iwlwifi modlule loaded into kernel

   This requires firmware (non-free package is `firmware-iwlwifi`) to be installed

2. Also install `wireless-tools` package
3. Verify device is accessible with `iwconfig`
4. Raise interface with `ifconfig wlan0 up`
5. Configure wireless interface with network-manager or wicd
6. Be sure to point wicd to wlan0

### Other steps



## CONSOLE BEEPS

1. Stop console beeps while in X with (as root) `xset b off`
2. Stop console beep on gdm login screen using `gdmsetup` program

    OR uncomment `set bell-style none` in `/etc/inputrc` for a permanent solution in consoles.

    OR blacklist the kernel module by adding `blacklist pcspkr" to /etc/modprobe.d/blacklist.conf


## SCREEN MANAGEMENT
arandr provides screen management (frontend for `xrandr" commands).
VGA 1 is the VGA port on the side of the laptop, LVDS1 is the laptop's screen


## URXVT and other X configs
Setting preferences for X and X applications can be done using .Xdefaults and .Xresources files. See https://wiki.archlinux.org/indes.php/Xdefaults. After adding something to these files use `xrdb -merge ~/.Xdefaults/Xresources".

urxvt is a nice light terminal to replace xterm, but it pays to configure its default colors:

Create ~/.Xdefaults
Add a bunch of lines with color definitions and other URxvt config options
I used the wiki at http://crunchbanglinux.org/wiki/urxvt
Also see wiki.archlinux.org/index.php/Rxvt-unicode

## VIM

Installed vim with vim-gtk3
Configured in .vimrc using the Brad Moolenar example from vim website
Added `set nobackup" to keep annoying backup files (file.txt~) away.

##BITTORRENT SYNC

1. Download binary from http://labs.bittorrent.com/experiments/sync.html
2. Extract binary and move to desired folder (probably /usr/local/installed)
3. Run with './btsync'
4. Access user interface at http://localhost:8888/gui/

May want to autostart this

## DIGITAL CAMERA

I installed Shotwell as a photo organizer
This relies on libgphoto2 to communicate with my Canon cameras, it all seems to work as long as this is installed.
Gphoto2 can be used to access cameras on the command line.

## OTHER STUFF

Installing .deb files:
Debian packages (.deb files) can be downloaded from various sources. They can be unpacked and installed with `dpkg -i ..."
If the .deb fails to install read the dependency output and install the required dependencies and then reinstall.

Getting information about packages:
`apt-cache showpkg ..." gives very detailed info about packages, dependencies, etc.
`apt-cache policy ..." gives info about the repositories a package is in
`apt-get show ..." gives general info about packages, good for prior to install"apt-cache search ..." searches for a package
`apt-get install -s ..." simulates the install of a package

Viewing logs: 
All logs are in /var/log/. They can be viewed in a terminal using less, more, etc. `tail /var/log/..." shows the last 10 lines of a log. "tail -f /var/log/... follows the log and updates the display as it is appended.



## OTHER PACKAGES to install
* xorg
* openbox
* obconf
* xfce4
* zotero extension - point to ~/data/literature/zotero in prefs
* gnumeric
* abiword
* libreoffice writer, calc, impress
* libreoffice-gtk (helps with desktop integration)
* htop
* powertop
* vim-gtk - set prefs with .vimrc (use moolenaar example)
* google-earth - installed with smxi
* chromium-browser
* gimp
* numpy
* scipy
* matplotlib
* ipython
* shotwell
* rdesktop (remote desktop for windows access)
* mpd (music player daemon)
* gmpc (client for music player daemon)
* hpodder (podcatcher)

