## In that study a custom Linux is installed to the Orange Pi. All steps made manually from power-on to login.

`u-boot` -> `kernel` -> `device tree` -> `rootfs`

**1. Toolchain**

   Cross compilers installed *(toolchain directory)*. Linaro's cross compilers used in that study.

**2. Bootloader**

   U-Boot downloaded, configured, and compiled *(u-boot directory)*.
   After that, First Stage Bootloader and Second Stage Bootloader images installed to the MBR formatted SD Card beginning from 8th sector with the following command:

    $ dd if=u-boot-sunxi-with-spl.bin of=/dev/mmcblk0 bs=1024 seek=8

*Note: Every board has different aspects to load First Stage and Second Stage Bootloaders. OrangePi loads directly from the boot sector.*

**3. Kernel**

- Kernel has been downloaded.
- OrangePi specific patches applied.
- `.config` file has been created and customized.
- The kernel has been compiled.
- Device Tree Source (dts) compiled, and Device Tree Blob (dtb) derived.

**4. RootFS**

- `/bin`, `/sbin`, `/usr/bin`, `/usr/sbin` filled with BusyBox.
- `/boot` contains zImage (Linux Kernel) and `/boot/dtb` contains DeviceTreeBlob (dtb).
- `/lib` consists of libraries derived from the toolchain.
