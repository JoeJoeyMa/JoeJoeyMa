---
title: Kali Linux 2020.1 Release
date: 2020-01-29 21:26:00
tags:
- Linux
- Kali
- 2020
- Vmware
- iso
- system
---
ali as your Main OS
So with this, should you use Kali as your daily driver, as the primary OS? It’s up to you.
There wasn’t anything really stopping you before, we just don’t encourage it. We still don’t. But its a helping hand for the people who are familiar with Kali enough.

Why do we not recommend it?
Because we are unable to test for that usage pattern and we don’t want the influx of bug reports that would come with it.
If you are brave enough to try it, you may wish to switch the branch from “rolling” to “kali-last-snapshot” to try and be more stable.

Kali Single Installer Image
We took a good hard look at the usage of Kali, what images are actually downloaded, how they are put to use, and so on. With this information in hand, we decided to completely restructure and simplify the images we release. Going forward, we will have an installer image, a live image, and a network installer image.

These changes should allow for easier selection of the right image for you to download, while increasing flexibility on installation and further reducing download sizes.

Our Installer Image

This is what we recommend for most users that want to install Kali on their system
Doesn’t require a network connection (aka offline install) for the default package selection
Able to select desktop environment to install (Previously there was a separate image for each DE: XFCE, GNOME, KDE, etc.)
Able to select tools to install at install time
Can’t be used to boot a live system. This is just an installer image.
Filename:
kali-linux-2020.1-installer-<amd64|i386>.iso
We are no longer offering separate images for every desktop environment (DE). Instead, we now have a single image with the option to pick your DE during installation. This means there isn’t a download link for Xfce (which is our default option since 2019.4), GNOME, KDE, MATE or LXDE DEs. Just one image to rule them all.

At install time, you may select the tools included with Kali (or none at all)! This gives you more control over what you want. We understand that Kali comes with more tools than some people use, or they have their own select tools they use. Now they can install Kali without any metapackages, giving them a bare Kali installation, so they can individually select what tools they want (rather than groups).

The default image contains the kali-desktop-xfce and kali-tools-default packages, allowing for an offline installation of Kali (as it always has been). Selecting any non-default tools will require a network connection.

Note: “Kali Live” is not included in this image. If you wish to use live mode, you’ll need the live image.

Kali Setup Screen

Network Install Image

Smallest image to download
This requires a network connection to install
During setup, it will download the latest packages every time it’s used
Able to select desktop environment to install
Able to select tools to install
Can’t be used to boot a live system. This is just an installer image.
Filename:
kali-linux-2020.1-installer-netinst-<amd64|i386>.iso
It’s a very small image, containing only enough to install the base system, but behaving exactly like the full installer image, allowing you to install everything that Kali offers, provided that you have enabled network connectivity.

Live Image

Its primary use is to be able to run Kali, without installing it
But it also contains an installer, behaving like the “Network Install Image” described above
Filename:
kali-linux-2020.1-live-<amd64|i386>.iso
“Kali Live” hasn’t been forgotten about – it’s just moved to its own image. This allows you to try Kali without installing it and is perfect for running off a USB stick. You can install from this image, however, it will require a network connection (this is why we suggest the stand-alone install image for most users).

Alternatively, you can generate your own image, in particular if you want to use another desktop environment instead of our default Xfce. It’s not as hard as it sounds!.

ARM Images
You will probably notice a bit of a change in the ARM images starting with our 2020.1 release. There are fewer images available for download, due to both manpower and hardware constraints, some images won’t be posted without community assistance.
The scripts are still updated, so if an image doesn’t exist for a machine you use, you will have to create it by running the build script on a Kali machine.

ARM images for 2020.1 will still run as root by default.

The sad news that a lot of people didn’t want to hear… an image for the Pinebook Pro isn’t included in the 2020.1 release. We are still working on getting it added, and as soon as it is ready we will post it.

NetHunter Images
Our mobile pen-testing platform, Kali NetHunter, has also had some new improvements. You are now no longer required to root your phone in order to run Kali NetHunter, but that does come with some limitations.

To suit everybody’s needs, Kali NetHunter now comes in the following three editions:

