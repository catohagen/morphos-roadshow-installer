This is a quick fix for the Roadshow 68k TCP/IP stack included installer that fails to work on MorphOS, so i wrote my own.

Its written in Arexx scripting language, maybe not the best way to do an installer, but for now it works.

advantages over the orginal installer :

* skips all files not related to Morphos (amiga hardware config files) that the orginal installer would copy.
* You can also skip to install the included Firewall, normally not needed if you have a good router.
* You can skip to install Documentation and PPP/PPPoe drivers for ADSL modem users.

* It finds and uses your existing config files for nameserver(dns) and hosts and imports directly
  into Roadshow config files (you choose if you want)

* After you installed a hardware device config file for your hardware, it asks and loads the installed
  config file into editor, so you dont have to search and manually edit the file, the provided
  default configfiles have commented examples and comments, so its easy to edit what you need.

* You can import your existing nameserver(dns) and hosts file directly into Roadshow files,
  no editing of individual files(optional, it asks)

* Another important feature it has, is the tuning of internal tcp settings, Roadshow default tcp settings
  are not very efficient in routers today because when the TCP/IP kernel used by Roadshow was still new,
  routers had low much lower packets than today, so you will see a 3-4 increase of throughput by adjusting tcp settings.
  Using your input about your line speed and round-trip-time or ping, it can calculate better tcp.sendspace and tcp.recvspace
  so you will get much faster browsing responsivness and transfer rates over the web.
  On my 60/60mbit line, i got ~1MB/s with default tcp settings, and ~4.5MB/s both in OWB and wget 1.9.1 after
  this installer calculated my tcp settings.

It will not work correctly if :
* if/when you manually installed Roadshow, you put c:addnetinterface directly in user-startup.
* if you have disabled Morphos internal Netstack by renaming MOSSYS:S/network-startup some other name.
Installer tries to rename MOSSYS:S/network-startup to MOSSYS:S/network-startup.off when you trigger the installer to enable Roadshow.


** So make sure the file "network-startup" exist a MOSSYS:s/ and delete any existing "network-startup" in S: before you start installing **

For best results with this installer, its best to remove your manual installation, especially making sure there is no
Roadshow startup files or lines added in user-startup or startup-sequence, Morphos internal Netstack should be enabled
too, installer will disbale the internal Netstack startup but can also enable it if you want it back, incase you want to go
back to orginal configuration/system of Morphos incase there is an update.

** INSTALLATION WITH THE INSTALLER **

first you need the Roadshow 68K archive and extract it somewhere (ramdisk is a good place)
then you need the Roadshow MorphOS update, extract this to where you extracted Roadshow 68K
then copy this installer to where you extracked Roadshow 68K

ram:Roadshow should look like this

Ram Disk:Roadshow> list
Install_Roadshow_MorphOS.txt      4412 ----rwed Today     10:13:14
Install_Roadshow_MorphOS.info     8262 ----rwed Today     10:13:14
Install_Roadshow_MorphOS         18841 ----rwed Today     10:13:14
Roadshow-Update-MorphOS.info       628 ----rwed 15-Jan-80 13:58:14
Roadshow-Update-MorphOS            Dir ----rw-d 15-Jan-80 13:59:32
Workbench                          Dir --p-rwed 10-Jan-80 14:04:08
version                             31 ----rw-d 19-Jan-80 10:02:14
ReadMe.info                        464 ----rw-d 20-Nov-10 11:40:06
ReadMe                            8596 ----rw-d 19-Jan-80 11:14:28
Installer                       109956 ----rwed 15-Nov-10 11:01:20
Install_Roadshow.info              698 ----rw-d 21-Nov-10 10:06:16
Install_Roadshow                 19490 ----rw-d 01-Jan-80 17:47:28
Install-Extras                     Dir ----rwed 01-Jan-80 14:31:24
Documentation                      Dir ----rw-d 08-Dec-80 10:21:08
Documentation.info                 628 ----rw-d 20-Nov-10 11:40:06
11 files - 4 directories - 172006 bytes used

Open a shell and cd to where you extracted Roadshow and Roadshow MorphOS update

type : rx Install_Roadshow_MorphOS to start (clicking icon should work too, resize the shell that pops up if its too small)


The installer will help you install Roadshow 68K and spesific files you select depending on what hardware you have.

*For a Morphos system you need to do atleast step [1] and [2 or 3 or 4 or 5] depending what network card you have, and option [e] *

Option 1 installs all the basic stuff that Morphos needs, no files or settings for amiga hardware will be installed.

Option 2 installs files spesific to Apple Hardware with the SunGEM ethernet (Macmini and Powerbooks)

Option 3 installs files for Pegasos I & II with the VIA Rhine ethernet.

Option 4 installs files for Efika and the internal ethernet

Option 5 Installs files for Pegasos II Marvell Discovery Gigabit network driver

Option 6 Installs Realtek-RTL8139 PCI card configuration network driver

Option 7 copies the Roadshow documentation to SYS:Docs/Roadshow68K
Option 8 installs The IPFILTER (IPF) Firewall, once installed you need to manually configure it and start it

Option 9 installes PPP/PPPoE device drivers spesific to ADSL users



Configuration :

More settings related options are :

Option [s] runs through a setup that requires you enter informantion about your network, you need to know your connection speed
and round-trip-time (ping) your connection have. Adjusting these isnt required but can boost your browsing experience.

I have seen a good increase in performance locally on my Macmini and Powerbook, getting file transfers at 11.8 MB/s on the macmini
and 35 MB/s on the powerbook when copying from/to different machines in the lan.

Option [e] lauches the Morphos internal editor (mossys:c/ed) and loads up config files required for your local settings.
           You will be asked if you want to import your existing Netstack configurations for nameservers(dns) and hosts
           If you want to use DHCP you can skip this step, as Roadshow will try and get all the relevant info it needs from your router.
           You need to know your : gateway (usally your routers ip)
                                   dns     (usally your routers ip)
                                   ip      (for your machine)

Please read the Roadshow documentation if you need more information.


To install a working arexx, try this

1. use this url : http://aminet.net/search?content=rexxsyslib.library
2. download any package, they should have rexxsyslib.library inside
3. copy rexxsyslib.library to MOSSYS:libs/ (rename or overwrite the non working morphos one)
4. reboot and arexx scripts should work.

