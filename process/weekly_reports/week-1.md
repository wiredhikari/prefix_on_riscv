# Week 1 Report for RISC-V Support for Gentoo Prefix

Hello all,
Hope you all are doing great, this is my weekly report for the first week of Google Summer of Code. For the initial weeks I have planned to fix issues which occur during the 3 stages of Prefix.
During the first week I have made pr's to fix errors that occur during compilation of stage 1 and 2. I have uploaded all the logs and issues I faced in prefix_on_riscv repository[7].
To start with, I worked on making a riscv profile for prefix[2] and added a symlink[4] which allowed stage 1 to continue. As we don't use multilib in prefix, we have decided to settle on one ABI (lp64d).
Added patches to some of the issues that occur during stage 2: The app-misc/pax_utils​ failed to compile[1] due to files getting compiled outside of prefix. To fix this, In src_install, I changed _emake DESTDIR="${D}"​ ... to _emake DESTDIR="${ED}"​ ... in pax-utils-1.3.4.ebuild​. The `sys-libs/pam` failed to compile[3] due to similar reasons as `app-misc/pax_utils`. And also caused further issues while compiling `pkgconf`. To fix this we had initially decided to fix the ebuild and add support for prefix to it, but it will be better to avoid pulling it by any other package as its not required for prefix. A lot of package depend on it so we started working on the latter solution.
To test on riscv using my local machine I am using riscv-chroot-env[5], plct-lab’s machine, dlan’s qemu image. I found riscv-chroot-env pretty fast and easy to use, after using the riscv profile and solving issues with pam, pax-utils and pkgconf, the build went upto stage 3 but couldn't continue due to the limitations of the chroot environment[6], it couldn't run emerge -uDNv system​ and stopped working there, also got permission errors when changing ownership (chown), but its fine to ignore when bootstrapping Prefix. I am working on fixing chroot env issue[6] so we can continue running emerge -uDNv system​.
Then comes plct-lab’s real riscv machine, I have access to it via ssh and it is pretty fast so far. After using the profile it got through stage 1 but couldn't compile gcc after that due to missing gcc-multilib and due to less privileges to users we can't install packages on the machine. Also while fixing things on this machine we found out host system needs to have pax-utils installed to use scanelf, to fix this we are planning to add a check in the script to make bootstrapping process more independent from the host.
I discussed this with mentors and we are planning to have a common environment to share the work done and to fix the limited privilege issues we faced earlier.
This is my summary of my work done in week one. I learned more about writing ebuilds and testing them, made scripts to speed up my testing and made pull requests to fix pam, pax-utils, created a to riscv profile for prefix and symlink to riscv profile. My mentors have been really helpful and helped me during all problems I came across.
[1]: https://github.com/gentoo/gentoo/pull/25855
[2]: https://github.com/gentoo/gentoo/pull/25667
[3]: https://github.com/gentoo/gentoo/pull/25850
[4]: https://github.com/gentoo/prefix/pull/6
[5]: https://gitlab.com/cwittlut/riscv-chroot-env
[6]: https://github.com/bekcpear/riscv-chroot-env/issues/1
[7]: https://github.com/wiredhikari/prefix_on_riscv/tree/main/logs
-- 
Regards,
wiredhikari
