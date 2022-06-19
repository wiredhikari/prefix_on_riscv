Hello all,

Hope you all are doing great, this is my weekly report for the first week of Google Summer of Code. For the initial weeks I have planned to fix issues which occur during the 3 stages of Prefix.



Talking about the issues faced during the three stages:







To test on riscv using my local machine I am using riscv-chroot-env[1], plct-lab’s machine, dlan’s qemu image[2]. I found riscv-chroot-env pretty fast and easy to use, after using the riscv profile and solving issues with pam, pax-utils and pkgconf as discussed above, the build went upto stage 3 but couldnt continue due to the limitations of chroot environment my mentor Kenneth is setting up





This is my summary of work dont in



[1]: https://gitlab.com/cwittlut/riscv-chroot-env
[2]:
[3]:
[4]:


Regards,
wiredhikari
