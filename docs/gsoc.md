+++
title = "RISC-V Support for Gentoo Prefix"
date = 2022-06-15

[taxonomies]
tags = ["gsoc" , "gentoo" , "prefix" ]
+++
Process of bootstrapping gentoo prefix on RISC-V architecture
<!-- more -->


----------------------------------------------------------------
## Overview
#write in the end
## Workflow
* your custom prefix fork
* using tags to use gentoo fork
* testing on 3 risc-v environments
* What happens after pr's get merged
* 

### Machines used for development:


#### riscv-chroot-env
This environment 
https://gitlab.com/cwittlut/riscv-chroot-env
#### plct-lab

#### dlan's qemu image
(todo add links)
I have been using dlan's qemu risc-v image for testing, it worked well except it is pretty old and causes several issues during compilation so it went upto compiling python and couldnt move further due to date and time issues. It can be fixed but currently relying more on riscv-chroot-env and plct-lab's machine.
#### Kenneth's RISC-V environment
Mentors are working on setting up a RISC-V environment which can be accessible for them and me with root privilages, so it will be easy to share logs and work in a easier way than the older workflow.

----------------------------------------------------------------
## Current Progress:

### Setting up a profile for RISC-V:

#todo - Issue -> link -> workaround
### Issues faced during Stage-1:
After having a symlink to RISC-V profile in bootstrap-prefix.sh https://github.com/gentoo/prefix/pull/6, the compilation didn't cause any errors.
### Issues faced during Stage-2:
* ncurses issue on plct machine and workaround :  https://raw.githubusercontent.com/wiredhikari/prefix_on_riscv/main/logs/stage1_logs/stage2.log . The host was missing pax-utils package so installing it in user and giving the relevent path to the user fixed it.
* gcc error due to missing multilib libraries: https://raw.githubusercontent.com/wiredhikari/prefix_on_riscv/main/logs/stage2_logs/stage2.log .This was a problem with plct-lab's host machine and due to limited permissions, had to pause the work on this machine.
* 
### Issues faced during Stage-3:
* pam error https://github.com/wiredhikari/prefix_on_riscv/tree/main/logs/pam_error
* portage eror https://github.com/wiredhikari/prefix_on_riscv/tree/main/logs/portage_error
* pkg_conf error https://raw.githubusercontent.com/wiredhikari/prefix_on_riscv/main/logs/stage3/stage3.log

## Future Work:
* We will have a working gentoo prefix working soon on RISC-V, then we will do rigerous testing of all three stages.
* Write documentation on porting prefix to new architecture
* Test and keyword packages for RISC-V.
#to-add
----------------------------------------------------------------

## References

### Repositories I am working on:

* Documentation : https://github.com/wiredhikari/prefix_on_riscv
* Prefix Fork  : https://github.com/wiredhikari/prefix
* Gentoo Fork   : https://github.com/wiredhikari/portage

### Pull Requests:
*  profiles: initial commits for riscv profile for prefix https://github.com/gentoo/gentoo/pull/25667
*  app-misc/pax-utils: Add prefix support https://github.com/gentoo/gentoo/pull/25855
*  sys-libs/pam: Add prefix support https://github.com/gentoo/gentoo/pull/25850
*  bootstrap-prefix.sh: adding riscv profile #6  https://github.com/gentoo/prefix/pull/6
