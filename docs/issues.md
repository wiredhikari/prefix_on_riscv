### Issues faces so far
* Initiating a new profile (to-update)
* Stage 1
  *
* Stage 2
  *   
* Stage 3
  * fixing pam - sys-libs/pam was installing files outside prefix, giving the right path in ebuild fixed it 
  * fixing pax-utils - app-misc/pax-utils had been causing trouble as lib files were being installed outside prefix, adding ${EPREFIX} at respected paths fixed it 