NetHunter – Needs rooted devices with custom recovery and patched kernel. Has no restrictions. Device specific images are available here.
NetHunter Light – Needs rooted devices with custom recovery but no custom kernel. Has minor restrictions, i.e. no WiFi injection or HID support. Architecture specific images are available here.
NetHunter Rootless – Installable on all stock standard, unmodified devices using Termux. Some limitations, like lack of db support in Metasploit and no root permissions. Installation instruction is available here.
The NetHunter documentation page includes a more detailed comparison.
Each NetHunter edition comes with both the new “kali” user as well as root. KeX now supports multiple sessions so you can opt to run your pentest in one whilst writing a report in another.

Please note that due to how Samsung Galaxy devices function, the non-root user might not be able to run sudo but has to use su -c instead.

One of the peculiarities of the new “NetHunter Rootless” edition is that the default non-root user has almost full privileges in the chroot due to how proot containers work.

Kali Nethunter Kex Manager

Theming
With our last release, we made a major change switching from GNOME to Xfce. That wasn’t the end for us; we have kept on going with the design work, and have more updates:

GNOME There is now a new theme for GNOME users and as an additional bonus, there is a light and dark theme!

Shell Overview

Light Theme

Dark Theme

Tools We are giving the tools that you are very fond of a makeover too! We are slowly working through our collection, refreshing them and adding in new icons.

Kali Tools Icons

Menu Eagle-eyed users may also notice the icons used in the menu have also been replaced.

Kali Menu

Setup And if you opt to use the graphical installer of Kali, it’s also been updated (Before and after shots)

Kali Setup Options

Kali-Undercover
We were not expecting the community’s overwhelming response to kali-undercover. So carrying on from Kali 2019.4 release, Kali-undercover now starts to feel even more like Windows to help blend in.

Kali Undercover

New Packages
Kali Linux is a rolling distribution, so it gets updates as soon as they are available, rather than waiting for “the next release”. So since the last release, we have the normal tool upgrades as well as a few new tools added, such as: cloud-enum, emailharvester, phpggc, sherlock, splinter.

We have a few new (kali-community-wallpapers) and old (kali-legacy-wallpapers) wallpapers to offer up if you want to customize or are feeling a little a little nostalgic.

Python 2 End Of Life
As a reminder, Python 2 has reached “end of life” on the 1st of January 2020. What this means is, we are removing tools that depend on Python 2. Why? Because they are no longer being maintained, they are not receiving updates, and they need replacing. The pentesting landscape is a dynamic field that is forever changing. It’s time to keep up. We will be doing our best to find alternatives that are actively worked upon.

Giving A Helping Hand
If you want to contribute to Kali please do! If you have an area, idea of something YOU would like to work on, please dig in. If you want to help, but don’t know where to start, please see our docs page. If you have a suggestion for a feature, please record it on the bug tracker.

Note: the bug tracker is for bugs & suggestions. Its not a place to get help or support – that’s for the forums.

Download Kali Linux 2020.1
Fresh images Why are you waiting? Start downloading now!

Existing Upgrades If you already have an existing Kali installation, remember you can always do a quick update:

kali@kali:~$ cat <<EOF | sudo tee /etc/apt/sources.list
deb http://http.kali.org/kali kali-rolling main non-free contrib
EOF
kali@kali:~$
kali@kali:~$ sudo apt update && sudo apt -y full-upgrade
kali@kali:~$
kali@kali:~$ [ -f /var/run/reboot-required ] && sudo reboot -f
kali@kali:~$
You should now be on Kali Linux 2020.1. We can do a quick check by doing:

kali@kali:~$ grep VERSION /etc/os-release
VERSION="2020.1"
VERSION_ID="2020.1"
VERSION_CODENAME="kali-rolling"
kali@kali:~$
kali@kali:~$ uname -v
#1 SMP Debian 5.4.13-1kali1 (2020-01-20)
kali@kali:~$
kali@kali:~$ uname -r
5.4.0-kali3-amd64
kali@kali:~$
NOTE: The output of uname -r may be different depending on architecture.

As always, should you come across any bugs in Kali, please submit a report on our bug tracker. We’ll never be able to fix what we don’t know is broken.

## Setting up the root account on Kali 2020
If you would like to use root instead of the none superuser account kali, here are the instructions to do so:

Issue command “sudo su”

<Enter the password for kali user account>

Issue command “passwd root”

<Enter new password and retype that password>

At this point you can log-off and re log-in or you can just switch the user and log in as root.

 

Let me know if this helped you.

