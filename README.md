# Crouton-Reference


####To Update Crouton
------------------
Download latest chroot-http://goo.gl/fd3zc

Press CTRL-ALT-T

`Shell`

`sudo sh ~/Downloads/crouton -u -n precise (or other chroot, trusty, raring etc.)`

####Startxfce4 Error
-------------------
if `sudo startxfce4` results in error

`sudo enter-chroot` = enter the terminal of chroot w/o launching GUI

####Force Chroot Unmount
-------------------
`sudo unmount-chroot -a -f`

######Failed to Unmount
-------------------
`y` to send SIGTERM to mount processes

####Update Ubuntu Release
-------------------
[Solution](https://github.com/dnschneid/crouton/wiki/Upgrade-chroot-release)

####To Backup as .tar
-------------------
`sudo edit-chroot -b chrootname`

####To Restore with an Existing Install
-------------------
`sudo edit-chroot -r chrootname`

####To Restore from New
-------------------
`sudo sh ~/Downloads/crouton -f mybackup.tar.gz`

####List All Chroots and Info
-------------------
`sudo edit-chroot -al`

####Fix freon error
-------------------
`sudo CROUTON_BRANCH=x11_freon sh ~/Downloads/crouton -t xfce -n precise -u`

####Reinstall xorg Server
-------------------
`sudo apt-get install --reinstall xserver-xorg-coresudo apt-get install --reinstall xserver-xorg-core`

####Cycle Mount of Chroot
-------------------
`sudo enter-chroot croutoncycle next`

####Only Start Chroot if it Contians Viable Packages
-------------------
`sudo startxfce4 -n precise -t xfce,keyboard,xorg`

####Rename Chroot
-------------------
`sudo edit-chroot -m <newname> <oldname>`

####Fix DPKG Error 'dpkg: error processing package' after trusty update
-------------------
`sudo dpkg --purge -a`
`sudo apt-get update`
`sudo apt-get -f install`

####Update Unable to Connect to Precise Server
-------------------
Error: "`requesting key 142986CE from hkp server keyserver.ubuntu.com`"

Fix: "https://github.com/dnschneid/crouton/issues/162"

"The keyserver thing is actually only an issue when installing the Precise release (the default). The script pulls in a xubuntu PPA that maintains a newer version of Xfce since the version in Precise is extremely old.

Ways around this are installing a different release (i.e. -r raring), or manually fixing the script after it fails by doing the following:
1. Enter the chroot as root: sudo enter-chroot -u root and say "no" to doing the prep script. The root user always exists, so this should work fine.
2. Use vi to edit /prepare.sh. There should be a line towards the bottom that checks if the release is precise, and if so, adds the Xfce 4.10 PPA. Break the check by adding a random letter to 'precise' or similar, or remove the if...fi entirely.
3. Save and exit the chroot, then enter it again normally and run the preparation script, which will succeed.

You can use something similar to the above steps to diagnose, debug and work around any issues in the preparation script."





Crouton Github
https://github.com/dnschneid/crouton
