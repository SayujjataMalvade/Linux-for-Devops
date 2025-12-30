# Linux Boot Process & TCP Handshake
---

## 📌 Linux Boot Process

The Linux boot process consists of multiple stages that initialize hardware, load the operating system kernel, and finally present the user with a login interface.

### 🔹 1. Power ON & POST (Power-On Self-Test)

* When the system is powered on, the firmware performs **POST**.
* POST checks critical hardware components such as CPU, RAM, disk, and peripherals.
* If POST fails, the system will not proceed further.

---

### 🔹 2. BIOS / UEFI

* After POST, **BIOS** (or **UEFI** in modern systems) is executed.
* It initializes hardware components and identifies a **bootable device**.
* BIOS then hands control to the **bootloader**.

---

### 🔹 3. Bootloader (GRUB)

* The bootloader is typically **GRUB (Grand Unified Boot Loader)**.
* In legacy systems, GRUB resides in the **MBR (Master Boot Record)** (512 bytes).
* GRUB allows:

  * Selecting the operating system
  * Loading the Linux kernel into memory
  * Passing boot parameters to the kernel

---

### 🔹 4. Kernel

* The **Linux kernel** is the core of the operating system.
* It performs:

  * Memory management
  * Process scheduling
  * Device driver initialization
* The kernel mounts the root filesystem and starts the first user-space process.

---

### 🔹 5. Init / systemd (PID 1)

* The kernel launches **`systemd`** (or `init` in older systems).
* `systemd` always runs with **Process ID 1 (PID 1)**.
* It initializes services, mounts filesystems, and manages system targets.

#### 🎯 Targets (Runlevels)

| Runlevel | Target            | Description      |
| -------- | ----------------- | ---------------- |
| 0        | poweroff.target   | Shutdown         |
| 1        | rescue.target     | Single-user mode |
| 3        | multi-user.target | CLI mode         |
| 5        | graphical.target  | GUI mode         |
| 6        | reboot.target     | Reboot           |

To check the current default target:

```bash
systemctl get-default
```

---

### 🔹 6. User Space

* Once the default target is reached, the login screen (CLI or GUI) is presented.
* Users can now interact with the system.

---

## 🛠️ Real-World Problems Solved by Understanding Boot Process


| Problem                  | Cause                           | Resolution                      |
| ------------------------ | ------------------------------- | ------------------------------- |
| Black screen on startup  | Display manager failure         | Use TTY and fix via `systemctl` |
| No bootable device found | Missing bootloader              | Reinstall GRUB                  |
| System hangs during boot | Corrupt `fstab` or kernel panic | Use recovery mode or Live CD    |

---

## 🌐 TCP Three-Way Handshake

The **TCP three-way handshake** establishes a reliable connection between a client and a server before data transfer begins.

### 🔁 Steps Involved

1. **SYN (Synchronize)**

   * Client sends a SYN packet to the server requesting a connection.

2. **SYN-ACK (Synchronize-Acknowledgment)**

   * Server acknowledges the request and responds with SYN-ACK.

3. **ACK (Acknowledgment)**

   * Client sends an ACK, and the connection is established.

✔️ After this handshake, data transmission begins securely.

---

### 🔐 Practical Example (With Proxy)

* Client → Proxy Server → Database Server
* The proxy handles the handshake and forwards validated traffic.
* This architecture improves **security, privacy, and scalability**.

---




