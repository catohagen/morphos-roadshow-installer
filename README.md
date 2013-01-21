morphos-roadshow-installer


Quick Morphos installer for Roadshow 68K TCP/IP stack v1 (19.01.2013) by catohaghen@fastmail.fm


Since the orginal included installer for Roadshow doesnt work properly on Morphos, so I wrote one in arexx.

This installer will skip the amiga hardware spesific files, as it was written for Morphos systems.

You can also skip the firewall, the PPP/PPPoE files for ADSL and documentation.

You can also use this installer to tune Roadshow internal settings, it will try to calculate better
values based on your linespeed and rtt, since the default Roadshow settings are kinda low as they
where probably intended for low memory 68K classic amiga systems.


**You need a working arexx installation to use this installer**


first you need the Roadshow 68K archive and extract it somewhere (ramdisk is a good place)
then you need the Roadshow MorphOS update, extract this to where you extracted Roadshow 68K
then copy this installer to where you extracked Roadshow 68K

ram:Roadshow should look like this

Ram Disk:Roadshow> list
Documentation.info                 628 ----rw-d 20-Nov-10 11:40:06
Documentation                      Dir ----rw-d 08-Dec-80 10:21:08
Install_Roadshow                 18658 ----rw-d 22-Nov-10 09:59:08
Install_Roadshow.info              698 ----rw-d 21-Nov-10 10:06:16
Installer                       109956 ----rwed 15-Nov-10 11:01:20
ReadMe                            7164 ----rw-d 09-Dec-80 09:53:50
ReadMe.info                        464 ----rw-d 20-Nov-10 11:40:06
Workbench                          Dir --p-rwed 24-Oct-10 09:55:32
Roadshow-Update-MorphOS            Dir ----rw-d 15-Jan-80 13:59:32
Roadshow-Update-MorphOS.info       628 ----rwed 15-Jan-80 13:58:14
Install_Roadshow_MorphOS         15289 ----rwed Today     14:49:19
Install_Roadshow_MorphOS.info     8173 ----rwed Today     14:52:32
Install_Roadshow_MorphOS.txt      2453 ----rwed Today     15:29:31

Open a shell and cd to where you extracted Roadshow and Roadshow MorphOS update

type : rx Install_Roadshow_MorphOS to start (clicking icon should work too, resize the shell that pops up if its too small)



The installer will help you install Roadshow 68K and spesific files you select depending on what hardware you have.

*For a Morphos system you need to do atleast step [1] and [2 or 3] and option [e] *

Option 1 installs all the basic stuff that Morphos needs, no files or settings for amiga hardware will be installed.

Option 2 installs files spesific to Apple Hardware with the SunGEM ethernet (Macmini and Powerbooks)

Option 3 installs files for Pegasos I & II with the VIA Rhine ethernet, if you have a realtek card you just install with option 3
         and when asked for configuring settings you change 'device=via_rhine_pci.device' to rtl_8139pci.device instead.

Option 4 copies the Roadshow documentation to SYS:Docs/Roadshow68K
Option 5 installs The IPFILTER (IPF) Firewall, once installed you need to manually configure it and start it

Option 6 installes PPP/PPPoE device drivers spesific to ADSL users



Configuration :

More settings related options are :

Option 7 runs through a setup that requires you enter informantion about your network, you need to know your connection speed
         and round-trip-time (ping) your connection have.
   Adjusting these isnt required but can boost your browsing experience.

         I have seen a good increase in performance locally on my Macmini and Powerbook, getting file transfers at 11.5 MB/s on the macmini
         and 35 MB/s on the powerbook when copying from/to different machines in the lan.

Option [e] lauches the Morphos internal editor (mossys:c/ed) and loads up config files required for your local settings.
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
