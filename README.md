# Homey Pro (Early 2023) – CM4 Upgrade Guide  
Upgrade to Raspberry Pi Compute Module 4 (8GB RAM / 32GB eMMC)

---

## ⚠️ Disclaimer

This guide describes a **hardware modification that is not supported by Athom**.  
Performing this upgrade will **void your warranty** and carries a risk of damaging your device if done incorrectly.

You should only attempt this if you are comfortable with electronics, static-sensitive components, and device disassembly.

Proceed at your own risk.

NB: Pictures used in this guide is taken from a Danish YouTubers guide. But i followed his guide to do the procedure, so I can confirm that the pictures are correct

***If I have missed something or you have any question, use the discussion button on this repo***

---

# 📦 What This Upgrade Does

Homey Pro (Early 2023) uses a Raspberry Pi **Compute Module 4 (CM4)** internally.  
The stock model includes:

- **2GB RAM**
- **8GB eMMC**

This guide shows you how to replace it with a **CM4 featuring 8GB RAM and 32GB eMMC** for a major performance improvement:

- Faster app load times  
- Fewer “Homey Offline” freezes  
- More stable when running many apps  
- Improved responsiveness  
- Better long-term uptime  
- Faster boot time  
- More storage for updates and apps  

---

# Part 1 — Backup the Original Homey System (Before you touch the hardware)

Before opening or replacing anything, you must **create a full backup** of your existing Homey Pro — this includes OS, all settings, devices, flows, networks, etc. That way you can restore everything after the CM4 swap.  

### ✅ Backup Steps

<img width="1622" height="601" alt="image" src="https://github.com/user-attachments/assets/f9545d3a-3c51-43cf-a67d-27ae83475dd0" />


