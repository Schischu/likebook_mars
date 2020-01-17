# Likebook Mars

## Windows drivers
https://github.com/rockchip-linux/tools/tree/rk3399/windows

## Linux
### Pulling partitions

Compile https://github.com/linux-rockchip/rkflashtool

Reboot into LOADER mode
adb reboot-bootloader

    sudo ./rkflashtool p
    rkflashtool: info: rkflashtool v5.2
    rkflashtool: info: Detected RK3368...
    rkflashtool: info: interface claimed
    rkflashtool: info: reading parameters at offset 0x00000000
    rkflashtool: info: size:  0x000003b1
    FIRMWARE_VER: 6.0.0
    MACHINE_MODEL: RK3368
    MACHINE_ID: 007
    MANUFACTURER: RK3368
    MAGIC: 0x5041524B
    ATAG: 0x00200800
    MACHINE: 3368
    CHECK_MASK: 0x80
    PWR_HLD: 0,0,A,0,1
    #KERNEL_IMG: 0x00280000
    #FDT_NAME: rk-kernel.dtb
    #RECOVER_KEY: 1,1,0,20,0
    #in section; per section 512(0x200) bytes
    CMDLINE: console=ttyS2 androidboot.baseband=N/A androidboot.selinux=permissive androidboot.hardware=rk30board androidboot.console=ttyS2 init=/init mtdparts=rk29xxnand:0x00002000@0x00002000(uboot),0x00002000@0x00004000(trust),0x00002000@0x00006000(wbf),0x00002000@0x00008000(misc),0x00008000@0x0000a000(resource),0x0000a000@0x00012000(kernel),0x00010000@0x0001c000(boot),0x00010000@0x0002c000(recovery),0x00038000@0x0003c000(backup),0x00040000@0x00074000(cache),0x00002000@0x000B4000(kpanic),0x00300000@0x000B6000(system),0x00008000@0x003B6000(metadata),0x00002000@0x003BE000(baseparamer),0x00020000@0x003C0000(radical_update),-@0x003E0000(userdata)

mtdparts show available partitions

    ./rkflashtool r uboot > uboot.img
    ./rkflashtool r trust > trust.img
    ./rkflashtool r wbf > wbf.img
    ./rkflashtool r misc > misc.img
    ./rkflashtool r resource > resource.img
    ./rkflashtool r kernel > kernel.img
    ./rkflashtool r boot > boot.img
    ./rkflashtool r recovery > recovery.img
    ./rkflashtool r backup > backup.img
    ./rkflashtool r cache > cache.img
    ./rkflashtool r kpanic > kpanic.img
    ./rkflashtool r system > system.img
    ./rkflashtool r metadata > metadata.img
    ./rkflashtool r baseparamer > baseparamer.img
    ./rkflashtool r radical_update > radical_update.img
    ./rkflashtool r userdata > userdata.img
or

    rkflashtool r 0x00002000 0x00002000 > uboot.img
    rkflashtool r 0x00004000 0x00002000 > trust.img
    rkflashtool r 0x00006000 0x00002000 > wbf.img
    rkflashtool r 0x00008000 0x00002000 > misc.img
    rkflashtool r 0x0000a000 0x00008000 > resource.img
    rkflashtool r 0x00012000 0x0000a000 > kernel.img
    rkflashtool r 0x0001c000 0x00010000 > boot.img
    rkflashtool r 0x0002c000 0x00010000 > recovery.img
    rkflashtool r 0x0003c000 0x00038000 > backup.img
    rkflashtool r 0x00074000 0x00040000 > cache.img
    rkflashtool r 0x000B4000 0x00002000 > kpanic.img
    rkflashtool r 0x000B6000 0x00300000 > system.img
    rkflashtool r 0x003B6000 0x00008000 > metadata.img
    rkflashtool r 0x003BE000 0x00002000 > baseparamer.img
    rkflashtool r 0x003C0000 0x00020000 > radical_update.img
    #rkflashtool r 0x003E0000 0x018f0000 > userdata.img
