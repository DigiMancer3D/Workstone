# Workstone
#### Turning portable memory (SSD &amp; Flash-SSD) into a mobilized workstation built via Kubuntu!
---
</br></br>
</br>

## Get the ISO
I'm using <a href="https://Kubuntu.org" target="_blank" rel="noopener noreferrer">Kubuntu</a> but you can pick any ISO you'd like but you'll have to change the commands to meet your ISO type/version.

</br></br>

## Rufie the USB
I'm using <a href="https://rufus.ie/en/" target="_blank" rel="noopener noreferrer">Rufus [4.5+]</a> because I'm using a version of Linux greater than versions 18 & 20. Most versions of Linux (especially Ubuntu Flavors & Debain Flavors) changed when MBR became the common Partition scheme for UEFI booting. YUMI, UUI, UnetBootin or most versions of Ventoy based ISO installers/burners don't work with UEFI + MBR over secureBOOT. So, if you want a multiboot in the quick-n-easy way (ventoy based installers), you'll most likely have to turn off secure boot & you may not get the "DisplayLink" drivers to work properly without secureBOOT.

</br></br>

## Edit the GRUB
I'm not planing on installing this linux from a LiveDVD (the current way to full install onto a thumbdrive or partioned drive) so I'm going to edit to drop off at least the GRUB menu, you can actually edit to change the GRUB to suit your needs. For Example, if you install Linux onto your main drive you may want the GRUB menu to allow you to pick which Operating System or even the "Safe Mode" to fix things or do routine maintnace. In our case, we just want to attempt to drop into the desktop enviroment instead of the "Live-Desktop". Without using customizer & a Linux Live Wrapper that allows for disabling of disk-check with dedicated cdrom loading, the most we can do is edit a couple of files ahead of time. Once you have a "fully upgraded" or "fully installed" Linux, you can edit these files from the terminal within the browser otherwise the live-desktop will not allow us to update the GRUB file itself.

| File to edit | What to add & where |
|---|---|
| <code>USB/boot/grub/grub.cfg</code> | <code>set timeout=1</code> replace what says <code>set timeout=30</code> |
|  | <code>noprompt cdrom-detect/try-usb=true persistant acpi=off quit splash ---</code> where it says <code>persistant ---</code> |
|  |
| <code>/etc/default/grub/</code> | <code>GRUB_SAVEDEFAULT=true</code> above <code>GRUB_TIMEOUT=0</code> & add: <code>GRUB_HIDDEN_TIMEOUT=0</code> & <code>GRUB_HIDDEN_TIMEOUT_QUIET=0</code> after <code>GRUB_TIMEOUT=0</code> as each add as a new line |
|---|---|


</br></br>
 







