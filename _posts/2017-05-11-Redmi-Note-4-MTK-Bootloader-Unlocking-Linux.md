---
layout: post
comments: true
title: Redmi Note 4 MTK Bootloader Unlocking using Linux
categories: xiaomi android
---

After long and tedious process of unlocking bootloader in my Xiaomi Redmi Note 4
phone using linux, to sum up I decided to write definitive tutorial. This
tutorial is writen especially for MTK SOC devices, so if you have locked
bootlader on other Xiaomi phone that Redmi Note 4, then you can try unlocking
it using tools presented here.

# Disclaimer
> I don't take any responsibility for bricked or broken devices.
> You are performing all steps at your own risk.

# General informations
Probably many of you knows that
[bootloader unlocking process](http://en.miui.com/thread-202290-1-1.html)
in recent Xiaomi phones is difficult and requires a lot of work.
First of all it requires special tool called Mi Unlock. Unfortunately it works
only in Windows operating system. Second thing is that to unlock bootloader you
must [ask for premission](https://miui.com/unlock/) first. Then you need to
wait for SMS message that you are allowed to proceed to next steps. To sum up
this part - **we will need to use Windows operating system anyway**.
Right now there is not way to unlock bootloader using linux only :(
So install one
on physical machine or virtual one.

# Unlocking process

## Preparation
- Create Xiaomi Account if you don't have one
    - Go to <https://account.xiaomi.com/>
    - At button of page change language from Chinese to English
    - Click on **Create Mi Account**
    - Fill form and click **Create Mi Account**
- Pass all security check-ups
    - Login to your account <https://account.xiaomi.com/>
    - Fulfill all 4 tasks (Password, Recovery email,...)
    - Make sure there is green bar saying that your account is secure

    This step in necessary to make sure your bootloader unlock permission grant
    application will be accepted.
- Go to <https://miui.com/unlock/apply.php> and apply for unlocking your device.
    Provide reason of unlocking like:
    > I want to install custom ROM.
- Wait for grant permissions SMS message. Myself, I have waited for 10 hours. This time
my vary between users.
- After receiving email go to
<https://drive.google.com/open?id=0B9wtW2KGOf0RYWhLNG9ybWM3OG8>
and download old version of Mi Flash tool. This is needed for bypass the error
saying that **binding time is too short**.
- Install application of windows machine

## Flashing China Developer ROM
To be able to unlock bootlader on Redmi Note 4 you need China Developer ROM
installed on your device.
- Backup all your important data
- Download **Redmi Note 4 Latest China Developer Version Fastboot** from
    <http://en.miui.com/a-234.html>
- Download custom CUST.BIN <https://www.dropbox.com/s/gyrpatlwi4ok1ct/cust_global.rar?dl=0>
- Extract **ROM** archive
- **Replace** CUST.BIN in images/ dir with custom one you have downloaded
- Download latest version of SP Flash Tool for **Linux** from
    <https://androidmtk.com/smart-phone-flash-tool>
- Extract downloaded archive
- Add your user to special linux group
    - For ubuntu
    > sudo adduser username dialout
    - For arch
    > sudo gpasswd -a username uucp
- Logout and login again to make change live
- run sp\_tool.sh which is located in folder where you extracted archive
- Set **Download Agent** to **MTK_All_In_One_DA.BIN**
- Set **Scatter-loading File** to **MT6797_Android_scatter.txt** which is
located in **ROM** images/ dir
- **Uncheck preloader** position on the list of images to push to device
- Turn off phone
- Click **Download** Button in SP Flash Tool
- Click and hold **Volume Down (-)** on phone and while holding it plug your phone
to PC via USB cable
- If phone is detected then yellow bar appears at button and flashing process
begins. You can release **Volume Down (-)** button.
- After flashing is done **Download OK** message appears.
- You can unplug your phone and turn it on. First boot might take up to 10
minutes. This is normal.

## Binding Mi Account to phone
After your phone is ready you must bind it to Xiaomi Account which you have
created in previous steps. Follow following steps in configuration wizard.
- Change language to English
- Connect to network
- Login to Mi Account (very important step)
- Finish wizard
- Go to Setting -> About phone -> Tap on MIUI version for 10 times until message
    appears
- Go to Setting -> Additional settings -> Developer options
- Turn on USB Debuging

## Unlocking Bootloader
- Start Mi Unlock Tool
- Login to your account
- Turn off your phone and turn in on in Fastboot mode. Hold **Volume (+) and
    Power** buttons together. Relase buttons when Fastboot screen appears.
- Follow steps in Mi Unlock and connect your phone to PC via USB cable when
    you are asked to do so.
- If everything works out well Mi Unlock will stop at 100% and **your bootloader
    will be unlocked**.
- Enjoy!

## What to do next ?
Now when you have your bootloader unlocked you will probably want to **flash
custom Recovery** to manage your ROMS. This process will be described in next
post.

# References
- <https://forum.xda-developers.com/redmi-note-4/how-to/guide-redmi-note-4-unlock-bootloader-t3517806>
- <https://forum.xda-developers.com/general/rooting-roms/tutorial-how-to-setup-spflashtoollinux-t3160802>
- <http://en.miui.com/thread-202290-1-1.html>
- <http://en.miui.com/thread-371349-1-1.html>
