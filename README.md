
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

* Another important feature it has, is the tuning of internal tcp settings, using your input about
  your line speed and round-trip-time or ping, it can calculate better tcp.sendspace and tcp.recvspace
  so you will get much faster browsing responsivness and transfer rates over the web.
  (on my 60/60mbit line, i got ~1MB/s with default tcp settings, and ~4.5MB/s after this installer calculated my tcp settings)

Read Install_Roadshow_MorphOS.txt 
