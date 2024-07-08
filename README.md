# Workstone
#### Turning portable memory (SSD &amp; Flash-SSD) into a mobilized workstation built via Kubuntu!
---
&nbsp;&nbsp; **Go through this list of actions to turn your thumbdrive into a mobile linux workstation. This is a very generic method for ubuntu flavors to be used on a thumbdrive without fully installing with a LiveDVD. This is a common method for getting extra use out of a single machine. Use the thumbdrive on any machine and change your boot order to adjust for the thumbdrive and watch a new computer arise from your previous computer's ashes but when you are done and want to have fun again: Turn off the computer, unplug the thumbdrive & turn on your computer again! </br></br>&nbsp;&nbsp;&nbsp;   A great way to take a "gaming machine" and reuse it for the "office".** </br></br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;   **;}** </br>
 </br></br>
</br>

## Get the ISO
- &nbsp;&nbsp; I'm using <a href="https://Kubuntu.org" target="_blank" rel="noopener noreferrer">Kubuntu</a> but you can pick any ISO you'd like but you'll have to change the commands to meet your ISO type/version.

</br></br>

## Rufie the USB
- &nbsp;&nbsp; I'm using <a href="https://rufus.ie/en/" target="_blank" rel="noopener noreferrer">Rufus [4.5+]</a> because I'm using a version of Linux greater than versions 18 & 20. Most versions of Linux (especially Ubuntu Flavors & Debain Flavors) changed when MBR became the common Partition scheme for UEFI booting. YUMI, UUI, UnetBootin or most versions of Ventoy based ISO installers/burners don't work with UEFI + MBR over secureBOOT. So, if you want a multiboot in the quick-n-easy way (ventoy based installers), you'll most likely have to turn off secure boot & you may not get the "DisplayLink" drivers to work properly without secureBOOT.

</br></br>

## Edit the GRUB
- &nbsp;&nbsp; I'm not planing on installing this linux from a LiveDVD (the current way to full install onto a thumbdrive or partioned drive) so I'm going to edit to drop off at least the GRUB menu, you can actually edit to change the GRUB to suit your needs. For Example, if you install Linux onto your main drive you may want the GRUB menu to allow you to pick which Operating System or even the "Safe Mode" to fix things or do routine maintnace. In our case, we just want to attempt to drop into the desktop enviroment instead of the "Live-Desktop". Without using customizer & a Linux Live Wrapper that allows for disabling of disk-check with dedicated cdrom loading, the most we can do is edit a couple of files ahead of time. Once you have a "fully upgraded" or "fully installed" Linux, you can edit these files from the terminal within the browser otherwise the live-desktop will not allow us to update the GRUB file itself. After this you'll need to hold "shift" key while booting to get the GRUB menu. So, even if you setup your GRUB fancy, the below add-ons will then hide that GRUB menu as quickly as possible until you need it.

| File to edit | What to add & where |
|---|---|
| <code>USB/boot/grub/grub.cfg</code> | <code>set timeout=0</code> replace what says <code>set timeout=30</code> |
|  | <code>persistant quiet splash noprompt --- cdrom-detect/try-usb=true</code> where it says <code>persistant ---</code> |
|  |
| <code>USB/boot/grub/loopback.cfg</code> | <code>--- acpi=off quiet splash noprompt</code> where it says <code>--- quiet splash</code> |
| | |

</br></br>

## Edit in LINUX
- &nbsp;&nbsp; This is a quick introduction to the terminal aka konsole [console], you only need to do this if you were able to exit the "Live-Desktop" or have full installed. This will just help remove extra login & GRUB menus at boot by dropping all the wait times to zero.

| File to Edit | What to add & where |
|---|---|
| <code>/etc/default/grub/</code> | <code>GRUB_SAVEDEFAULT=true</code> above <code>GRUB_TIMEOUT=0</code> & add: <code>GRUB_HIDDEN_TIMEOUT=0</code> & <code>GRUB_HIDDEN_TIMEOUT_QUIET=0</code> after <code>GRUB_TIMEOUT=0</code> as each add as a new line |


