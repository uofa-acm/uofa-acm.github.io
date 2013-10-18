---
layout: post
title: Web App Security
smalltext: Joshua Koike
tags: talk
---
This week, Josh will be presenting a basic introduction to web application \(and site\) security. 
While not designed to be an all-encompassing presentation, this talk will hopefully provide you with 
a basic understanding of the most common attacks against web applications, using DVWA 
\(Damn Vulnerable Web App\). This talk will use live exploits against intentionally vulnerable 
targets, so networking setup will be important. There is quite a bit of setup for this talk, so
email me at <jkoike@email.arizona.edu> if you get confused. I will respond as quickly as I can.

##SETUP:

1. Download and install [VirtualBox](https://www.virtualbox.org/wiki/Downloads) \(Free\), or [VMWare Workstation/Fusion](http://www.cs.arizona.edu/computing/facilities/vmap.html) \(Recommended\)
2. Download [Metasploitable](http://sourceforge.net/projects/metasploitable/files/Metasploitable2/)
3. \(Optional\) Download a linux \(or other, I don't really care\) operating system to work in. A 
later talk on buffer overflows will require a linux virtual machine to work in. \(hint\)
4. \(Optional\) Download [WebGoat](http://sourceforge.net/projects/owasp/files/WebGoat/WebGoat%205.2/).
I don't know if there will be enough time to cover this, but it's still a good resource.
5. Unzip the Metasploitable package to somewhere where you can find it\(e.g. into your documents, ect.\)
 *At this point, instructions will be different, depending on whether you installed VMWare or VirtualBox.*
 
 ####For VMWare Users:
 1. In the menu bar at the top: File > Open
 2. Browse to the directory where you unzipped the Metasplotable archive
 3. Open
 4. Press "Edit virtual machine settings" \(Right under "Power on this virtual machine"\)
 5. Go to Network Adapter
 6. Set to Host-only
 
 ####For VirtualBox Users \(Don't worry, it's not that much harder\)
 
 1. Press "New"
 2. Press Next? You want the screen that gives you the option to name your machine
 3. The Operating System is Linux, the Version is Other Linux
 4. Set the amout of memory for the virtual machine. Go wild if you want, but Metaspoitable shouldn't
 need that much memory. 512 MBs should be plenty.
 5. Select "Use existing hard disk". Press the folder with the green up arrow and select "Metasploitable.vmdk"
 from the folder where you extracted the archive
 6. Press "Settings"
 7. Go to Network
 8. Change "Attached to" to Host-only Adapter
 
 ####For both VMWare and VirtualBox users \(After setting everything up\)
 1. Start up your virtual machine
 2. Log in with username "msfadmin" and password "msfadmin"
 3. Run "sudo dhclient && ifconfig"
 4. Remember the IP address that isn't 127.0.0.1, it should be listed under an interface like eth0
 5. Go back to your regular computer \(Right control in VirtualBox, ctrl+alt in VMWare)
 6. Check that you can ping Metasploitable \("ping \[The IP you previously found\]" for windows, "ping -c5 \[The IP you previously found\]" for Mac/Linux\)
 7. Shut down Metasploitable (close out of its window, select "shut down")
 8. Profit. You're finally finished.