1. Open you browser and go to [https://ota-usb.homeypro.net/](https://ota-usb.homeypro.net/)
2. If it's your first time doing this, you might be prompted to install a driver on you windows machine.
3. Take the USB cable that was with you Homey Pro 2023, nad connect it to your PC
   While connecting the USB to your Homey Pro 2023 and your PC, you need a paperclip to hold down the small button on the bottom on the unit. This will make the Homey boot into a USB mode (The light on the Homey Pro 2023 should be yellow)
4. It will now be shown as a unit in the browser.
5. Press the unit and connect
6. Now wait for the Homey to do it's magic!

   <img width="1142" height="559" alt="image" src="https://github.com/user-attachments/assets/bab92687-8274-4e5b-aac5-b6a4439f4021" />

7. In the USB Tool interface in your browser, select the device and click **“Create a Backup”**. Choose a location on your PC to store the file.
8. Wait for the backup process to complete (may take a few minutes). Now you have a full system image — OS + all your Homey data.  
9. Store the backup file safely (e.g. on an external drive, cloud storage, etc.).  
10. The backup is now done and we can move to the next step, replacing the CM4 with the new one! **Turn off and unplug** your Homey Pro before opening the case.  

> **Important:** this backup image includes your Homey account credentials. **Do not share the backup file publicly or with others.**


# Part 2 - Hardware Upgrade
<img width="2371" height="384" alt="image" src="https://github.com/user-attachments/assets/11860413-f3c6-4fd8-b6da-a93d1646990e" />


1. Turn the unit upside down. Carefully detach the rubber bottom to reveal 4 screws (not just one).

2. Use a Torx T9 bit (or suitable screwdriver) to unscrew the 4 screws at the bottom. Remove them completely.

3. Open the plastic casing. Carefully separate the two halves of the shell; there are no more screws, but be gentle.

4. Inside you’ll find a black heatsink-fin module attached over the CM4. Instead of desoldering pins between boards (which is a different method), this guide uses removal of the nuts on the heatsink. 

## Remove the old CM4-Module
<img width="2560" height="353" alt="image" src="https://github.com/user-attachments/assets/2f26c7e9-e307-4edb-823d-42e370dfa63b" />

5. Using a small wrench or (better) small precision pliers / flat-nose pliers, loosen and remove the 4 nuts that hold down the heatsink module. The space is tight, but it’s doable — some bending of fins may be needed (bend carefully, then bend back when reassembling). 

6. Once the heatsink and its spacers are free, lift off the heatsink module. Then you’ll have access to the underlying CM4-carrier board with the module. 

7. Gently unplug the CM4 module from its edge connector using a plastic pry tool (or gentle leverage), carefully lifting — don’t force or twist.

8. Remove the small thermal pad ("kølepad") attached to the old CM4 module. It’s lightly stuck — remove carefully.

## Mount the new CM4-Module
<img width="1271" height="384" alt="image" src="https://github.com/user-attachments/assets/a3d83db2-6ce6-4944-ae1c-1c5d4227b275" />

10. Attach this same thermal pad onto the new CM4 module (don’t add extra glue or adhesives). 

11. Place the new CM4 module on the carrier board where the old one was. Align the module properly. 

12. Reinstall the spacers and black heatsink-fin module. Carefully realign and reattach the 4 heatsink nuts (best done with precision tools, possibly holding nuts with pliers while tightening). Close the plastic case: reassemble housing, reinstall the 4 bottom screws, and snap/attach the rubber base.

## Restore the Linux operating system and Homey software on the new CM4 module
The new larger CM4 module is completely empty and does not contain an operating system. So now we need to restore the backup we took of the old/original CM4 module that was in the Homey Pro 2023 from the start, in "Part 1 — Backup the Original Homey System (Before you touch the hardware)"
<img width="1904" height="384" alt="image" src="https://github.com/user-attachments/assets/43297608-e99d-481d-8b92-5b722d126215" />

13. Find a paper clip or similar that fits into the small hole at the bottom of the Homey Pro 2023.
    Take the USB cable that comes with the Homey Pro 2023 and plug it into the Homey Pro 2023’s USB-C port.
    Press the paper clip into the hole until you feel a small contact being pressed in. Keep pressing while you connect the other end of the USB-C cable to the PC’s USB port. Continue to hold the clip in until the Homey Pro 2023 lights up yellow/orange in the LED ring.
    The Homey Pro 2023 has now started up in a special setup mode.
    If the Homey Pro 2023 lights up white in the LED ring, you must remove the USB cable and start over from this point.

14. Open you browser and go to [https://ota-usb.homeypro.net/](https://ota-usb.homeypro.net/)
15. Since we already have the USB driver installed from earlier and Homey Pro 2023 has started in setup mode, we will not encounter the same screen as in Part 1 – Backup of Homey’s operating system. We will proceed directly to the next point and can choose what we want to do.
    Select "Restore a Backup" and select the backup file that we created earlier from the old CM4 module.
16. Wait while the backup image is restored to the new CM4 module in Homey Pro 2023 - this may take a few minutes.

## When the restore is finished, eject the homey from the system and boot it up using the power supply that you normally use it with. You can then confirm that your homey has more RAM (The storage will still say 2.7GB as max, since we haven't changed the partition yet)
<img width="852" height="418" alt="image" src="https://github.com/user-attachments/assets/d9f3186e-5af4-4dde-a374-0d52f60de673" />

# Part 3 - Jailbreak / Get root access
By jailbreaking the Homey Pro 2023, we get root (super administrator) access to the Homey Pro 2023 via the SSH protocol. We can use this to make changes to the Linux operating system that underlies the Homey software.

The jailbreak is necessary so that in **Part 4 – Expanding storage** we can run system commands that expand the USER partition/drive to MAX size, so that we can access the full disk space that we have purchased with the new and larger CM4 module.

In this part of the article series, I will show you how to jailbreak the Homey Pro 2023 and get full control.

Remember to take a backup of your Homey Pro 2023 before you continue. If you have followed this series of articles from the beginning, you will already have a backup that you can use. If not, go to Part 1 — Backup the Original Homey System first and return here.

## The Jailbreak Script
We will use a jailbreak script that will install OpenSSH in the Linux operating system on the Homey Pro 2023 and then create a user with root access (super administrator), which we will need to be able to log in to the operating system via the newly installed SSH access and execute the system commands.

You can download the jailbreak script here: [Jailbreak script for Homey Pro 2023](https://homey.guide/wp-content/uploads/jailbreak/HP23-Jailbreak-Files.zip)

Unzip the zip file with the script so that you end up with 2 folders: **etc** and **home**

In each of the folders there is one file. You can open them in Notepad on the PC and see what they contain. The most important is the home/ssh-setup.sh file, which is the file that will open SSH access to the Homey Pro 2023's operating system and create the root user for us with the username homey-pro

## Raspberry Pi USB Boot Tool
In order to copy the 2 unpacked jailbreak folders, with the 2 files, into the Homey Pro 2023, we need access to the file system in Homey – or corrected the file system on the CM4 module.

It's actually not as difficult as it sounds. The people behind Raspberry Pi provide a developed tool for the purpose, called Raspberry Pi USB Boot Tool, and that's what we're going to use.

Download [Raspberry Pi USB Boot Tool](https://github.com/raspberrypi/usbboot/raw/master/win32/rpiboot_setup.exe) and install it on your PC. Along the way, a few black command prompt windows will appear, where a USB driver is being installed – this is completely normal.

## Linux filsystem på Windows
Some of the partitions/drives that we will be working with on the CM4 module are formatted in the FAT32 format, which Windows can work with – while others are in the ext4 format, which is a pure Linux format that Windows does not understand. And it is precisely some ext4 partitions/drives that we need access to in order to perform the jailbreak.

Fortunately, the problem is easily solved with the software **[Linux File Systems for Windows by Paragon Software](https://www.paragon-software.com/home/linuxfs-windows/)**. The software can be tried for free for 10 days – which is enough to perform this jailbreak. Otherwise, the software can be purchased later for approx. $29,95 as a private user.

Download Linux File Systems for Windows by Paragon Software and install it on your PC. Just click next to everything you are asked about.

Restart the PC afterwards.

## Perform the jailbreak
<img width="2560" height="354" alt="image" src="https://github.com/user-attachments/assets/3342f3fb-b0d5-4291-ac90-41b6838cefef"/>

1. Find a paper clip or similar that fits into the small hole at the bottom of the Homey Pro 2023.
   Take the USB cable that comes with the Homey Pro 2023 and plug it into the Homey Pro 2023’s USB-C port.
   Press the paper clip into the hole until you feel a small contact being pressed in. Keep pressing while you connect the other end of the USB-C cable to the PC’s USB port. Continue to hold the clip in until the Homey Pro 2023 lights up yellow/orange in the LED ring.
   The Homey Pro 2023 has now started up in a special setup mode.
   If the Homey Pro 2023 lights up white in the LED ring, you must remove the USB cable and start over from this point.

2. In the Windows start menu, a folder called Raspberry Pi has appeared after we installed the Raspberry Pi USB Boot Tool.
   In that folder there is a shortcut to rpiboot. Start rpiboot.
   Rpiboot will transfer a temporary image to the memory of the Homey/CM4 module, which it will boot from. This is possible because we have started Homey in setup mode. After starting the image, which takes a few seconds, all the partitions on the CM4 module are offered as independent drives via the USB connection.
   If this is the first time you are performing this jailbreak, your Windows can only see 3 FAT32 partitions now. We are missing 3 ext4 partitions, which we will access in the next step.

3. Open the Linux File Systems for Windows by Paragon app on your PC.
   Here you can see the 3 ext4 partitions that we are missing: ROOTA, ROOTB, USER. They are not connected to the PC yet and therefore cannot be seen in Windows Explorer yet.

   - For each of the 3 drives, you must do the following:
   - 3.1 – Click on the eject icon.
   - 3.2 – Select Mount Volumes in: Read-Write.
   - 3.3 – Click on the Mount button.
   - 3.4 – You can choose to activate the Mount automatically button, but it is not necessary. If you activate it, you do not have to go through this step again if you need to access the partitions/drives on the CM4 module another time.

4. Open File Explorer on your PC (shortcut: Windows key + E) and go to **This PC**
Here you can see that there are now 6 extra volumes. They come from Homey Pro 2023 – or rather the volume from the CM4 module, which now shows all the partitions (divisions of disk space) that you normally do not have access to. Each partition appears as an independent volume in Windows, and you can actually not see here that it is 1 volume that is divided into 6 partitions, rather than 6 independent volumes.

The only partition that you normally have access to is the one called USER. This is where all your Homey apps are installed – and it is that drive/partition that we are going to make MUCH LARGER in the next and final part of this article series.

5. Copy the 2 folders, **etc** and **home** from the Jailbreak zip file, onto the drive called **ROOTA** – NOT BOOTA.
   Then copy the same 2 folders, **etc** and **home*, onto the drive called **ROOTB** – NOT BOOTB.

   ***During both copies you will be asked if you want to overwrite the existing files. You can safely answer yes.***

## Exit the jailbreak
After the files are moved over it is important to **"Eject Compute Module"**. Not doing this can result in the jailbreak not working as some of the files you copied over might end up corrupt.
You may have to do this several times before it succeeds, and it may take some time. Also close everything that has a relationship with copying the jailbreak files. Explorer, Notepad, possibly Winrar, etc.

***See number six in the image above***

# Part 4 – Expanding storage
When we took a backup of the Homey Pro 2023 in ***Part 1 — Backup the Original Homey System (Before you touch the hardware)***, the backup only contained a total allocation of 8 GB of disk space – because that is the size of the original CM4 module in the Homey Pro 2023.
This resulted in the fact that when we restored the backup on the new CM4 module in the last part of Part 2 - Hardware Upgrade – and then restored Homey, only 8 GB of space was allocated, despite the fact that we now have 32 GB to make good use of.

## SSH communication with Homey Pro 2023
In order to communicate with the operating system behind the Homey Pro 2023, we need to communicate via a technology called SSH. Usually I like to use the software called ***Putty***, but their website seems to be down, so for now I will guide you using **Terminal**/**CMD** on a windows computer.

SSH stands for Secure Socket Shell and with it you can create an encrypted connection from your computer to the Homey Pro 2023. SSH is used to administer Unix and Linux based operating systems remotely – that is, when you do not have physical and direct access to the computer with Unix/Linux on it. Remote access via SSH can be both on the local network and via the Internet – which is why it is important that the connection is encrypted. Most Unix/Linux servers do not have a graphical user interface installed, as it takes up unnecessary system resources, and they can therefore only be administered via SSH.

Homey Pro 2023 is actually also a computer/server that runs Debian GNU/Linux as an operating system, and on top of that operating system the Homey software is installed, with the graphical user interface that you are used to building flows in.

The user interface in an SSH client is simple and resembles the old Microsoft DOS system that some of us have worked with on PCs in the early 80s and 90s - before Microsoft Windows 3.11 began to dominate the market.

This means that just like in the old DOS days, SSH also only works via text commands - and also responds back with text. It can be a little scary if you are only used to working with graphical user interfaces. But we only have to execute a handful of commands, and I make sure to document with each command how you can check that no changes have occurred since I wrote this article and you therefore risk making changes to something other than intended.

Should something go completely wrong, remember that we have a backup from ***Part 1 – Backup of Homey’s operating system*** that we can always return to. And we even have the option to reinstall the old CM4 module – then everything is as it was before we started this guide.

## SSH - Using "Terminal" on windows
To connect to your Homey using the credentials created by the jailbreak we will use window's built in terminal.

1. Find the IP-Adress to you Homey Pro unit This can be done by going into the homey app and looking into General setting -> About (Under system information)

2. Open ***Terminal*** or CMD and follow this setup to connect to your homey:
   ``ssh -p 2222 homey-pro@[Your_Homey_Address] `` Remember to remove the brackets [] on the start and end of your ip adress
   If you get a security warning type ``yes`` and then press enter.

3. When you are logging into your homey, you will not be using you normal login. The SSH script provided in ***Part 3 - Jailbreak / Get root access*** creates a root user with this info:
   Login as: **homey-pro**
   Password: **pro**

4. After you are logged in, you will get prompted to create a new password. Type in the old password **pro** and then type in your new password. It will look something like this:

    ``Current password: pro``
   
   ``New password: [Your new password]``

   ``Retype new password: [Your new password]``

## The commands to expand disk space - Who is Sudo?
<img width="1505" height="192" alt="image" src="https://github.com/user-attachments/assets/b1da7d12-5c3c-499c-8085-3de97f7569fc" />
When we start typing the 7 commands in the **Terminal** that are needed to expand the disk space, you may notice that sudo is the first thing in all of them. Why is that?

When you are logged in with SSH into a Linux operating system, you only have regular user rights, regardless of who you are, and cannot make changes to the system that require root (administrator) rights.

The homey-pro user has root rights in the backpack, but they are only taken out when they are needed. That way, you don't make accidents when you have to actively request that root rights be used.

If you want to have root rights at all times, and thus avoid typing sudo in front of all the commands, you can start by typing ``sudo -i`` and enter your code again. Then you have root rights for the rest of the session – until you log out or close **Terminal**.

Let's look at the 7 commands. When you want to execute them, copy/paste them into Terminal, rather than typing them manually. This will avoid typing errors. A single wrong letter can result in unexpected results.

1. ``sudo fdisk -l /dev/mmcblk0``
   
   ***You may be asked to enter your password again to confirm that root privileges are to be used.***
   <img width="811" height="356" alt="image" src="https://github.com/user-attachments/assets/d11186f3-519c-47f6-a37d-a4f6f3589d37" />

   This command shows how the disk space on the CM4 module is divided. Compare the output below with the graphic image further up under the section heading. You will see that you can find the 6 divisions – or partitions as they are called, including the 7th mysterious division in line 2, which is called Extended. The partitions in the list from SSH are in the same order as you see them in the graphic image. This is also the order in which they are located on the volume.

Line number 2, marked with a $${\color{red}red \space \color{red}sqare}$$, which ends with the word Extended and is 7.2 GB in size, requires a little explanation. If we find Extended again in the graphic image, we can see that it encloses 4 other partitions (divisions of the disk space on the CM4 module).

If you have more than 4 partitions on a volume unit – and Homey Pro 2023 has 6 – then you have to cheat a little. You do this by creating an Extended partition, which in this case is 7.2 GB. Within the Extended partition, you can create several (logical) partitions, which together can be a maximum of 7.2 GB. In this way, there are actually only 2 parent partitions.

In Homey Pro 2023's Extended partition, there are 4 (logical) partitions nested. One is the User partition, which we are very interested in expanding so that it gets the 21.84 GB of disk space that the graphic image entices us with, not yet allocated to anything.

But since the User partition is embedded in a 7.2 GB Extended partition, which is completely filled, we cannot expand it right away. We have to expand the Extended partition first.

2. ``sudo parted /dev/mmcblk0 resizepart 2 100%``
   
   ***You may be asked to enter your password again to confirm that root privileges are to be used.***
   <img width="1000" height="129" alt="image" src="https://github.com/user-attachments/assets/2b17ab00-634a-4bff-914d-587c833e2a62" />

   This command expands the **Extended** partition, which includes the **User** partition, to fill all available space. This means that it is allocated the 21.84 GB of disk space that no one else has claimed.

   If you are warned that the partition is in use, type y followed by pressing the enter button to continue.

   Note the number **2** in the command. This corresponds to the number that the **Extended** partition has.

4. ``sudo fdisk -l /dev/mmcblk0``
   
   ***You may be asked to enter your password again to confirm that root privileges are to be used.***
   <img width="954" height="378" alt="image" src="https://github.com/user-attachments/assets/689c0a60-3763-4d07-b340-50a58f1409ec" />

   Same command as in point 1. Here we check that the Extended partition has been expanded from 7.2 GB to 29.1 GB.

5. ``sudo parted /dev/mmcblk0 resizepart 9 100%``
   
   ***You may be asked to enter your password again to confirm that root privileges are to be used.***
   <img width="1000" height="129" alt="image" src="https://github.com/user-attachments/assets/838a1011-1775-4063-92fa-8965604a3ad6" />

   After we expanded the **Extended** partition in step 3, it has a lot of free space inside it. We will allocate the free space to the **User** partition with this command.

   Notice the number **9** in the command. This corresponds to the number that the User partition has – which we checked at the end of step 1.

6. ``sudo fdisk -l /dev/mmcblk0``
   
   ***You may be asked to enter your password again to confirm that root privileges are to be used.***
   <img width="954" height="356" alt="image" src="https://github.com/user-attachments/assets/d8958182-ae3e-46ca-9e3d-edd8197ac92d" />

   Well-known command that we have used twice before. This time we check that the **User** partition, ``/dev/mmcblk0p9``, has been expanded from 2.7 GB to a glorious 24.6 GB!

7. ``sudo resize2fs /dev/mmcblk0p9``
   
   ***You may be asked to enter your password again to confirm that root privileges are to be used.***
   <img width="962" height="127" alt="image" src="https://github.com/user-attachments/assets/68711c5a-ef44-4fc7-bcac-cbe0014d7a80" />

   When you run the ``resize2fs`` command on a partition that has been extended, the command automatically resizes the file system to the new partition size, allowing you to fully utilize the available space.

   Without this command, Homey cannot see and utilize more than the 2.7 GB that the partition originally had before we extended it.

8. ``sudo reboot now``
   
   <img width="668" height="172" alt="image" src="https://github.com/user-attachments/assets/3fa558cc-5b8e-42c3-84ee-6cf3c9aeccfb" />

   Restart Homey Pro 2023 so that it detects that more disk space has become available in the **USER** partition.

## Verifying MAX disk space available
<img width="852" height="418" alt="image" src="https://github.com/user-attachments/assets/c3a77c30-0184-47d2-b4a5-ccc0628d8c3b" />

Wait a moment until your Homey Pro 2023, with its new and many times larger CM4 module, has finished restarting.

Then go to https://my.homey.app/ or the homey app and click on the gear at the bottom of the menu on the left.

# Backup time
Now we have reached our goal! We have gone through the process of backing up the Linux operating system including the Homey software on the old/original CM4 module, replacing it with a new CM4 module with much larger memory and disk space, restoring the original operating system on the new CM4 module, jailbreaking our way into the Linux operating system behind the Homey software and finally expanding the USER disk space with a bunch of SSH system commands – SO NOW IT IS TIME TO TAKE A NEW BACKUP.

This backup will be a good starting point for the new CM4 module, if the developers behind Homey later try to cancel our upgrade. This backup cannot be used to restore to the old/original Homey Pro 2023 CM4 module, as it is adapted to 32 GB of disk space and not 8 GB, which is the original disk space.

In Part 1 – Backup of Homey’s operating system you can get help taking a new backup.

I would recommend that you save a backup file of both the old/original Homey Pro 2023 CM4 module and the new CM4 module on your PC in a safe place. It is best to make a backup of these backup images, e.g. to Microsoft Onedrive or similar.

IMPORTANT! You must never share your Homey backup image with others! Your Homey account is included in the backup and will be transferred to the recipient's Homey Pro 2023.

There have been rumors in several forums on the Internet that this backup cannot be restored on new CM4 modules. I have tested it and it works perfectly!
