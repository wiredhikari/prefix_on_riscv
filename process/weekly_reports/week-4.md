Hello everyone,
So the fourth week of Google Summer of Code has come to an end and here is my weekly report for the same.

This week we got a working prefix with Stage 3 compiling till the end. Profile for lp64d got merged as well.

Earlier I use to pull my gentoo fork for testing but as the pull request for lp64d no-multilib Profile[1] got merged, I tested with the official Gentoo repository.

Current approach is to fix the bugs locally and see how far stage 3 goes. So after the fixes we did in previous weeks there are 2 major bugs that need fix to complete stage 3.

We need to add check for scanelf​ in bootstrap script as its needed in the host for ncurses to install during stage 2.

libfl.so.6​ library is missing due to which riscv64-pc-linux-gnu-ar​ and riscv64-pc-linux-gnu-ranlib​ fails to execute.

I tried bootstrapping by fixing these issues locally and it continued till the end.
It was decided that we add support to lp64d as of now and accordingly I have added the patch to Gentoo Prefix[2], other profiles are under 17.0​ directory while RISC-V is under 20.0​, it has been fixed accordingly.

Also continued documentation on “Porting Prefix to New Architecture” and Setting up RISC-V environment for testing prefix.
In upcoming weeks I plan to continue testing with the latest packages and work on libfl.so.6​ and scanelf​ issue. Post that I will work on keywording packages with RISC-V.

[1]https://github.com/gentoo/gentoo/pull/26211
[2] https://github.com/gentoo/prefix/pull/13
–
Regards,
wiredhikari