## apt-get update
```
gedit /etc/apt/sources.list
deb http://http.kali.org/kali kali main non-free contrib
deb-src http://http.kali.org/kali kali main non-free contrib
deb http://security.kali.org/kali-security kali/updates main contrib non-free
deb http://ftp.sjtu.edu.cn/debian wheezy main non-free contrib
deb-src http://ftp.sjtu.edu.cn/debian wheezy main non-free contrib
deb http://ftp.sjtu.edu.cn/debian wheezy-proposed-updates main non-free contrib
deb-src http://ftp.sjtu.edu.cn/debian wheezy-proposed-updates main non-free contrib
deb http://ftp.sjtu.edu.cn/debian-security wheezy/updates main non-free contrib
deb-src http://ftp.sjtu.edu.cn/debian-security wheezy/updates main non-free contrib
deb http://mirrors.163.com/debian wheezy main non-free contrib
deb-src http://mirrors.163.com/debian wheezy main non-free contrib
deb http://mirrors.163.com/debian wheezy-proposed-updates main non-free contrib
deb-src http://mirrors.163.com/debian wheezy-proposed-updates main non-free contrib
deb-src http://mirrors.163.com/debian-security wheezy/updates main non-free contrib
deb http://mirrors.163.com/debian-security wheezy/updates main non-free contrib


root@kali:~# apt-get update
Get:1 http://mirrors.aliyun.com/kali kali-rolling InRelease [30.5 kB]
Get:2 http://mirrors.aliyun.com/kali kali-rolling/contrib Sources [59.9 kB]
Get:3 http://mirrors.aliyun.com/kali kali-rolling/non-free Sources [127 kB]
Get:4 http://mirrors.aliyun.com/kali kali-rolling/main Sources [12.9 MB]
Get:5 http://mirrors.aliyun.com/kali kali-rolling/main amd64 Packages [16.5 MB]
Get:6 http://mirrors.aliyun.com/kali kali-rolling/non-free amd64 Packages [200 kB]                                                                        
Get:7 http://mirrors.aliyun.com/kali kali-rolling/contrib amd64 Packages [96.4 kB]                                                                        
Fetched 29.9 MB in 13s (2,219 kB/s)                                                                                                                   
Reading package lists... Done
```

## apt-get install ttf-wqy-zenhei


```
root@kali:~# apt-get install ttf-wqy-zenhei
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'fonts-wqy-zenhei' instead of 'ttf-wqy-zenhei'
The following NEW packages will be installed:
  fonts-wqy-zenhei
0 upgraded, 1 newly installed, 0 to remove and 418 not upgraded.
Need to get 7,472 kB of archives.
After this operation, 16.8 MB of additional disk space will be used.
Get:1 http://mirrors.aliyun.com/kali kali-rolling/main amd64 fonts-wqy-zenhei all 0.9.45-7 [7,472 kB]
Fetched 7,472 kB in 4s (1,893 kB/s)           ^[[B^[[B^[[B
Selecting previously unselected package fonts-wqy-zenhei.
(Reading database ... 255564 files and directories currently installed.)
Preparing to unpack .../fonts-wqy-zenhei_0.9.45-7_all.deb ...
Unpacking fonts-wqy-zenhei (0.9.45-7) ...
Setting up fonts-wqy-zenhei (0.9.45-7) ...
Processing triggers for fontconfig (2.13.1-2+b1) ...


```
## dpkg-reconfigure locales
## apt-get install fcitx-googlepinyin
## im-config


Kali Linux 2020.4 Release
November 18, 2020
g0tmi1k
Kali Linux News, Kali Linux Releases
We find ourselves in the 4th quarter of 2020, and we are ecstatic to announce the release of Kali Linux 2020.4, which is ready for immediate download or updating.

What’s different with this release since 2020.3 in August 2020 is:

ZSH is the new default shell – We said it was happening last time, Now it has. ZSH. Is. Now. Default.
Bash shell makeover – It may not function like ZSH, but now Bash looks like ZSH.
Partnership with tools authors – We are teaming up with byt3bl33d3r.
Message at login – Proactively pointing users to resources.
AWS image refresh – Now on GovCloud. Includes Kali’s default (command line) tools again. And there is a new URL.
Packaging Guides – Want to start getting your tool inside of Kali? This should help.
New Tools & Updates – New Kernel and various new tools and updates for existing ones, as well as setting Proxychains 4 as default.
NetHunter Updates – New NetHunter settings menu, select from different boot animations, and persistent Magisk.
Win-KeX 2.5 – New “Enhanced Session Mode” brings Win-KeX to ARM devices
Vagrant & VMware – We now support VMware users who use Vagrant.
ZSH Shell By Default
In our previous quarterly release, 2020.3, we gave a heads up that we will be switching from Bash to ZSH as our default shell going forwards (where possible). We are happy to announce that after testing and feedback from users, the switch has now happened. Say hello to ZSH.

