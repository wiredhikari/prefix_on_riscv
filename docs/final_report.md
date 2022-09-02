## GSoC 2022 Project Report
<div align="center">
<img src="./../assets/images/gentoo.svg" width="200"/> <img src="./../assets/images/arrow.svg" width="200"/> <img src="./../assets/images/gsoc.svg" width="200"/> 
</div>

# RISC-V support for Gentoo Prefix

**Student:** [Atharva Amritkar](https://github.com/wiredhikari)

**Organisation:** [Gentoo](https://www.gentoo.org/)

**Mentors:** [Guilherme Amadio](https://github.com/amadio), [Kenneth Hoste](https://github.com/boegel)

**Project repository:** [Gentoo](https://github.com/gentoo/gentoo), [Prefix](https://github.com/gentoo/prefix), [EESSI](https://github.com/EESSI)

**Project proposal:** [Proposal link](https://docs.google.com/document/d/1vKRaRKEWt-485oVdCfxLecXKbMwgajlv-6ZOGflwW6g/edit#heading=h.7uif4cjti9op)

## Table of Contents

- [RISC-V support for Gentoo Prefix](#risc-v-support-for-gentoo-prefix)
  - [Table of Contents](#table-of-contents)
  - [Project overview](#project-overview)
  - [Project Deliverables](#project-deliverables)
    - [A working Profile for RISC-V architecture.](#a-working-profile-for-risc-v-architecture)
    - [Bootstrap and use a Gentoo Prefix system on RISC-V architecture.](#bootstrap-and-use-a-gentoo-prefix-system-on-risc-v-architecture)
    - [Test and keyword necessary packages in Gentoo for RISC-V.](#test-and-keyword-necessary-packages-in-gentoo-for-risc-v)
    - [Documentation on “Porting Prefix to new Architectures”.](#documentation-on-porting-prefix-to-new-architectures)
    - [Thorough documentation of all work done via blogs and Gentoo Wiki.](#thorough-documentation-of-all-work-done-via-blogs-and-gentoo-wiki)
  - [Project Results](#project-results)
    - [Contributions](#contributions)
    - [Profile](#profile)
    - [Prefix](#prefix)
    - [Test and Keyword](#test-and-keyword)
    - [EESSI Overlay](#eessi-overlay)
  - [Conclusion](#conclusion)
  - [Acknowledgement](#acknowledgement)


## Project overview

RISC-V is an emerging open CPU architecture that is starting to be adopted well beyond the embedded domain; the European Processor Initiative (EPI) project is a clear example of this.

Gentoo Prefix is a key component in the European Environment for Scientific Software (EESSI) project, which is a collaboration between various partners in the High-Performance Computing (HPC) community to build a common stack of scientific software installations for HPC systems and beyond, including laptops, personal workstations, and cloud infrastructure.

RISC-V is one of the target CPU architectures in the EESSI project, and good support for RISC-V in Gentoo Prefix is a crucial first step towards supporting RISC-V in EESSI. 

The project majorly involved creating of the new profile in Gentoo Prefix of RISC-V, fixing the bugs faced during bootstrap of Stage-1, Stage-2 and Stage-3. 

## Project Deliverables

### A working Profile for RISC-V architecture.
### Bootstrap and use a Gentoo Prefix system on RISC-V architecture.
### Test and keyword necessary packages in Gentoo for RISC-V.
### Documentation on “Porting Prefix to new Architectures”.
### Thorough documentation of all work done via blogs and Gentoo Wiki.



## Project Results 



### Contributions

### Profile

| Pull Requests                                        | Description                                                                                     |
|------------------------------------------------------|-------------------------------------------------------------------------------------------------|
| [#25667](https://github.com/gentoo/gentoo/pull/25667)| profiles: initial commits for riscv profile for prefix                                          |
| [#26211](https://github.com/gentoo/gentoo/pull/26211)| profiles/default/linux/riscv/20.0/rv64gc/lp64d/prefix: new riscv prefix profile                 |

### Prefix

| Pull Requests                                        | Description                                                               |
|------------------------------------------------------|---------------------------------------------------------------------------|
| [#6](https://github.com/gentoo/prefix/pull/6)        | bootstrap-prefix.sh: adding riscv profile                                 |
| [#13](https://github.com/gentoo/prefix/pull/13)      | bootstrap-prefix.sh: using lp64d for riscv profile                        |


### Test and Keyword

| Pull Requests                                        | Description                                                               |
|------------------------------------------------------|---------------------------------------------------------------------------|
| [#24630](https://github.com/gentoo/gentoo/pull/24630)| sys-apps/lsd: keyword ~riscv                                              |
| [#24904](https://github.com/gentoo/gentoo/pull/24904)| riscv: keyword app-crypt/asekey, app-accessibility/yasr, sys-apps/watchdog|
| [#26850](https://github.com/gentoo/gentoo/pull/25850)| sys-libs/pam: Add prefix support                                          |
| [#26855](https://github.com/gentoo/gentoo/pull/25855)| app-misc/pax-utils: Add prefix support                                    |
| #||
| #||


### EESSI Overlay

| Issues and Pull Requests                                        | Description                                                               |
|-----------------------------------------------------------------|---------------------------------------------------------------------------|
| [#80](https://github.com/EESSI/gentoo-overlay/pull/80)          | sys-cluster/reframe: Keyword ~riscv                                       |
| [#79](https://github.com/EESSI/gentoo-overlay/issues/79)        | Remove sys-libs/pam from our overlay                                      |
| [#78](https://github.com/EESSI/gentoo-overlay/pull/78)          | sys-apps/archspec: Keyword ~riscv and dev-python/click version bump       |

## Conclusion

I was able to complete all of the goals that were decided for the project and it got completed before the timeline which gave us more time for testing Prefix and packages.


## Acknowledgement

I am extremely grateful to get mentored by [Guilherme Amadio](https://github.com/amadio) and [Kenneth Hoste](https://github.com/boegel), for their constant support, guidance and help.

Thanks to Google and Gentoo Linux for providing me the opportunity to work on this amazing project. It has been a great learning experience and contributing to Gentoo has been an amazing experience. I would certainly want to continue contributing and help the community.
