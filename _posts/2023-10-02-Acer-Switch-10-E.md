---
layout: post
categories: Linux
title: "Installing Linux on Acer Switch 10E (SW3-016)"
date: 2023-09-16 21:00:00 +0800
tags: [linux, blog]
---
*(This is not a full guide on how to install Manjaro on this system, it's a documentation of the problems I encountered and how I solved it.)*

I bought this convertible second-handed in my freshman year in university, it was one of the worst device I ever used, but it was always a secondary device for me so I just keeping it and used it from time to time.

At that time I was still using Windows in all of my PCs but I was beginning to try out Linux. This was the first device I changed to Linux completely. I was using Kubuntu at that time, and it served me well through the uni, I even wrote most of the code of my graduation project with this nugget.

As of last week, it had been sit on my shelf for about 2 years because of 2 things:
- The keyboard was broken and I didn't bother to get it fixed.
- A weird bug happened when I was distro hopping: the wifi stopped working all together.

The original plan was to somehow make it tablet only, make a shell to hold the keyboard's PCB(there's a usb port on it), and stick a hub on the back with one of those nano sized usb wifi adapter.

I installed Manjaro on it but later never bother to finish the project.

Until last week, I picked up this almost abandon project. And I started by designing & printing the shell using FreeCAD.

![](/assets/images/posts/2023-10-02-Acer-Switch-10-E/minimized-dock.jpg){: width="500" : height="auto"}

The shell was the easy part unfortunately...

## First Problem: Where's the battery indicator?

I was trying out EndeavourOS with this device but I noticed the battery indicator was missing, I thought it was EndeavourOS's problem so switched to pure Arch(took me a while) and later switched back to Manjaro, but the problem persisted.

After some trial and error and installing stuff here & there, turn's out is cause by the Linux kernel 6.5. This kernel version for some reason can't properly read the battery from the ACPI tables.

**Switching to 6.4 or older version fixed the problem.**

## Second Problem: Touch Control on KDE Plasma (X11) SUCKS

During the trial and error, using the device without a mouse and keyboard was real pain. Dragging icons didn't work 90% of the time and felt janky through and through, touch input won't register in context menu & lack of on screen keyboard.

Even after installed [OnBoard](https://launchpad.net/onboard), the experience still sucks but suck less.

So, how do I solved this issue? **Switching to Wayland!**

To my surprise, Plasma on Wayland has improved a lot since the last time I've tried it, and it handle touch input like a champ, no more janks dragging across the screen.

As for the on screen keyboard, OnBoard doesn't support Wayland but I found [Maliit](https://github.com/maliit/keyboard), and what's better it's that Maliit support Chinese input which I still need from time to time.

Setting up Maliit took me some trials, but I got it in the end. Here's a rough walkthrough:

1. Install `maliit-framework` & `maliit-keyboard` and `libchewing` or `libpinyin` depend on your need.
2. Make sure `~/.config/kwinrc` has these config set:
    ```conf
    ...
    [Wayland]
    VirtualKeyboardEnabled=true
    ...
    [XWayland]
    VirtualKeyboardEnabled=true

    ```
3. Enable virtual keyboard in `Settings` -> `Input Device` -> `Virtual Keyboard` and select `Maliit`.
4. Enable Chinese input through `gsettings`:
    ```bash
    # Set the keyboard language to English & Chewing.
    $ gsettings set org.maliit.keyboard.maliit enabled-languages "['en', 'zh-hant']"

    # Set the keyboard language to English & Pinyin.
    $ gsettings set org.maliit.keyboard.maliit enabled-languages "['en', 'zh-hans']"
    ```

## Last Problem: The Bugged Out On Board WiFi

I stumbled upon this [blog post](https://hansdegoede.livejournal.com/24132.html) written by hansdegoede when I was looking for solution for the battery indicator issue, it turns out that wifi problem is caused by the shitty & weird BIOS implementation.

In short, the BIOS changes its DSDT on the fly using the boot loader efi it recognized, and the SD card reader's controller's DSDT entries are set to invalid values *(because why the hell not?)*, and causing the wifi card to be offline because it is connect through the controller.

Instead of using the blog post's solution (which I can't reproduce), I use another mechanism of Linux, **ACPI table override**.

Here's a rough walkthrough with the help of this [Arch Wiki article](https://wiki.archlinux.org/title/DSDT):

1. Tools preparation: install `acpica` & `cpio`
2. Dump & decompile the table
    ```bash
    # Dump DSDT
    $ sudo cat /sys/firmware/acpi/tables/DSDT > dsdt.aml

    # Decompile the dsdt's aml to dsl, this will produce dsdt.dsl
    $ iasl -d dsdt.aml
    ```
3. Modify the dsl
    ```c
    ...
    DefinitionBlock ("", "DSDT", 2, "ACRSYS", "ACRPRDCT", 0x00000003)
    //                                                    ^^^^^^^^^^ --> Increase the last value.
    ...
            Device (SDHB)
            {
                Name (WADR, Zero)
                Name (WHID, "80860F14") // --> Change to "Name (_HID, "80860F14")"
                Name (AHID, "INT33BB")
    ...
            Device (SDHC)
            {
                Name (WHID, "80860F14") // --> Change to "Name (_HID, "80860F14")"
                Name (AHID, "INT33BB")
    ...
    ```
4. Recompile, package & put it into place
    ```bash
    # Compile to aml.
    $ iasl -tc dsdt.dsl

    # Package it (done loacally in your working directory.)
    $ mkdir -p kernel/firmware/acpi
    $ cp dsdt.aml kernel/firmware/acpi
    $ find kernel | cpio -H newc --create > acpi_override

    # Put into place.
    $ sudo cp acpi_override /boot
    ```
5. Set up bootloader, I'm using GRUB
    1. Edit `/etc/default/grub`
        ```conf
        # Add this line
        GRUB_EARLY_INITRD_LINUX_CUSTOM="acpi_override"
        ```
    2. Update grub config
        ```bash
        $ sudo update-grub
        ```
6. Reboot

After that the wifi card should be in working order.

---

That's all the major problem I've encountered so far. I might update more once I found more issue. Until then, I hope this will help someone with the same problems.