┌──(kali㉿kali)-[~]
└─$ echo Hello World. I'm $0
Hello World. I'm zsh

┌──(kali㉿kali)-[~]
└─$
Thank you to everyone who provided positive and constructive feedback. We are happy with it, and hope you are too. With that said, we know we cannot please everyone with it (so if you wish to revert back to Bash, please do: chsh -s /bin/bash).

ZSH will be the default shell on our desktop images (amd64/i386), and cloud. For the time being, other platforms (e.g. ARM, containers, NetHunter, WSL) will still use Bash. We hope to switch more over in later versions. If you use adduser, regardless of the platform, it will also default to Bash for the time being (to avoid some edge cases of items breaking). In time, this will be changed as well.

How do I get it? Good question! If you:

Do a fresh install of Kali Linux 2020.4 or later, it will “just happen” during the setup.
If you are updating Kali, you will need to switch each user to ZSH (e.g. non-root & root since Kali Linux does not use the root account since 2020.1).
I need to switch. How do I? This can be done by applying our default zshrc file. If you are not already using ZSH, you can simply copy it over. If you are, you will need to overwrite (make sure to backup first).

kali@kali:~$ [ -e ~/.zshrc ] && cp -i .zshrc{,.bak}
kali@kali:~$
kali@kali:~$ cp -i /etc/skel/.zshrc ~/
kali@kali:~$
kali@kali:~$ chsh -s /bin/zsh
kali@kali:~$
kali@kali:~$ zsh
If you’re reading this, you may also be the type of person who likes Easter eggs – our prompts contain a few! If you go looking you may find a few gems (e.g. new_line_before_prompt & root vs non-root)._

Bash Shell Makeover
Kali Linux now has a universal, cross-shell theme.

Whilst we were tweaking ZSH, we also updated our Bash prompt ($PS1), to make it feel similar (but not act similar) to our ZSH prompt. We started playing with the Bash prompt in Kali Linux 2020.3, when the colors changed for non-root users, from red to blue. Before then, we had not changed it since Kali Linux was first released.



How do I get it? Another good question! Very similar answer to ZSH, but this time using .bashrc instead. If you are doing:

A fresh installation of Kali Linux 2020.4 or later, it’s already applied.
If you are updating Kali, you will need to configure each user (e.g. non-root & root)
If you have made any alterations to ~/.bashrc, make sure to back it up before replacing it.

kali@kali:~$ cp -i .bashrc{,.bak}
kali@kali:~$
kali@kali:~$ cp -i /etc/skel/.bashrc ~/
kali@kali:~$
kali@kali:~$ source ~/.bashrc
┌──(kali㉿kali)-[~]
└─$ echo Hello World. I'm $0
Hello World. I'm bash
┌──(kali㉿kali)-[~]
└─$
If you look & edit the contents of .bashrc, you can switch to the red “BackTrack-Linux” prompt to be nostalgic.

Partnership with tools authors: byt3bl33d3r’s CrackMapExec (CME)
Kali Linux is part of the greater community and we want to support tool authors where possible. If you have not heard of CrackMapExec (a.k.a CME), you may be missing a trick (or three) when it comes to doing infrastructure assessments (especially involving Active Directory).

We noticed that byt3bl33d3r made the decision to move to a sponsorware model. You may or may not agree with his decision, but we understand his reasoning. The tools which he makes are highly valuable and relied upon by many. We want to support him and our Kali Linux users. After various calls and email exchanges, we are delighted to reveal Kali has partnered with byt3bl33d3r.

What does this mean for me? The Kali package of CME is now pulling from a private source, allowing Kali Linux users to get access to the newest changes in CME 30 days before the tool is made public to everyone else. If you don’t use Kali, you either need to sponsor directly or wait for it to be released after 30 days.

Why are you doing this? Because we believe in open source and the community as a whole. This way, everyone benefits; both authors and users.

Kali is open source. What is stopping me from stealing/ripping/cloning from you? The code will be distributed with a banner saying something along the lines of, “for Kali users only”. Removing/altering the code will break the software license thus breaking copyright law. Do not be that guy.

