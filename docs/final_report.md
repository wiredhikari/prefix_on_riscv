## GSoC 2022 Project Report

<div align="center">
<img src="./../assets/images/gentoo.svg" width="200"/> <img src="./../assets/images/arrow.svg" width="200"/> <img src="./../assets/images/gsoc.svg" width="200"/> 
</div>

# RISC-V support for Gentoo Prefix

**Student:** [Atharva Amritkar](https://github.com/wiredhikari)

**Organisation:** [Gentoo Linux](https://www.gentoo.org/)

**Mentors:** [Guilherme Amadio](https://github.com/amadio), [Kenneth Hoste](https://github.com/boegel)

**Project repository:** [Gentoo](https://github.com/gentoo/gentoo), [Prefix](https://github.com/gentoo/prefix), [EESSI](https://github.com/EESSI)

**Project proposal:** [Proposal](https://docs.google.com/document/d/1vKRaRKEWt-485oVdCfxLecXKbMwgajlv-6ZOGflwW6g/edit#heading=h.7uif4cjti9op)

## Table of Contents

- [RISC-V support for Gentoo Prefix](#risc-v-support-for-gentoo-prefix)
  - [Table of Contents](#table-of-contents)
  - [Project Overview](#project-overview)
  - [Project Deliverables](#project-deliverables)
  - [Project Results](#project-results)
    - [A working Profile for RISC-V architecture.](#a-working-profile-for-risc-v-architecture)
    - [Bootstrap and use a Gentoo Prefix system on RISC-V architecture.](#bootstrap-and-use-a-gentoo-prefix-system-on-risc-v-architecture)
    - [Test and keyword necessary packages in Gentoo for RISC-V.](#test-and-keyword-necessary-packages-in-gentoo-for-risc-v)
    - [Documentation on “Porting Prefix to new Architectures”.](#documentation-on-porting-prefix-to-new-architectures)
  - [Contributions](#contributions)
    - [Profile](#profile)
    - [Prefix](#prefix)
    - [EESSI Overlay](#eessi-overlay)
    - [Prefix Support](#prefix-support)
    - [Test and Keyword](#test-and-keyword)
  - [Conclusion](#conclusion)
  - [Acknowledgement](#acknowledgement)
## Project Overview

[RISC-V](https://riscv.org/) is an emerging open CPU architecture that is starting to be adopted well beyond the embedded domain; the European Processor Initiative (EPI) project is a clear example of this.

[Gentoo Prefix](https://wiki.gentoo.org/wiki/Project:Prefix) is a key component in the European Environment for Scientific Software ([EESSI](https://www.eessi-hpc.org/)) project, which is a collaboration between various partners in the High-Performance Computing (HPC) community to build a common stack of scientific software installations for HPC systems and beyond, including laptops, personal workstations, and cloud infrastructure.

RISC-V is one of the target CPU architectures in the EESSI project, and good support for RISC-V in Gentoo Prefix is a crucial first step towards supporting RISC-V in EESSI. The project majorly involved creating of the new profile in Gentoo Prefix of RISC-V, fixing the bugs faced during bootstrap of Stage-1, Stage-2 and Stage-3.

## Project Deliverables

- A working Profile for RISC-V architecture.
- Bootstrap and use a Gentoo Prefix system on RISC-V architecture.
- Test and keyword necessary packages in Gentoo for RISC-V.
- Documentation on “Porting Prefix to new Architectures”.


## Project Results

### A working Profile for RISC-V architecture.

Worked on making a RISC-V profile for prefix and added a symlink, this allowed stage 1 to continue. We are using kernel-3.2+, as we don't have enough multilib support for RISC-V, we have decided to settle on one ABI (lp64d) and use a no-multilib profile. 

Current features of RISC-V Profile for Prefix:

**`make.defaults`**
```
ARCH="riscv"
CHOST="riscv64-pc-linux-gnu"
ACCEPT_KEYWORDS="~riscv"
SYMLINK_LIB=""
LIBDIR_lp64d="lib"
```

**`profiles/prefix/linux/riscv/parent`**
```
../../../default/linux/riscv/20.0/rv64gc/lp64d
..
```

Symlink for RISC-V in bootstrap prefix script:

**`bootstrap-prefix.sh`**
```
riscv64-pc-linux-gnu)
  profile=${profile_linux/ARCH/riscv}
  profile=${profile/17.0/20.0/rv64gc/lp64d}
  ;;
```      

### Bootstrap and use a Gentoo Prefix system on RISC-V architecture.

Firstly, we created a RISC-V Profile for Gentoo Prefix, made necessary changes in bootstrap-prefix.sh script which allowed Stage-1 to continue. After having a new profile for RISC-V, the latest python and portage was installed in `${EPREFIX}/tmp` and then Stage-2 emerged build utilities and coretools from the base RISC-V profile. After getting Stage-2 to work, GCC installed by Portage to install a Gentoo base system in `${EPREFIX}`. Then portage rebuild all installed packages with custom optimizations and features. 

Worked on fixing all the bugs that I got during the three stages, this was the major task as we face a lot of issues during the compilation of the three stages. Some issues got fixed as bootstrap script got patches, some got updated with version bumps, some needed special attention and RISC-V support.

There were several environments we tested the new Profile for Gentoo Prefix, and see if any specific environment caused issue. After rigorous testing, we got it working on available RISC-V environments.


### Test and keyword necessary packages in Gentoo for RISC-V.

Tested 150+ packages during the process for RISC-V and Prefix. We tested it with FEATURES="test" and all the USE flags enabled, for those packages which restricted testing, tried testing them manually. Some packages needed Prefix support and were mandatory for the compilation of the three stages. The list of pull requests made is [here](#test-and-keyword). 

### Documentation on “Porting Prefix to new Architectures”.

The thorough documentation of all work done has been uploaded has been uploaded in the form of weekly reports on [gentoo-soc](https://archives.gentoo.org/gentoo-soc/) mailing list. Compile contents in the weekly reports written and document “Porting Prefix to new Architectures”, which might help the developers to Port Prefix to new Architecture in future.
The [documentation](https://github.com/wiredhikari/prefix_on_riscv/blob/main/docs/porting.md) gives a walkthrough on making a new profile and how stages in Gentoo Prefix work. Following that a walkthrough on Keywording Packages. We have structured it so that someone new with Prefix can follow it to get the new profile for Prefix working.

## Contributions

### Profile

| Pull Requests                                         | Description                                                                     |
| ----------------------------------------------------- | ------------------------------------------------------------------------------- |
| [#25667](https://github.com/gentoo/gentoo/pull/25667) | profiles: initial commits for riscv profile for prefix                          |
| [#26211](https://github.com/gentoo/gentoo/pull/26211) | profiles/default/linux/riscv/20.0/rv64gc/lp64d/prefix: new riscv prefix profile |

### Prefix

| Pull Requests                                   | Description                                               |
| ----------------------------------------------- | --------------------------------------------------------- |
| [#6](https://github.com/gentoo/prefix/pull/6)   | bootstrap-prefix.</span>sh: adding riscv profile          |
| [#13](https://github.com/gentoo/prefix/pull/13) | bootstrap-prefix.</span>sh: using lp64d for riscv profile |

### EESSI Overlay

| Issues and Pull Requests                                 | Description                                                         |
| -------------------------------------------------------- | ------------------------------------------------------------------- |
| [#78](https://github.com/EESSI/gentoo-overlay/pull/78)   | sys-apps/archspec: Keyword ~riscv and dev-python/click version bump |
| [#79](https://github.com/EESSI/gentoo-overlay/issues/79) | Remove sys-libs/pam from our overlay                                |
| [#80](https://github.com/EESSI/gentoo-overlay/pull/80)   | sys-cluster/reframe: Keyword ~riscv                                 |

### Prefix Support

| Issues and Pull Requests                              | Description                                                                    |
| ----------------------------------------------------- | ------------------------------------------------------------------------------ |
| [#26850](https://github.com/gentoo/gentoo/pull/25850) | sys-libs/pam: Add prefix support                                               |
| [#26855](https://github.com/gentoo/gentoo/pull/25855) | app-misc/pax-utils: Add prefix support                                         |
| [#26346](https://github.com/gentoo/gentoo/pull/26346) | app-portage/prefix-toolkit: riscv keywording                                   |
| [#835069](https://bugs.gentoo.org/835069)             | sys-devel/gcc-10.3.1_p20211126 failed to build while building prefix on gentoo |

### Test and Keyword

| Pull Requests                                         | Description                                                                |
| ----------------------------------------------------- | -------------------------------------------------------------------------- |
| [#24630](https://github.com/gentoo/gentoo/pull/24630) | sys-apps/lsd: keyword ~riscv                                               |
| [#24904](https://github.com/gentoo/gentoo/pull/24904) | riscv: keyword app-crypt/asekey, app-accessibility/yasr, sys-apps/watchdog |
| [#26506](https://github.com/gentoo/gentoo/pull/26507) | dev-util/patchelf,dev-lua/{luajson,lua-bit32,luaposix}: keywording ~riscv  |
| [#26508](https://github.com/gentoo/gentoo/pull/26508) | dev-util/hermes,sys-cluster/lmod: keywording ~riscv                        |
| [#26679](https://github.com/gentoo/gentoo/pull/26679) | keyword riscv for packages in app-portage                                  |
| [#26725](https://github.com/gentoo/gentoo/pull/26725) | RISC-V keyword for app-arch/\*                                             |
| [#26803](https://github.com/gentoo/gentoo/pull/26803) | dev-python/semver: ~riscv keywording                                       |
| [#26848](https://github.com/gentoo/gentoo/pull/26848) | sys-apps/cinit: adding prefix support                                      |
| [#26853](https://github.com/gentoo/gentoo/pull/26853) | sys-apps/fxload:add prefix support and riscv keyword                       |
| [#26869](https://github.com/gentoo/gentoo/pull/26869) | keyword ~riscv for sys-apps                                                |
| [#26960](https://github.com/gentoo/gentoo/pull/26960) | app-arch/alien: ~riscv keyword                                             |

## Conclusion

I was able to complete all of the goals that were decided for the project and it got completed before the timeline which gave us more time for testing Prefix and keywording packages with RISC-V. I would thank my mentors for guiding me throughout the journey. I loved working on this project and I would continue working and contributing to the community. 

For me, Open-Source seemed like a wild forest which pretty much confused me, but contributing to Gentoo Linux is one of the best experiences I have had and it gave me quite some clarity and confidence on contributing to large codebases and fixing issues. Thanks to Google Summer of Code I got this opportunity to learn and contribute for this amazing organization. It has been a fun experience. I am grateful that I got an opportunity to get mentored by such experienced developers, they helped and guided me whenever I got stuck and thanks to them for bearing the silly mistakes I did and helping me throughout the journey. 

## Acknowledgement

I am extremely grateful to get mentored by [Guilherme Amadio](https://github.com/amadio) and [Kenneth Hoste](https://github.com/boegel), for their constant support, guidance and help. Also the Gentoo Community has been immensely helpful and developers guided me throughout the project.

Thanks to Google and Gentoo Linux for providing me the opportunity to work on this amazing project. It has been a great learning experience and contributing to Gentoo has been an amazing experience. I would certainly want to continue contributing and help the community.