</br></br>

## Connect the Universe

&nbsp;&nbsp; Visit: <a href="https://itsfoss.com/mount-exfat/" target="_blank" rel="noopener noreferrer">itsFOSS.com/mount-exFAT</a> for the following commands to connect to the universe for mounting & using exFAT drives (normally Hard-Drives [HDDs]).

<code>sudo add-apt-repository universe</code>

<code>sudo apt update</code>

<code>sudo apt install exfat-fuse</code>

<code>sudo apt install exfat-fuse exfat-utils</code>
 </br>&nbsp;&nbsp; **this last one, almost never works**


</br></br>


## Drive the Displays
- &nbsp;&nbsp; I use multiple displays and I use a J5create display adapter (works fine in my windows OS) and so I get these generic driver displays for one of my monitors. Still looking for a fix for my digital billboard used as a monitor (ACER #P237HL").

&nbsp;&nbsp; Download the packet: <a href="https://www.synaptics.com/products/displaylink-graphics/downloads/ubuntu" target="_blank" rel="noopener noreferrer">www.synaptics.com/products/displaylink-graphics/downloads/ubuntu</a> (look down for the buttons).

&nbsp;&nbsp; Visit: <a href="https://support.displaylink.com/knowledgebase/articles/684649" target="_blank" rel="noopener noreferrer">support.displaylink.com/knowledgebase/articles/684649</a> for the following commands to get generic <b><i>DisplayLink</i></b> display drivers.

<code>sudo apt-get update</code>

<code>sudo apt-get dist-upgrade</code>

- &nbsp;&nbsp; You will need to extract the zip files to where you can change-directory ("cd" command in the terminal) to the location. While in the file explorer, right click on the ".run" file, click properties and go through the settings to allow executable (may say "is exacutable"). Back in the terminal, change-directory into the location. Possible location could be: <code>cd ./Downloads</code>. Then run the file with this: <code>sudo ./displaylink-driver-xxxxx.run</code> but use the driver numbers (with dots/dashes/hyphens) instead of the x's before ".run".

- &nbsp;&nbsp; This will cause a SecureBoot and some changes before this secure boot may be lost (mostly theme related changes). The system will tell you it's about to secure boot and you'll have to use your keyboard arrow keys and enter key for these type of popup menu. It'll then ask for a password, this is only going to be used for confirming you asked to install this driver set. This will not become a password for the linux or device. Again, this password is only for confirming the secure boot upon the next bootup. The system will ask you if you want to restart, let it reboot.

#### You may need to readjust your boot settings during this reboot

- &nbsp;&nbsp; Once in the secure boot menu (a sometimes small blue box on the screen). You'll need to click "Enroll MOK" (should be the first option) then "Enroll" or "Approve" (sometimes it'll say enroll then ask if it's okay or cancel). Then finally let the system reboot again. It should reboot back into linux.


</br></br>

## Install the Apps
- &nbsp;&nbsp; We are going to install a bunch of applications and programs to either setup for later or for standard use. Install these in order shown and skip any application you'd like to not have installed. The choosen apps for this section are for various reasons including making this OS more productive capable or to install repos you may need for something else. A quick tip: after pikopixel.app you can just hit "up arrow" key to show the last input, delete the app name, put the next app name in and hit "Enter" key, then end with a confirm "y" then "Enter" key.

<code>sudo apt-get install ffmpeg</code>

<code>sudo snap install krita</code>

<code>sudo apt-get update && sudo apt-get install pikopixel.app</code>

<code>sudo apt-get install blender</code>

<code>sudo apt-get install obs-studio</code>

<code>sudo apt-get install inkscape</code>

<code>sudo apt-get install gimp</code>

<code>sudo apt-get install kdenlive</code>

<code>sudo apt-get install shotcut</code>

<code>sudo apt-get install winehq-devel</code>

<code>sudo apt-get install ardour</code>

<code>sudo apt-get install carla</code>

<code>sudo apt-get install audacity</code>

<code>sudo apt-get install qtractor</code>
  </br>&nbsp;&nbsp; **decide if you want to give extra permissions for jackd (I picked, "no")** 

<code>sudo apt-get install hydrogen</code>

&nbsp;&nbsp; Visit: <a href="http://yoshimi.github.io/downloads.html" target="_blank" rel="noopener noreferrer">http://yoshimi.github.io/downloads</a> & get the latest <code>tar.gz</code> from <a href="https://github.com/Yoshimi/yoshimi/tags" target="_blank" rel="noopener noreferrer">github</a>.
 - &nbsp;&nbsp; You may need to move the file to where you can change-directory ("cd" command in the terminal) to the location. It may drop to the "Desktop" or <code>/home/kubuntu/Downloads</code>. If it's the Downloads try <code>sudo ./Downloads</code> & if that works you'll see "~/Downloads$" in the terminal. Next open the file with this: <code>sudo tar -xvzf yoshimi-2.3.2.tar.gz</code>


</br></br>

## Close the Konsole
- &nbsp;&nbsp; Close the terminal program Konsole (click the "x" in top right of window box).

- &nbsp;&nbsp; Now reopen it again to begin with the last few installing steps.
 

</br></br>

## Get new Eyes
- &nbsp;&nbsp; I use DroidCam X for my main webcam system. FOSS & usefull.

  
Visit: <a href="https://www.dev47apps.com/droidcam/linux/" target="_blank" rel="noopener noreferrer">www.dev47apps.com/droidcam/linux</a> & click "Install" to get the following commands.

<code>cd /tmp/
wget -O droidcam_latest.zip https://files.dev47apps.net/linux/droidcam_2.1.3.zip</code>
  </br>&nbsp;&nbsp; **there's a return between /tmp/ & wget so that's basically two commands-in-one**

<code>unzip droidcam_latest.zip -d droidcam</code>

<code>cd droidcam && sudo ./install-client</code>

<code>sudo apt install libappindicator3-1</code>

<code>sudo apt install linux-headers-&#96;uname -r&#96; gcc make</code>

<code>sudo ./install-video</code>
</br>&nbsp;&nbsp; **may need to answer qeustions about a key, both answers are 0**

<code>sudo ./install-sound</code>

<code>sudo apt-get install adb</code>


</br></br>

## Telegram or Signal
- &nbsp;&nbsp; I'm grabbing Telegram upfront (I use it as a cloud storage pass between my phone & PC). I don't use this for anything other than this. I have telegram & signal on my phone for their inteded use.

<code>sudo snap install telegram-desktop</code>

 </br>
 
&nbsp;&nbsp; Visit: <a href="https://flathub.org/setup/Kubuntu" target="_blank" rel="noopener noreferrer">flathub.org/setup/Kubuntu</a> to get the following commands.

<code>sudo apt install flatpak</code>

<code>sudo apt install plasma-discover-backend-flatpak</code>

<code>sudo apt install plasma-discover-flatpak-backend</code>

<code>flatpak remote-add --if-not-exists flathub https://dl.flathub.org/repo/flathub.flatpakrepo</code>


</br></br>

## Off & Back-On
- &nbsp;&nbsp; Turn off and then back-on the system and go back into linux. At this point, this should directly load back into linux if the shutdown process goes correctly (fully shuts down without needing to click enter). </br></br>**If shutdown messes up, you'll have to hit enter then if it doesn't shutdown in 40 seconds or less, you'll have to hold the button and hard-shut-down the machine.**


</br></br>

## Edit & Upgrade
- &nbsp;&nbsp; Edit the theme & do the little things in the settings (main linux settings & browser settings). Once you are done getting your desktop feeling and looking good, insert this into the terminal:
</br></br>
<code>sudo apt-get upgrade</code> </br></br>&nbsp;&nbsp; **This may take a while and there's a chance it'll fail the first time. If it fails, it'll have you retype the command <code>sudo apt-get</code> then the special bit stated on screen (copy and paste with mouse) then click the "Enter" key wait for finish then reinsert <code>sudo apt-get upgrade</code> & hit the "Enter" key again.**


 


 
 
 
 
 
 
 







