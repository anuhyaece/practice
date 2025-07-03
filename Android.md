
## Introduction to Android
- Android is an open-source mobile operating system developed by Google.
- It is built on the Linux kernel and designed for touchscreen devices (smartphones, tablets, etc.).
- Supports millions of apps through the Google Play Store.
- Written primarily in Java and Kotlin.

---

## Key Features:
- Open-source and customizable
- Wide device compatibility
- Rich APIs for UI, camera, GPS, sensors, etc.
- Backed by Google with regular updates

---


## Android Architecture:

    Android architecture is structured in layers:
    
                        +------------------------+
                        | Applications           |
                        +------------------------+
                        | Application Framework  |
                        +------------------------+
                        | Android Runtime (ART)  |
                        | Native Libraries       |
                        +------------------------+
                        | HAL (Hardware Abstraction Layer) |
                        +------------------------+
                        | Linux Kernel           |
                        +------------------------+
    
- **Linux Kernel:** Handles core system services like process and memory management.
- **HAL:** Interfaces between hardware and higher-level APIs.
- **Libraries:** Native C/C++ libraries for graphics, media, and databases (SQLite).
- **Android Runtime (ART):** Executes app bytecode and manages memory.
- **Application Framework:** APIs used to build Android apps (Activity Manager, Notifications, etc.).
- **Applications:** Pre-installed and user-installed apps.

---

## Difference Between Linux OS and Android OS

| Feature/Aspect            | **Linux OS**                                              | **Android OS**                                                     |
| ------------------------- | --------------------------------------------------------- | ------------------------------------------------------------------ |
| **Target Devices**        | Servers, desktops, embedded systems                       | Smartphones, tablets, smart TVs, wearables                         |
| **User Interface**        | Typically uses desktop environments (GNOME, KDE)          | Mobile GUI with touch-based interface                              |
| **Kernel**                | Linux kernel                                              | Modified Linux kernel (with Android-specific changes)              |
| **Developed By**          | Community, Linux Foundation                               | Google (based on Linux kernel)                                     |
| **File System Hierarchy** | Standard Linux file system (`/etc`, `/bin`, `/usr`, etc.) | Customized file system for mobile (e.g., `/data`, `/system`)       |
| **Application Format**    | Executables (`.out`, `.elf`) or packages (`.deb`, `.rpm`) | APK (Android Package) files                                        |
| **Package Management**    | APT, YUM, DNF, etc.                                       | Google Play Store, ADB install, sideloading                        |
| **Default Shell**         | Bash, Zsh                                                 | No user-visible shell (though shell exists under-the-hood via ADB) |
| **Programming Language**  | Mostly C, C++, Python, Bash scripting                     | Java, Kotlin, XML (for UI), C/C++ (NDK)                            |
| **System Access**         | Full root access available to user                        | Root access restricted by default (can be unlocked)                |
| **Multitasking**          | True multitasking                                         | Managed multitasking (background limits)                           |
| **System Services**       | Init/Systemd for booting and services                     | Android Init, Zygote, Binder, and custom daemons                   |
| **Usage Purpose**         | General computing, development, servers                   | Mobile computing, apps, touch-based UI                             |
In Linux we have **IPC** mechanisms to communicate between two processes, In android we have **Binder IPC** to communicate between two processes.

---

## What is Booting?
Booting is the process of starting or restarting the system by loading the operating system into memory.

---
## Types of Boot
**Hard Boot**
- It is also called as cold boot.
- Booting a system from a powered off state.
- Happens when the device is turned on.
- **Example:** Turning on your PC using the power button.

---
**Soft Boot**
- It is also called as warm boot.
- Restarting the system without turning off the power.
- Triggered by OS restart, reset button, or a software command.
- **Example:** Clicking Restart in Windows.

---
**Dual Boot**
- Booting into more than one OS (user selects one during startup).
- Example: Windows + Linux on one machine.

---
**Fast Boot**
- Fast Boot is a feature that reduces boot time by skipping certain hardware checks and initializations during startup.
- Skips some initial checks (like POST) to speed up the booting process.

---
**Secure Boot**
- Secure Boot is a security feature that prevents unauthorized or malicious code from running during the boot process.
- A UEFI feature that ensures only trusted software is loaded during boot.

---

## Android Boot Process (When You Power On)

- **Bootloader:** Initializes hardware and loads the kernel.  
- **Linux Kernel:** Starts managing CPU, memory, drivers.  
- **Init:** Android’s init process starts system services (like Wi-Fi, Bluetooth).  
- **Zygote:** A special process that loads common app code (Java libraries) and starts apps quickly by forking.  
- **System Server:** Starts Android’s core services (WindowManager, PackageManager, etc.).  
- **Home/Launcher App:** The main screen you see (with icons and widgets) starts.  

---
## Difference betwwen Linux boot and Android boot

| Feature                  | Linux Boot Process                                    | Android Boot Process                                     |
|--------------------------|--------------------------------------------------------|-----------------------------------------------------------|
| **Target Devices**       | Desktops, Servers, Embedded Systems                    | Smartphones, Tablets, Smart Devices                       |
| **Operating System Type**| General-purpose OS                                     | Mobile OS based on Linux kernel                           |
| **Bootloader**           | GRUB, LILO, U-Boot                                     | Android Bootloader with Fastboot support                  |
| **Kernel**               | Standard Linux kernel                                  | Modified Linux kernel with mobile-specific changes        |
| **Init System**          | `systemd`, `SysVinit`, `Upstart`                       | Android `init` with `.rc` configuration scripts           |
| **Root Filesystem**      | Uses `/`, `/etc`, `/home` (ext4, xfs, etc.)            | Uses `/system`, `/vendor`, `/data` (ext4, YAFFS2, F2FS)   |
| **Boot Image Format**    | Separate `vmlinuz` (kernel) and `initrd`               | Single `boot.img` (kernel + ramdisk + DTB)                |
| **Startup Services**     | Daemons like `sshd`, `cron`, `networkd`                | `system_server`, `Zygote`, Android Framework services     |
| **Java Runtime**         | Optional (only when installed)                         | Core component (Zygote spawns ART/Dalvik runtime)         |
| **App Launch Mechanism** | Standard process execution                             | Apps launched by forking Zygote process                   |
| **Recovery Mode**        | Not standard; may require custom setup                 | Dedicated Recovery Partition                              |
| **Fastboot Mode**        | Not typical                                             | Standard bootloader mode for flashing and debugging       |
| **Secure Boot**          | UEFI Secure Boot (optional, PC-specific)               | Verified Boot (dm-verity, AVB enforced on most devices)   |
| **Update Mechanism**     | Package managers (`apt`, `yum`) or scripts             | OTA updates, often with A/B partitioning scheme           |
| **Filesystem Structure** | Conventional Linux hierarchy                           | Partition-based (boot, system, vendor, recovery, etc.)    |
| **Target Users**         | Developers, Sysadmins, General Users                   | End Users, App Developers, OEMs                           |

---
## Interview Questions
- what is Android?
- Difference between Linux os and Android os.
- Explain about Android Architecture.
- Explain about Android booting Process.

---

## Downloading and Building Source code
- repo init manifest.xml
- repo sync
- cd apps/LINUX/android
- source build/envsetup.sh
- lunch devicename-variantname
   **ex:** lunch tinker-user
- make
## Build variants
- **userdebug:** Engineering build W/O root(possible to root) and it is used for testing and debugging.
- **user:** production build W/O root(different kernel config).
- **eng:** Engineering build W/root.
   
    

    
