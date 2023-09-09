# M2-S3
M2-S3


## Building the Linux Kernel


```sql
Configure Kernel: KConfig/Defconfig ---> Build using kBuild
```
- Introduction to <mark style="background: #BBFABBA6;">kConfig</mark>
	- `Text format which controls kernel configuration.`
	- Steps:
	```bash
		make menuconfig # trigger kConfig.
		# output after config
		# .config file on source tree of kernel.
	```
- Kernel <mark style="background: #BBFABBA6;">defconfig</mark>
	- `Default Configuration, .config provided by Hardware vendor.`
- Building Kernel <mark style="background: #ABF7F7A6;">kBuild</mark>.
```bash
building Kernel.
#output: 
# ELF File with all symbols and table #vmlinux.
# Artifcats:
(1) - Image  ---> Binary Version of vmLinux # make Image
(2) - zImage ---> Compressed Image. # make zImage
(3) - uImage ---> Compressed Image + UBoot Bootloader Header. # make uImage


# make process
(1) - make ARCH=arm64
(2) - CROSS_COMPILE=aarch64-none-linux-gnu mrproper # clean .config.
(3) - CROSS_COMPILE=aarch64-none-linux-gnu defconfig

#example:
# make -j4 ARCH=arm64 CROSS_COMPILE=aarch64-none-elf-  HOSTCFLAGS="-I/Applications/ArmGNUToolchain/12.2.rel1/aarch64-none-elf/aarch64-none-elf/include" Image

# Targets:
	# mrproper
	# defconfig
	# all ---> vmlinux.
	# modules --> modules.
	# dtbs ---> device tree


#steps:
Decisions:
    (1)- Version => Kernel.
    (2)- Arch    => ARM64
0. ToolChain
1. Configure kernel.
2. Build Kernel.
3. Root-file system as defined in Standard RFS.
4. Busy Box &rarr; min utilities needed.
5. Dependencies of Busy-Box.
6. Create initramfs.
7. Run it on QEMU.
```
- Boot Kernel on <mark style="background: #FFB86CA6;">QEMU</mark>
