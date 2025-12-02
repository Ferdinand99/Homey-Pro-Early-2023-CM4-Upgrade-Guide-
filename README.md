# Homey Pro (Early 2023) – CM4 Upgrade Guide  
Upgrade to Raspberry Pi Compute Module 4 (8GB RAM / 32GB eMMC)

---

## ⚠️ Disclaimer

This guide describes a **hardware modification that is not supported by Athom**.  
Performing this upgrade will **void your warranty** and carries a risk of damaging your device if done incorrectly.

You should only attempt this if you are comfortable with electronics, static-sensitive components, and device disassembly.

Proceed at your own risk.

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

12. Reinstall the spacers and black heatsink-fin module. Carefully realign and reattach the 4 heatsink nuts (best done with precision tools, possibly holding nuts with pliers while tightening). 
Homey Guide

13. Close the plastic case: reassemble housing, reinstall the 4 bottom screws, and snap/attach the rubber base.
