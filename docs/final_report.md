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
  - [Project Results](#project-results)
    - [Contributions](#contributions)
    - [Profile](#profile)
    - [Prefix](#prefix)
    - [Test and Keyword](#test-and-keyword)
    - [EESSI Overlay](#eessi-overlay)
  - [Conclusion](#conclusion)
  - [Acknowledgement](#acknowledgement)


## Project overview




## Project Deliverables



## Project Results 



### Contributions

### Profile

| PR link                                              | Description                                                                                     |
|------------------------------------------------------|-------------------------------------------------------------------------------------------------|
| [#25667](https://github.com/gentoo/gentoo/pull/25667)| profiles: initial commits for riscv profile for prefix                                          |
| [#26211](https://github.com/gentoo/gentoo/pull/26211)| profiles/default/linux/riscv/20.0/rv64gc/lp64d/prefix: new riscv prefix profile                 |

### Prefix

| PR link                                              | Description                                                               |
|------------------------------------------------------|---------------------------------------------------------------------------|
| [#6](https://github.com/gentoo/prefix/pull/6)        | bootstrap-prefix.sh: adding riscv profile                                 |
| [#13](https://github.com/gentoo/prefix/pull/13)      | bootstrap-prefix.sh: using lp64d for riscv profile                        |


### Test and Keyword

| PR link                                              | Description                                                               |
|------------------------------------------------------|---------------------------------------------------------------------------|
| [#24630](https://github.com/gentoo/gentoo/pull/24630)| sys-apps/lsd: keyword ~riscv                                              |
| [#24904](https://github.com/gentoo/gentoo/pull/24904)| riscv: keyword app-crypt/asekey, app-accessibility/yasr, sys-apps/watchdog|
|||
|||
|||
|||


### EESSI Overlay


## Conclusion

I was able to complete all of the goals that were decided for the project and it got completed before the timeline which gave us more time for testing Prefix and packages.


## Acknowledgement

I am extremely grateful to get mentored by [Guilherme Amadio](https://github.com/amadio) and [Kenneth Hoste](https://github.com/boegel), for their constant support, guidance and help.

Thanks to Google and Gentoo Linux for providing me the opportunity to work on this amazing project. It has been a great learning experience and contributing to Gentoo has been an amazing experience. I would certainly want to continue contributing and help the community.
