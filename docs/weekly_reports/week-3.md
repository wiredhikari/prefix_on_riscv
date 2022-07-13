# Week3 GSoC
Hello all,
 
The 3rd week of my GSoC project has come to an end and this is the brief overview of the progress so far.

To start with, most of the week has been spent on testing, we have decided upon a non-gentoo riscv environment for testing and are finally able to get `emerge -u system` working, (128/143) packages have been compiled so far and we can will get it working soon. We also have profiles for risc-v merged in Gentoo. Have also been working on a new profile for lp64d no-multilib and sent the pr for the same [3].

During the week we tried several non-gentoo riscv environments for testing like fedora,ubuntu riscv qemu and freedom-u-sdk[1]. The environment of freedom-u-sdk seems to be working great and is minimal, also doesnt give much errors like other images, so we have decided to settle on it.

During stage 2 it was noticed that missing `libfl.so.2` lib on host caused several `sys-libs/attr` to fail and it has been fixed. This didn't occur in other riscv environments so seems to be a `freedom-u-sdk` specific issue. Similarly, missing `libtinfo.so` lib caused issues for `sys-devel/gettext`.

So far I have been testing the new profile with my custom bootstrap-prefix.sh script [4] and added a new profile in for lp64d riscv [3]; will push the changes to upstream and get reviews for the same. There are some ambiguities with freedom-u-sdk host libraries, will dig more to check if we can make bootstrap script more independant from host.Talking about the upcoming plans,I plan to do testing on various machines. Currently last 15 packages are bring compiled while writing this, python and glibc might are expected to give some errors, stage 3 we will have a working riscv profile soon if the compilation gets successful.I am collecting logs and the issues faced during bootstrap [2] which will eventuall help in documentation of "Porting Prefix to new Architecture".

So this is the report of things accomplished in Week 3. Mentors have been immensely helpful, looking forward to next week.

[1]: https://github.com/sifive/freedom-u-sdk
[2]: https://github.com/wiredhikari/prefix_on_riscv
[3]: https://github.com/gentoo/gentoo/pull/26211
[4]: https://raw.githubusercontent.com/wiredhikari/prefix/kernel/scripts/bootstrap-prefix.sh
---
Regards,
wiredhikari
