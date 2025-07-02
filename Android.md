
## Introduction to Android

    Android is an open-source mobile operating system developed by Google.
    
    It is built on the Linux kernel and designed for touchscreen devices (smartphones, tablets, etc.).
    
    Supports millions of apps through the Google Play Store.
    
    Written primarily in Java and Kotlin.

---

## Key Features:

    Open-source and customizable
    
    Wide device compatibility
    
    Rich APIs for UI, camera, GPS, sensors, etc.
    
    Backed by Google with regular updates

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
    
    Linux Kernel: Handles core system services like process and memory management.
    
    HAL: Interfaces between hardware and higher-level APIs.
    
    Libraries: Native C/C++ libraries for graphics, media, and databases (SQLite).

    Android Runtime (ART): Executes app bytecode and manages memory.
    
    Application Framework: APIs used to build Android apps (Activity Manager, Notifications, etc.).
    
    Applications: Pre-installed and user-installed apps.

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


   
    

    
