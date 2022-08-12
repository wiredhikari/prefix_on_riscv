### Issues faced so far
* Initiating a new profile (to-update)
* Stage 1
  *
* Stage 2
  *   
* Stage 3
  * fixing pam - sys-libs/pam was installing files outside prefix, giving the right path in ebuild fixed it 
  * fixing pax-utils - app-misc/pax-utils had been causing trouble as lib files were being installed outside prefix, adding ${EPREFIX} at respected paths fixed it 
  * stage 3 fails on gentoo host because of host portage messing with prefix portage, so trying to solve this my masing host portage and rerunning the script
```
sudo mv /usr/bin/emerge-webrsync /usr/bin/emerge-webrsync1
sudo mv /usr/bin/emerge /usr/bin/emerge1
sudo mv /usr/lib/portage/ /usr/lib/portage1
sudo mv /usr/share/portage/ /usr/share/portage1
sudo mv /etc/portage/ /etc/portage1

```


* freedom-u-sdk
```
sudo mount -o bind /dev/pts ./dev/pts
sudo mount -t sysfs sys ./sys
sudo mount -t proc proc ./proc
sudo mount -o bind /dev ./dev
sudo mount tmpfs -t tmpfs ./run
```
* inside chroot(needed for python)
```
sudo mount --types tmpfs --options nosuid,nodev,noexec shm /dev/shm
sudo chmod 1777 /dev/shm /run/shm
```

### Pull Requests:
(#todo-ellaborate)
* #25855 https://github.com/gentoo/gentoo/pull/25855
* https://github.com/gentoo/gentoo/pull/25855
* https://github.com/gentoo/gentoo/pull/25667
* https://github.com/gentoo/prefix/pull/6
