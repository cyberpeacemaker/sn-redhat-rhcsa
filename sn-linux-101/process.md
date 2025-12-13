`Once the BIOS/UEFI hands control over to the bootloader, the bootloader (like GRUB) is responsible for loading the Linux kernel into memory.`
BIOS/UEFI, Bootloader, `Linux Kernel`

After the kernel is loaded, it performs a hardware initialization and basic setup (like detecting devices, mounting file systems, etc.).

Once the kernel has done this, it starts the first user-space process, and this is systemd (at least in Red Hat and other modern Linux distributions). So, systemd is spawned by the kernel, not directly by the BIOS/UEFI.

### The Key Sequence in a Linux Boot (with `systemd`):

1. **BIOS/UEFI**: Initializes hardware and hands control to the bootloader (e.g., **GRUB**).
2. **GRUB**: Loads the Linux kernel into memory.
3. **Linux Kernel**: Initializes hardware, mounts the root filesystem, and starts the first user-space process (`systemd`).
4. **`systemd`**: Now, **`systemd`** takes over. It is the **first user-space process** (PID 1) started by the kernel. It is responsible for:

   * Mounting filesystems.
   * Starting system services (e.g., networking, SSH, etc.).
   * Managing processes throughout the system's lifetime.

### Important Clarification:

* **`systemd` is not the parent of everything**, although it is the first process that gets run from **user-space**.
* The kernel itself **starts the `systemd` process**, and from there, `systemd` manages other processes.
* `systemd` is just **one part of the boot process** that takes over once the kernel is up and running.

* **`systemd` is not the "root" process** in the same way the root directory (`/`) is the top of the file system tree.
* It is the **first process that runs after the kernel**, and from there, it manages the system.
* The **BIOS/UEFI** is completely separate from `systemd` and has a different role: it deals with hardware initialization and handing control to the bootloader, which loads the kernel.

---

systemd
kthreadd (kernel thread)

---

daemon, service