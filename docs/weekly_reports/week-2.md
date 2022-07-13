# Week 2
Greetings,

Hope you all are doing good, the second week of coding period is over, it has been fun and quite some progress on the project has happened. To start with, I tested the new riscv profile for prefix on different riscv machines/images, have updated the changes and rebased the pull request [1]. After adding support to packages as discussed in last week's blog, I did testing for stage 1 and 2 on various machines and they got compiled without any trouble. 
    
During testing, the major bug it was seen that pkgconf failed due to missing `CHOST`, we which will be fixed by patching it for `riscv` in bootstrap script. 

Also, encountered portage falling back to root/portage and user/group in the gentoo chroot environment, similar to [2]. Host portage interfers with prefix installation. So, the current progress is that stage 3 stops towards the end as it ain't able to run `emerge -uDNv system` on the system with gentoo host and asks for root access. Although it will continue on non-gentoo host, which we will be testing further. To test further we are working with freedom-u-sdk [3] and a fedora riscv qemu image to test prefix.

So, this is the brief report for the second week, for the upcoming weeks I will be working more on testing and fixing the issues during stage 3. Thanks to Kenneth Hoste for setting up the shared VM to experiment with emulated RISC-V environment. Also had a fruitful discussions with Guilherme Amadio for the current issues in stage 3 and their workarounds, we will look into them and hope we get a working stage 3 soon.

Regards,
Atharva

[1] https://github.com/gentoo/gentoo/pull/25667
[2] https://bugs.gentoo.org/766417
[3] https://github.com/sifive/freedom-u-sdk




- Investigate why portage falls back to root/portage user/group in the chroot environment
 - stopped the compilation process on stage-3 as user couldnt run `emerge -uDNv system` .
- See https://bugs.gentoo.org/766417 (similar problem when user is managed by Kerberos). In this case, portage falls back to non-prefix mode, which should not happen. My guess is that the same is happening due to the fact the bootstrap process is being run from within a chroot environtment [G. Amadio]
- Documentation about how to add new architecture to prefix
- issue with your fetching
- we are testing on different environments
    freedom-u-sdk
    
