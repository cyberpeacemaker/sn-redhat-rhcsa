
- hardware [motherboard, cpu{x86/x64}, ram, disk{SSD/HDD}, peripheral]
- firmware[ROM, flash memory],nvram, {[BIOS, MBR]/[UEFI, GUID partition table]}
- os {windows, linux}, [bootloader{Windows boot manager, GRUB}, kernel, File System]


---


## Simple Mental Model

* **Architecture** → what kind of CPU runs the code
* **Firmware (BIOS/UEFI)** → how the machine starts
* **Partition scheme (MBR/GPT)** → how the disk is organized
* **Bootloader** → how the OS is loaded

1. **Power on**.
2. **Load firmware (BIOS/UEFI)** from ROM/flash into memory.
3. **POST (Power-On Self Test)** checks basic hardware functionality.
4. **Read partition table** from the bootable disk (MBR for BIOS, GPT for UEFI).
5. **Locate bootloader** (in MBR or ESP).
6. **Bootloader loads the kernel** into memory and hands control over to it.
7. **Kernel initializes** and starts the OS.
8. **Operating system finishes booting** and becomes usable.


## 6. Boot Flow Comparison 

### BIOS + MBR Boot

1. Power on
2. BIOS runs
3. BIOS reads **MBR**
4. MBR boot code runs
5. Bootloader loads OS

### UEFI + GPT Boot

1. Power on
2. UEFI runs
3. UEFI reads **GPT**
4. UEFI loads bootloader from **EFI System Partition**
5. Bootloader loads OS

Architecture: x86 / x86-64
Vendors: Intel, AMD