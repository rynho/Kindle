From ooommm (https://www.mobileread.com/forums//showthread.php?t=60006&page=3)

I succeeded changing amazon's SIM card in my kindle dx graphite to my local GSM provider's sim and getting online  

This is what I did:  
1. changed sim card in kindle
2. commented these lines in `/opt/amazon/ebook/config/browser_prefs`
```
#settings.proxy.hostname = fints-g7g.amazon.com
#settings.proxy.portnumber = 80
#settings.proxy.sslportnumber = 80
```
BTW, if you don't want your kindle to be recognized online as mobile device, change browser identification string in the same file to smt like this:
`user_agent.base = Mozilla/4.0 (compatible; Linux 2.6.22)`
3. changed DNS server's ip addresses to my GSM provider's in `/etc/resolv.d/resolf.conf.3`
4. changed some settings in `/etc/ppp/chat/connect-3` to be compagtible with my GSM provider's settings (dialing number and AT+CGDCONT connection string)
5. rebooted kindle and thats it! internet worked 

## some question
I found some thing here but it seem not working: http://wiki.openmoko.org/wiki/Manually_using_GPRS  
PS: I am not sure CHAP or PAP so I put username and pass to both files.  

## some answer
you can try the following:  
1. add user/password in `/etc/ppp/{chap,pap}-secrets`
2. in `/etc/ppp/peers/peer-3` comment line `noauth`  
3. add line (username to use for authentication, should match "client" in `/etc/ppp/{chap,pap}-secrets`):  
`user "change_this_to_your_username"`

You can also try to modify `peer-4` and `connect-4` according to your GSM provider, because kindle could use those files for connecting. I'm not sure how it chooses which peer/connect number to use  

If that don't help, you can turn on pppd debug mode and see whats going wrong. to enable debug mode enter these two lines in `/etc/ppp/peers/peer-3`:  
```
debug
logfile /mnt/us/pppd_log.txt
```

Then try to restart/connect to gsm network and read the log file.
