First, install jailbreak and then usbnetwork following instructions in: https://www.mobileread.com/forums/showthread.php?t=88004  

Then, activate usbnetwork state. In search box in your kindle dxg (home -> menu -> search) type without quotes:  
1. `;debugOn` and press enter  
2. `usbNetwork` and press enter  

These commands will allow you to access kindle dxg from network. drivers for new network card for winxp can be found here: http://www.davehylands.com/linux/gumstix/usbnet/linux.inf  
Kindle's IP address will be 192.168.2.2 (don't forget to accordingly configure your new (kindle's) internet connection's settings, that is to set same mask IP, for exemple 192.168.2.1)  

After doing that you'll be able to telnet 192.168.2.2 your kindle and access it's linux console.  
So using that console you will be able to access and change mentioned files.  

Be careful and don't edit/move/delete/rename wrong files, because it could result in your kindle not booting up.  