Is that it? Yes! Kali Linux is open source. We understand and respect software licenses, and by doing so we hope to keep everything open source as much as possible. Putting checks & protection in place, you may be happy using someone else’s cracked/pirated software (warez) – but do you know what has been altered under the hood?

But Kali Linux being open source, has to respect other people license agreements, as do any other respectable organizations. This also includes when tools which have their license agreements changed in software updates, as a result, we have removed them from Kali.

We have more to announce about direction step in a 2021.x release (as well as looking for other authors to sponsor with). Stay tuned for more information!

Message At Login
We have noticed there being a large uprise of the amount of people saying “Kali Linux is missing ‘XYZ'” or “XYZ feature is broken”, when this is not always the case. We have done our best to write up various issues on our docs pages, however it appears they are not always being read. We also know that not everyone has a unix beard as long as @elwood-offsec, but hope you still are an experienced Linux user. There is always a reason why something is the way it is, but it may require more than the usual basic troubleshooting.

With all of that said, we are wanting to improve our communications going forwards. Most of the actions in Kali are done by the command line. So now, upon logging into a Kali terminal or console, you may be presented with a mixture of the following (depending on the configuration of your system, as it is dynamic):

% ssh kali@172.16.13.37
Last login: Thu Nov 12 15:12:29 2020 from 172.16.13.1
┏━(Message from Kali developers)
┃
┃ This is a minimal installation of Kali Linux, you likely
┃ want to install supplementary tools. Learn how:
┃ ⇒ https://www.kali.org/docs/troubleshooting/common-minimum-setup/
┃
┃ This is a cloud installation of Kali Linux. Learn more about
┃ the specificities of the various cloud images:
┃ ⇒ https://www.kali.org/docs/troubleshooting/common-cloud-setup/
┃
┃ We have kept /usr/bin/python pointing to Python 2 for backwards
┃ compatibility. Learn how to change this and avoid this message:
┃ ⇒ https://www.kali.org/docs/general-use/python3-transition/
┃
┗━(Run "touch ~/.hushlogin"
┌──(kali㉿kali)-[~]
└─$
We hope this helps various common problems to be quickly fixed, but at the same time, not feel intrusive. Each of the issues have a link to our documentation page in order to correct the issue. After its been addressed, the message should not be displayed again. For whatever reason (unable or do not want to), you can permanently hide any messages from us being displayed by doing: touch ~/.hushlogin (per user) or touch /etc/kali-motd/disable-all (for a global setting).

We have a few other things in the works to help communicate items out planned for 2021.x. Stay tuned!

AWS EC2 Cloud Image Refresh
Kali Linux has been on AWS since 1.0.6. Over the years, we have done various refreshes of our build-scripts to produce the cloud images. Finally with Kali 2020.2, we have a fully automated system in place. However during the changeover, we were shipping the image without any GUI or any tools by default. This was to give the cleanest, smallest image as possible. In hindsight, we didn’t communicate this change over well, and a lot of you noticed “tools missing” (as kali-linux-default was not included). However, in 2020.4, we have created a new metapackage, kali-linux-headless, and included it which only has the default set of command line tools.

Upon doing the refresh, we have worked with AWS to get Kali Linux added to “GovCloud“. Which may be useful to a certain audience. With how the accounts were setup, we have had to start from fresh. As a result, we have a new marketplace entry.

What does this mean for people who are using the old entry? As Kali Linux is a rolling distribution, not a lot! You can still keep updating Kali Linux as usual. However, you will no longer be able to spin up the latest version using the latest instance. For that, you will need to switch to the new entry.

Note: We have tried to say it as many different places as possible, but putting it here is not going to hurt. The default login for AWS EC2 username is “kali” (not the standard “ec2-user”).

Kali Docs & Packaging Guides
In 2019.4, we moved https://docs.kali.org/ from a WordPress solution to https://www.kali.org/docs/ using Hugo. In September, we finished (for now) tweaking the theme, making it easier to use, super fast at loading and easier to anyone to edit.

We have started to go though all the pages and refreshing them, bringing them all up-to-date, and adding more in. We are doing it section by section, and so far have completed the first three (so we still have a way to go! After it is completed, it will be easier to keep them up-to-date, making it an on-going task. For the sections that are missing or lacking content, we have been generating issues to help track. If you want to help get involved with Kali Linux, this is an easy place to start.

We have also created various new pages, all about our packaging process:

Setting Up A System For Packaging
Introduction to Packaging (Instaloader​)
Intermediate Packaging (Photon)
Advanced Packaging (FinalRecon & Python-icmplib)
We have also the pages from our login messages:

Common Cloud Based Setup Information
Everything you need to know about the switch to Python 3
Minimum Install Setup Information
And various other pages created:

AWS
Kali inside VirtualBox (Guest VM)
Using EoL Python Versions on Kali
Win-KeX v2
Win-KeX SL
Win-KeX Win
New Tools & Updates
As with every Kali release, there are new tools and updates. The kernel got an upgrade to 5.9, so you benefit with all the loveliness that that brings. We have switched to “proxychains4” (aka ProxyChains-NG) as the default (everything from v3 should still work: same flags and configuration files & folder locations for legacy users, else the paths will reflect the version if starting from fresh). Also, GNOME was updated to 3.38 & KDE to 5.19.

New tools in Kali Linux:

Apple bleee
CertGraph
dnscat2
FinalRecon
goDoH
hostapd-mana
Metasploit Framework v6
Whatmask
One last thing. We have tweaked how we handle our wallpaper packages:

kali-wallpapers-all ~ Give me all the wallpapers
kali-wallpapers-2019.4 ~ Default for Kali Linux between 2019.4 and 2020.3
kali-wallpapers-2020.4 ~ Default for Kali Linux between 2020.4 and onwards
kali-wallpapers-legacy ~ Nostalgic value
Kali NetHunter
@yesimxev has added a new settings menu, allowing for easy back up and restore of configuration files. It also allows you to change the Kali NetHunter boot animation. How is this as a teaser?



Call on all boot animation devs out there: We’d love to hear from you. If you have a cool boot animation you’d like to share, please submit a merge request to our Kali NetHunter boot animation repository .

The new images also contain a “Magisk persistence” module, so we no longer have to flash Magisk again after we installed Kali NetHunter.

Win-KeX 2.5
Win-KeX 2.5 includes a new “Enhanced Session Mode (–esm)”, which works like the “Window” mode but uses the Remote Deskop Protocol (RDP) & client native to Windows. This mode will allow users of “Windows on ARM” devices to use Win-KeX and it adds sharpness to Win-KeX on HiDPI devices.

We have also added a “–ip” option to address a bug in WoA causing massive packet losses when using “localhost”. To start Win-KeX with sound on arm devices, just type:

kali@kali:~$ kex --esm --ip --sound
The “–ip” parameter has one little downside though: Win-KeX asks for the Kali Linux user password when launched for the first time and stores it in the Windows credentials store. Since the IP address changes after every reboot, you will be prompted again. This is a known WSL2 bug and we’ll expect it to be fixed soon so that we can drop the “–ip” parameter and we’ll never have to enter the password again.



Kali Vagrant & VMware
We have had a Vagrant image since Kali Linux 2018.3. However, it’s always been for VirtualBox. Until now. We are now also producing a VMware Vagrant image!

Note, you will need to have a separate license for both VMware and Vagrant for this to work, as it is a paid-for plugin.
For more information, you can see here and here.

Kali ARM devices
We have been working away on our ARM images as usual, and this release is no exception. We have reduced the amount of pre-generated images (now 14) as there has not been the demand for these other devices. We have left their build scripts (now up to 43 devices supported), in case you wish to generate the images yourself.

Community Shoutouts
Following on from last time, these are people from the public who have helped Kali and the team for the last release. We are super grateful and want to praise them for their work (giving credit where due!):

@1y for generating a ARM build script for a new device, imx6-ull-evk
@dracode for the awesome work on Nethunter, in particular the GPS fixes.
@mirivan for all the amazing additions and fixes to NetHunter as well as helping out with the issue tracker.
@TheMMcOfficial for his continued help with NetHunter and DuckHunter
@Martinvlba for his great contributions to NetHunter, especially hostapd
@s133py for all the tireless work on NetHunter and helping with issues
Not a community member per se, but we do want to give an honorable mention to GitLab. Kali Linux is now a Open-Source Partner (different to their Open-Source Program). We made the switch middle of 2019, and we could not have been happier. Thank you GitLab for supporting us, and for everything you do for the open-source communities as a whole!



And on the subject, Kali Linux is apart of Docker’s Open Source Community.

Download Kali Linux 2020.4
Fresh Images: So what are you waiting for? Start downloading already!

Seasoned Kali Linux users are already aware of this, but for the ones who are not, we do also produce weekly builds that you can use as well. If you cannot wait for our next release and you want the latest packages when you download the image, you can just use the weekly image instead. This way you’ll have fewer updates to do. Just know that these are automated builds that we do not QA like we do our standard release images. But we gladly take bug reports about those images because we want any issues to be fixed before our next release.

Existing Upgrades: If you already have an existing Kali Linux installation, remember you can always do a quick update, followed by setting the default shell to ZSH. If you’re already using ZSH, and want our new configuration, you can do the following:

kali@kali:~$ echo "deb http://http.kali.org/kali kali-rolling main non-free contrib" | sudo tee /etc/apt/sources.list
kali@kali:~$
kali@kali:~$ sudo apt update && sudo apt -y full-upgrade
kali@kali:~$
kali@kali:~$ cp -i /etc/skel/.bashrc ~/
kali@kali:~$
kali@kali:~$ cp -i /etc/skel/.zshrc ~/
kali@kali:~$
kali@kali:~$ chsh -s /bin/zsh
kali@kali:~$
kali@kali:~$ [ -f /var/run/reboot-required ] && sudo reboot -f
kali@kali:~$
You should now be on Kali Linux 2020.4. We can do a quick check by doing:

kali@kali:~$ grep VERSION /etc/os-release
VERSION="2020.4"
VERSION_ID="2020.4"
VERSION_CODENAME="kali-rolling"
kali@kali:~$
kali@kali:~$ uname -v
#1 SMP Debian 5.9.1-1kali2 (2020-10-29)
kali@kali:~$
kali@kali:~$ uname -r
5.9.0-kali1-amd64
kali@kali:~$
NOTE: The output of uname -r may be different depending on the system architecture.

As always, should you come across any bugs in Kali, please submit a report on our bug tracker. We’ll never be able to fix what we do not know is broken! And Twitter is not a Bug Tracker!


Win-KeX Version 2.0
September 18, 2020
re4son
Kali Linux News
We have been humbled by the amazing response to our recent launch of Win-KeX. After its initial release, we asked ourselves if that is truly the limit of what we can achieve or could we pull off something incredible to mark the 25th anniversary of Hackers? What about “a second concurrent session as root”, “seamless desktop integration with Windows”, or – dare we dream – “sound”?

With no further further ado, we are thrilled to present to you Win-KeX v2.0 with the following features:

Win-KeX SL (Seamless Edition) – bye bye borders
Sound support
Multi-session support
KeX sessions can be run as root
Able to launch “kex” from anywhere – no more cd-ing into the Kali filesystem required
Shared clipboard – cut and paste content between Kali and Windows apps
iWin-KeX v2.0

The installation of Win-KeX is as easy as always:

sudo apt upgrade && sudo apt install -y kali-win-kex (in a Kali WSL installation)

Win-KeX now supports two dedicated modes:

Win-KeX Window mode is the classic Win-KeX look and feel with one dedicated window for the Kali Linux desktop. To launch Win-KeX in Window mode with sound support, type:
kex --win -s
Win-KeX SL mode provides a seamless integration of Kali Linux into the Windows desktop with the Windows Start menu at the bottom and the Kali panel at the top of the screen. All applications are launched in their own windows sharing the same desktop as Windows applications.
kex --sl --s
To enable sound:
Start Win-KeX with the --sound or -s command line parameter. We’ve been watching Blu-rays in Win-KeX SL without problems. Why you ask? Because – now we can ;-)

Win-KeX now supports concurrent sessions
Win-KeX as unprivileged user
Win-KeX as root user
Win-KeX SL
Windows Firewall
Both SL mode and sound support require access through the Windows Defender firewall. When prompted, tick “Public networks”. You can later go to the firewall settings and restrict the scope to the WSL network (usually 172.3x.xxx.0/20)

Manpage
Forgotten that lifesaving parameter? Try:

kex --help
for a quick overview, or consult the manual page for a detailed manual:

man kex
Win-KeX Manpage

Big shout-out to the authors of the following components without which there would be no Win-KeX:
Win-KeX Win is brought to you by TigerVNC
Win-KeX SL utilizes VcXsr Windows X Server
Sound support is achieved through the integration of PulseAudio.
Further Information:
More information can be found on our documentation site.

We hope you enjoy Win-KeX as much as we do and we’d love to see you around in the Kali Forums

