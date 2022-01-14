---
title: "Debugging With the qorc-sdk"
description: "How to debug qorc-sdk based code on the EOS-S3"
layout: post
toc: true
comments: true
image: images/homepage_callout_qorc.jpg
hide: false
search_exclude: true
categories: [debugging, eoss3, qorc-sdk]
#metadata_key1: metadata_value1
#metadata_key2: metadata_value2
comments: true
sticky_rank: 1
---

# Debugging with the QORC SDK

There are 2 (interconnected) parts to debugging the code on the EOS-S3 with the QORC SDK:

- The Debugging Software Tools
- The Debug Probe

The choice of the debugging software tools influences what debug probe you can use.
The EOS-S3 being a Cortex-M4F based MCU, has a wide variety of options to choose from for the software tools, below is a list of option combinations:

1. JLink + Jlink Probes (JLink EDU / JLink EDU Mini / JLink BASE ...)
2. OpenOCD + SWD Probes (FT2232H-based probes, STLINK-v2 probes, JLink Probes...)
3. pyOCD + SWD Probes (CMSIS-DAP, JLink, STLINK-v2, picoprobe...)

There is another part of the debugging setup: the code environment.  
This largely depends on personal choices, such as:
1. use Vi/EMACS for code, and Commanline for build/debug/flash
2. use Eclipse-EmbedCDT for everything
3. Use VSCode for everything

In this post, I will focus on using VSCode for everything as I personally prefer this approach currently.

For Eclipse-EmbedCDT, there is already official docs which cover this to some extent: https://github.com/QuickLogic-Corp/qorc-sdk/blob/master/using_eclipse.rst  
The Eclipse approach is bit cumbersome to setup one time, but simple enough to use after that.

The Vi/Emacs/Commandline users are generally well versed in setting up specific personal configurations for use, and I will leave this out of the discussions.

Before we go on to the VSCode Setup, we would need to setup the QORC SDK, and the debug software tools.

## QORC SDK

The recommended way to use the QORC SDK painlessly, is to just let the `envsetup.sh` do the heavy lifting and install all the tools needed for build locally, within the QORC SDK directory itself: [QORC SDK automated-setup](https://github.com/QuickLogic-Corp/qorc-sdk/blob/master/quickstart.rst#automated-setup)

## gdb

This is a part of the ARM toolchain for Cortex-M processors, and should already be setup when we source the `envsetup.sh` from the root of the QORC SDK.

Check by running this from QORC SDK directory, after `envsetup.sh` is sourced:
```
$ which arm-none-eabi-gdb
arm_toolchain_install/gcc-arm-none-eabi-9-2020-q2-update/bin/arm-none-eabi-gdb

$ arm-none-eabi-gdb --version
GNU gdb (GNU Arm Embedded Toolchain 9-2020-q2-update) 8.3.1.20191211-git
Copyright (C) 2019 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.
```

## OpenOCD
{% include info.html text="TODO" %}

## JLink
{% include info.html text="TODO" %}

## pyOCD
{% include info.html text="TODO" %}

## VSCode Setup

I have 4 parts of the setup for using VSCode with any embedded project, which applies to QORC SDK as well:

- settings.json
  > Define setting specific to the project
- tasks.json
  > Define build/clean tasks
- c_cpp_properties.json
  > Define intellisense config
- launch.json
  > Define debugging config(s)

{% include info.html text="TODO" %}