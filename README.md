# Secure Kernel Concept

Secure Kernel Concept (SKC) is a next-generation, immutable, and highly secure Unix-based operating system. This OS has been designed to be in-line with POSIX standards while offering advanced security features such as application sandboxing, file integrity checks, and differential file-based updates. It's designed to be multi-user and multi-tasking.

> This is just a concept and not a real operating system.

## 📋 Index

- [Secure Kernel Concept](#secure-kernel-concept)
  - [📋 Index](#-index)
  - [🎯 Project Goals](#-project-goals)
  - [📅 Development Stages](#-development-stages)
    - [🛠️ Development](#️-development)
    - [🚀 Release](#-release)
    - [🔐 Security Enhancement](#-security-enhancement)
  - [📂 Directory Structure](#-directory-structure)
    - [🍉 Root Directory](#-root-directory)
    - [🙇 User Home directory](#-user-home-directory)
  - [🔩 System Settings](#-system-settings)
  - [📂 Filesystems Supported](#-filesystems-supported)
  - [🚗 Drivers](#-drivers)
    - [📦 Storage Drivers](#-storage-drivers)
    - [🎮 Graphics Drivers](#-graphics-drivers)
    - [🔊 Audio Drivers](#-audio-drivers)
    - [🌐 Network Drivers](#-network-drivers)
    - [⌨ Input / Peripheral Drivers](#-input--peripheral-drivers)
    - [💽 Peripheral and Expansion Support](#-peripheral-and-expansion-support)
    - [📸 Multimedia Drivers](#-multimedia-drivers)
    - [🔋 Power Management](#-power-management)
  - [🌐 Protocols and Standards Compliance](#-protocols-and-standards-compliance)
  - [📚 System Libraries](#-system-libraries)
    - [Core System Libraries](#core-system-libraries)
    - [Graphics and UI](#graphics-and-ui)
    - [Audio and Media](#audio-and-media)
    - [Networking](#networking)
    - [Additional Libraries](#additional-libraries)
  - [🎨 Desktop Environment](#-desktop-environment)
  - [🔐 Security Architecture](#-security-architecture)
    - [Core Security Features](#core-security-features)
    - [Encryption and Security Tools](#encryption-and-security-tools)
    - [System Updates and Maintenance](#system-updates-and-maintenance)
  - [☕ Essentials Binaries](#-essentials-binaries)
  - [📥 Pre-installed Developer Tools](#-pre-installed-developer-tools)
  - [🛠️ Pre-installed Applications](#️-pre-installed-applications)
  - [🌱 APIs](#-apis)
    - [Window creation and management](#window-creation-and-management)
      - [Basic Window Initialization](#basic-window-initialization)
      - [Window Flags](#window-flags)
      - [Window Methods](#window-methods)
    - [Window Rendering and Drawing](#window-rendering-and-drawing)
      - [Rendering Context](#rendering-context)
      - [Drawing Primitives](#drawing-primitives)
      - [Image Support](#image-support)
    - [Widget System](#widget-system)
      - [Button Example](#button-example)
      - [Other available widgets](#other-available-widgets)
      - [Custom Widgets](#custom-widgets)
    - [Window Event Handling](#window-event-handling)
      - [Mouse Events](#mouse-events)
      - [Keyboard Events](#keyboard-events)
      - [Touch and Gesture support](#touch-and-gesture-support)
    - [Layout Management](#layout-management)
      - [Grid Layout](#grid-layout)
      - [Stack LAyout](#stack-layout)
    - [Compositing and Transparency](#compositing-and-transparency)
    - [Multi-Screen and High-DPI Support](#multi-screen-and-high-dpi-support)
      - [Multi-Screen Handling](#multi-screen-handling)
    - [Accessibility Features](#accessibility-features)
      - [Screen Reader Integration](#screen-reader-integration)
      - [Keyboard Navigation](#keyboard-navigation)
    - [Desktop Widgets](#desktop-widgets)
      - [Simple Desktop Widget](#simple-desktop-widget)
      - [Rendering Contents in Widgets](#rendering-contents-in-widgets)
      - [Updating Widget Content](#updating-widget-content)
    - [Taskbar Widgets (Modular Islands)](#taskbar-widgets-modular-islands)
      - [Creating a Taskbar Widget](#creating-a-taskbar-widget)
      - [Interaction in Taskbar Widgets](#interaction-in-taskbar-widgets)
      - [Dynamic Island Configuration](#dynamic-island-configuration)
    - [System Notifications](#system-notifications)
      - [Simple Notification](#simple-notification)
      - [Interactive Notifications](#interactive-notifications)
      - [Notification Categories and Priority](#notification-categories-and-priority)
    - [System Tray](#system-tray)
      - [Adding Icons to the System Tray](#adding-icons-to-the-system-tray)
      - [System Tray Menu](#system-tray-menu)
    - [Pop-up Dialogs](#pop-up-dialogs)
      - [Open File Dialog](#open-file-dialog)
      - [Prompt Dialog](#prompt-dialog)
      - [Splash Screens](#splash-screens)
    - [Access to the Desktop](#access-to-the-desktop)
      - [Setting a Static Wallpaper](#setting-a-static-wallpaper)
      - [Settings Desktop Layout](#settings-desktop-layout)
  - [🍒 Conclusion](#-conclusion)

## 🎯 Project Goals

- Provide an **immutable** core: The base system cannot be altered from within once booted.
- Load **external configurations**, drivers, and software post-boot, isolating critical system components.
- Enable **file diff-based updates** for efficient system upgrades.
- Implement comprehensive **sandboxing** for all user applications, requiring explicit permissions for system calls.
- Offer a **POSIX-compliant** environment, ensuring compatibility with a wide range of Unix software and libraries.
- Support **multi-user** functionality, secure network and hardware integration, and modern application management.

## 📅 Development Stages

### 🛠️ Development

During the development phase, the foundational components of the operating system were built:

- Bootloader implementation with support for UEFI and legacy systems.
- Process **scheduler** supporting multi-threading and multi-tasking.
- Initial system services including basic **init** and **service management**.
- Creation of the primary filesystem structure, including `/bin`, `/system`, `/apps`, `/etc`, `/users`, `/dev`, `/mnt`, `/share`, and `/lib`.
- Driver support for essential hardware (CPU, memory, storage).

### 🚀 Release

In the release phase, the OS was optimized for general use:

- **Application sandboxing**: Every application runs in its own sandbox with fine-grained permission control.
- Extended hardware support for **peripherals**, including keyboard, mouse, and display.
- Full **networking stack** implementation (Ethernet, Wi-Fi, TCP/IP, etc.).
- Basic **window management** system for graphical user interfaces.
- External configuration loading, allowing dynamic system behavior without modifying the core OS.

### 🔐 Security Enhancement

Security was the focus in the final phase:

- **System integrity checks**: Each system boot involves verifying the integrity of critical files.
- **Application sandboxing** with permissions requests for sensitive operations (e.g., network access, file I/O).
- **File encryption** support for sensitive directories.
- Full support for **differential updates**, enabling minimal changes to the system during upgrades.
- Signed drivers and application verification for trusted execution.

## 📂 Directory Structure

SKC follows a standard Unix-like directory structure to organize system files and user data. The layout is designed to be intuitive and consistent with POSIX standards:

### 🍉 Root Directory

```bash
/
├── bin             # Essential system binaries
├── system          # Core system components (kernel, drivers, essential services)
|   ├── kernel      # Kernel files [Read Only] 
|   ├── drivers     # Internal pre-built device drivers.
|   ├── boot        # Bootloader and boot configuration
|   ├── init.d      # System initialization scripts
├── apps            # Installed applications (isolated and sandboxed)
├── etc             # System-wide configuration files
|   ├── cron.d      # Network configuration
|   ├── network.d   # Network configuration
|   ├── services.d  # System services configuration
|   ├── fstab       # Filesystem table
|   ├── groups      # Group information
|   ├── hosts       # Hostname resolution
|   ├── security    # Security configuration
|   ├── system      # System configuration
|   ├── users       # User management configuration
├── users           # User home directories
├── dev             # Device files representing hardware (e.g., block, character devices)
|   ├── sda         # Hard disk
|   ├── tty         # Console
|   ├── null        # Null device
|   ├── input       # Input devices
|   ├── audio       # Audio devices
|   ├── net         # Network devices
├── mnt             # Mounted filesystems and external storage
|   ├── usb         # USB storage
|   ├── cdrom       # CD/DVD drive
|   ├── nfs         # Network File System
|   ├── smb         # Samba shares
|   ├── drive       # External hard drive
├── lib             # Shared system libraries for system binaries and apps
|   ├── drivers     # User installed drivers.
|   ├── modules     # Kernel modules
|   ├── firmware    # Device firmware
├── share           # Shared system resources (logs, temp files, runtime data)
|   ├── log         # System logs
|   ├── tmp         # Temporary files, cleared on reboot
|   ├── cache       # Cached data (updates, downloads)
|   ├── lock        # Lock files to manage resource access
|   ├── proc        # Runtime process data and PID files
|   ├── fonts       # System fonts
|   ├── icons       # System icons
|   ├── themes      # System themes
|   ├── sys         # System information
```

### 🙇 User Home directory

```bash
/home/username/
├── Documents       # Store your documents here
├── Downloads       # Store your downloads here
├── Music           # Store your music files here
├── Pictures        # Store your pictures here
├── Videos          # Store your videos here
├── Desktop         # Store your desktop files here
├── .config         # For application specific configurations
|   ├── custom-app
|   └── terminal
├── .local          # For user specific data that should be hidden.
|   ├── apps        # A replacement for /apps
|   ├── bin         # A replacement for /bin
|   └── lib         # A replacement for /lib
|   └── logs        # A replacement for /share/log
|   └── tmp         # A replacement for /share/tmp
├── .cache          # For caching data
|   ├── application1
|   └── application2
├── .ssh            # For SSH keys
|   ├── id_rsa
|   ├── id_rsa.pub
|  └── known_hosts
├── .themes         # For custom themes for the system
|   └── custom-theme
└── .private        # This directory is always encrypted by the user password.
    ├── passwords.txt
    └── encryption_keys
```

## 🔩 System Settings

System configuration files would mostly be in .toml format, with legacy formats also being retained for backward compatibility. Here are some examples of configuration schemas/models:

- **Cron jobs:** Configuration for scheduled tasks. Each job has a name, schedule, and command to execute. [/etc/cron.d/(file).toml](etc/cron.d/backup.toml)
- **Network settings:** Configuration for network interfaces, IP addresses, and DNS servers. [/etc/network.d/network.toml](etc/network.d/network.toml)
- **Service management:** Configuration for system services, including startup order, dependencies, and status. [/etc/services.d/service.toml](etc/services.d/service.toml)
- **Fstab:** Filesystem table configuration for mounting drives and partitions. [/etc/fstab.toml](etc/fstab.toml)
- **Groups:** Group information, including group name, GID, and group members. [/etc/groups.toml](etc/groups.toml)
- **Hosts:** Hostname resolution configuration for local network mapping. [/etc/hosts](etc/hosts)
- **Security settings:** System-wide security configuration, including firewall rules, encryption settings, and user permissions. [/etc/security.toml](etc/security.toml)
- **System configuration:** General system settings, including timezone, language, and system-wide preferences. [/etc/system.toml](etc/system.toml)
- **User management:** User account configuration, including username, UID, home directory, and group membership. [/etc/users.toml](etc/users.toml)

## 📂 Filesystems Supported

SKC supports a variety of filesystems to cater to different use cases and requirements:

- **ZFS**: A highly resilient filesystem with built-in features like snapshots, data integrity checks, and compression. Ideal for large-scale storage.
- **Btrfs**: Offers advanced filesystem features such as subvolumes, snapshots, and data deduplication. Suitable for both consumer and enterprise use.
- **EXT4**: A reliable and well-tested filesystem used widely in Linux systems, offering a balance between performance and reliability.
- **FAT32**: Standard support for cross-platform external storage devices, ensuring compatibility with older systems and removable media.
- **NTFS**: Full read/write support for Microsoft Windows-formatted storage devices, allowing easy sharing of data between platforms.
- **XFS**: High-performance filesystem suitable for large-scale data processing.
- **TMPFS**: For storing temporary files in memory, enhancing speed for cache-heavy applications.

## 🚗 Drivers

### 📦 Storage Drivers

- **SATA (Serial ATA):**
  - Standard: SATA 3.0 (up to 6 Gbps data transfer rate).
  - AHCI (Advanced Host Controller Interface) for efficient access to storage devices.
  - TRIM command support for SSDs to improve lifespan and performance.
- **NVMe (Non-Volatile Memory Express):**
  - Standard: NVMe 1.3 and later, optimizing SSD performance via PCI Express interface.
  - Direct I/O parallelism and multi-queue architecture for high-performance data processing.
- **RAID (Redundant Array of Independent Disks):**
  - Standards: RAID 0, 1, 5, 6, 10 with full support for hardware and software RAID configurations.
  - Protocols: SAS (Serial Attached SCSI) for enterprise-grade RAID arrays.
- **USB Mass Storage:**
  - Protocols: USB Mass Storage Class (MSC).
  - Supports both USB 2.0 and USB 3.0/3.1 for connecting external drives (HDDs, SSDs, flash drives).

### 🎮 Graphics Drivers

- **GPU Support:**
  - **NVIDIA:** Full support for NVIDIA Proprietary Driver and open-source Nouveau drivers.
  - **AMD:** AMDGPU and Radeon drivers for open-source and proprietary support.
  - **Intel:** Support for integrated GPUs with i915 driver, compatible with modern Intel graphics.
- **Display Standards:**
  - **VESA** (Video Electronics Standards Association) compliant, ensuring compatibility with a wide range of displays.
  - DisplayPort 1.4, HDMI 2.1, and DVI-D support for high-resolution monitors (4K, 8K displays).
- **Rendering and APIs:**
  - OpenGL 4.6, Vulkan 1.2 for advanced 3D rendering in games and professional applications.
  - DRM (Direct Rendering Manager) for efficient GPU rendering.

### 🔊 Audio Drivers

- **ALSA (Advanced Linux Sound Architecture):**
  - Provides low-level interface for sound card devices, adhering to IEC 60958 (digital audio formats, SPDIF).
  - HDA (High Definition Audio) specification for modern integrated audio chipsets from Intel, Realtek, etc.
- **PulseAudio:**
  - Standard sound server for mixing and routing audio streams between applications.
  - Full support for HDA and AC'97 audio codecs.
- **PipeWire:**
  - Media server for handling both audio and video streams, replacing PulseAudio in certain configurations.
  - Adheres to standards like ALSA for audio and V4L2 for video handling.
- **Bluetooth Audio:**
  - A2DP (Advanced Audio Distribution Profile) support for wireless audio over Bluetooth.
  - HFP (Hands-Free Profile) for Bluetooth headsets, supporting wideband speech audio.

### 🌐 Network Drivers

- **Ethernet:**
  - Gigabit Ethernet (IEEE 802.3ab) and 10 Gigabit Ethernet (IEEE 802.3an) support.
  - SR-IOV (Single Root I/O Virtualization) for network virtualization in data centers.
  - IPv6: Full support for the modern Internet Protocol, in compliance with RFC 8200.
- **Wi-Fi:**
  - Standards: 802.11ac, 802.11ax (Wi-Fi 6), with backward compatibility to 802.11a/b/g/n.
  - Security Protocols: WPA3, WPA2-Enterprise (IEEE 802.1X authentication).
  - Chipset Support: Intel, Qualcomm Atheros, Broadcom, Realtek.
- **Bluetooth:**
  - Bluetooth 5.0 support for both Low-Energy (BLE) and high-speed data transmission.
  - Protocols: L2CAP, GATT (Generic Attribute Profile) for BLE communication.
  - Supports HID (Human Interface Device) profile for wireless keyboards, mice, and controllers.
- **VPN:**
  - Protocols: OpenVPN, WireGuard for secure network tunneling.
  - IPsec support for enterprise-grade VPN connections (RFC 4301).

### ⌨ Input / Peripheral Drivers

- **USB HID (Human Interface Device):**
  - Protocol: USB HID 1.11 for input devices like keyboards, mice, and touchpads.
  - PS/2 support for legacy devices like older keyboards and mice.
- **Touchscreen and Touchpads:**
  - Multi-touch gestures support via libinput.
  - Compliance with Windows Precision Touchpad standards for advanced gesture recognition.
- **Game Controllers:**
  - XInput and DirectInput drivers for compatibility with Xbox and PlayStation controllers.

### 💽 Peripheral and Expansion Support

- **PCI/PCIe:**
  - Full support for PCI Express 4.0 and backward compatibility with PCIe 3.0, 2.0, and PCI legacy.
  - SR-IOV: PCIe device virtualization for use in cloud environments.
- **Serial Devices:**
  - Standard RS-232 and RS-485 support for industrial devices and legacy hardware.
- **Printer and Scanners:**
  - CUPS (Common Unix Printing System) for managing local and networked printers (compliant with IPP - Internet Printing Protocol).
  - SANE (Scanner Access Now Easy) for scanner device compatibility.

### 📸 Multimedia Drivers

- **Webcams and Cameras:**
  - UVC (USB Video Class) compliant for webcams.
  - V4L2 (Video4Linux) framework for video capture devices, compliant with ITU-T H.264 for video compression.
- **Capture Cards:**
  - Support for HDMI and SDI capture devices, compliant with HDCP (High-bandwidth Digital Content Protection) standards for protected content.

### 🔋 Power Management

- **ACPI (Advanced Configuration and Power Interface):**
  - ACPI 6.0 for power management and device configuration.
  - Provides support for modern CPU power states, sleep (S3), hibernation (S4), and thermal management.
- **CPU Frequency Scaling:**
  - Intel P-State driver for dynamic power management on Intel processors.
  - AMD Cool'n'Quiet and AMD PowerNow! support for AMD processors.

## 🌐 Protocols and Standards Compliance

- **Networking:**
  - TCP/IP stack, compliant with IPv4 (RFC 791) and IPv6 (RFC 8200).
  - DHCP (Dynamic Host Configuration Protocol) for IP address assignment (RFC 2131).
  - NFS (Network File System) for shared storage (RFC 7530).
- **Peripheral Communication:**
  - USB protocol compliance (USB 2.0, 3.0, 3.1, USB-C), per the USB-IF specifications.
  - I2C, SPI, and UART for internal device communication, essential for embedded systems and IoT devices.
- **Security:**
  - Full compliance with FIPS 140-2 (Cryptographic Module Security) standards for secure cryptographic operations.
  - TLS 1.3 for secure network communication (RFC 8446).
  - UEFI Secure Boot (compliant with UEFI 2.6) for ensuring system integrity at boot time.
- **POSIX-compliant**: Full compliance with POSIX standards, ensuring compatibility with a wide range of Unix-based software and tools.
- **FHS (Filesystem Hierarchy Standard)**: SKC follows the FHS for organizing files and directories, providing consistency across Unix-like systems.
- **ELF binary format**: The system supports Executable and Linkable Format (ELF) binaries, making it easy to compile and run Unix applications.

## 📚 System Libraries

SKC includes a wide range of system libraries to support various programming languages, frameworks, and applications. These libraries provide essential functionality for system operations, multimedia processing, networking, and more:

### Core System Libraries

- **libc**: Standard C library for system calls and low-level functions.
- **libm**: Math library for mathematical operations.
- **libpthread**: POSIX threads library for multi-threading.
- **libdl**: Dynamic Linking library for loading shared objects at runtime.
- **librt**: Real-time library for time-sensitive operations.
- **libcrypt**: Cryptography library for secure data handling.

### Graphics and UI

- **libGL**: OpenGL library for 3D rendering.
- **libGLES**: OpenGL ES library for embedded systems.
- (A native library for window management and compositing with hardware acceleration support, replacement for Qt and GTK).

### Audio and Media

- **libasound**: ALSA library for low-level audio control.
- **libpulse**: PulseAudio library for high-level audio management.
- **libav**: FFmpeg library for audio and video decoding.
- **libdrm**: Direct Rendering Manager library for graphics rendering.
- **GStreamer**: Multimedia framework for audio and video processing.

### Networking

- **libcurl**: cURL library for URL transfers.
- **libssl**: OpenSSL library for secure network connections.
- **libpcap**: Packet Capture library for network monitoring.
- **libnss**: Name Service Switch library for resolving hostnames.
- **libgssapi**: Generic Security Services API library for secure communication.
- **libldap**: LDAP library for directory services.
- **libnfs**: NFS library for network file sharing.

### Additional Libraries

- **libxml**: XML library for parsing and manipulating XML data.
- **libjson**: JSON library for parsing and generating JSON data.
- **libz**: Zlib library for data compression.
- **libfreetype**: Freetype library for rendering fonts.

## 🎨 Desktop Environment

SKC includes a sleek and modern desktop environment with the following features:

- **Multi-Desktop support:** Users can create multiple desktops for different tasks.
- **Window Manager:**
  - **Tiling and floating windows:** Users can choose between tiling and floating window layouts.
  - **Gestures and shortcuts:** Support for touchpad gestures and keyboard shortcuts.
  - **Task switching:** Easy switching between open applications.
  - **Dynamic workspaces:** Automatically create new workspaces as needed.
- **Customization:**
  - **Themes and icons:** Users can customize the look and feel of the desktop.
  - **Applets and widgets:** Add applets and widgets to the desktop for quick access to information.
  - **Hot corners:** Assign actions to hot corners for quick access to common tasks.
  - **Lock screen:** Secure the desktop with a lock screen.
  - **Screen savers:** Display screen savers when the desktop is idle.
  - **Wallpaper:** Set custom wallpapers for the desktop.
  - **Screenshots:** Take screenshots of the desktop or specific windows.
- **Utilities:**
  - **Notification center:** A centralized location for notifications from applications.
  - **System tray:** Display system and application icons in the system tray.
  - **App launcher:** Quickly launch applications from a searchable list.

While the desktop environment is not part of the kernel, it must be possible to create and run a graphical environment that meets all of these requirements. The kernel must be able to provide all of the necessary services and APIs to achieve this goal.

## 🔐 Security Architecture

SKC emphasizes security at every layer, offering robust mechanisms to protect system integrity and user privacy:

### Core Security Features

- **Immutability**: The core system cannot be modified once booted, ensuring that critical system files remain untouched.
- **Application Sandboxing**: Each application is sandboxed and cannot access sensitive resources or perform privileged operations without explicit permissions.
- **File Integrity Verification**: On every boot, system files are cryptographically verified to prevent unauthorized modifications.
- **Differential Updates**: System updates are distributed as file-diff patches to minimize downtime and reduce the risk of corrupting system files.
- **Signed Drivers and Applications**: All drivers and applications are digitally signed, ensuring that only trusted software is allowed to execute.

### Encryption and Security Tools

- **Disk Encryption**: Full-disk encryption support (LUKS) for sensitive partitions, ensuring data protection even in case of physical theft.
- **Secure Boot**: Ensures that the system only boots with trusted firmware, preventing unauthorized software from being executed during startup.
- **User and Group Permissions**: Fine-grained user and group-based permission systems ensure that sensitive resources are restricted to authorized users.
- **Mandatory Access Control (MAC)**: Systems like **AppArmor** and **SELinux** can be used to further restrict system calls and resource access by applications.
- **Firewall**: A built-in firewall to control network traffic and prevent unauthorized access to the system.

### System Updates and Maintenance

- **File-Diff Patches**: Updates are delivered as small differential patches to minimize download sizes and apply changes quickly.
- **Automatic Rollbacks**: If an update fails or causes instability, the system can automatically roll back to the previous version, ensuring reliability.
- **Versioned Snapshots**: SKC creates system snapshots before every major update, providing an easy recovery point in case of errors.

## ☕ Essentials Binaries

SKC includes a set of essential binaries that are required for system operation and maintenance:

- **File system:** `ls`, `cd`, `pwd`, `mkdir`, `rmdir`, `cp`, `mv`, `rm`, `touch`, `cat`, `more`, `less`, `head`, `tail`, `ln`, `find`, `grep`, `awk`, `sed`, `sort`, `uniq`, `wc`, `diff`, `tar`, `zip`, `unzip`.
- **Process management:** `ps`, `top`, `kill`, `pkill`, `pgrep`, `nice`, `renice`, `jobs`, `bg`, `fg`, `nohup`.
- **User management:** `useradd`, `userdel`, `usermod`, `passwd`, `groupadd`, `groupdel`, `groupmod`, `chown`, `chgrp`, `su`, `sudo`.
- **Network utilities:** `ping`, `traceroute`, `netstat`, `ifconfig`, `route`, `ss`, `nc`, `telnet`, `ssh`, `scp`, `rsync`, `ftp`, `curl`, `wget`.

Those binaries are essential for system administration, troubleshooting, and day-to-day operations. They should be accessible from `/bin` or `/home/{user}/.local/bin` directories.

## 📥 Pre-installed Developer Tools

This project must provide developers with essential tools and environments to start building applications out of the box:

- **GCC**: The GNU Compiler Collection, pre-configured for compiling C, C++, and other supported languages.
- **Clang**: A fast and modern alternative to GCC with better diagnostics and static analysis tools.
- **Make**: Build automation tool for managing project builds.
- **CMake**: Cross-platform, open-source build system for easier management of complex builds.
- **Python**: Pre-installed Python 3.x with pip, for scripting, automation, and rapid development.
- **Node.js**: A powerful runtime for building scalable network applications using JavaScript.
- **Git**: Version control system for managing source code and collaboration.
- **Docker**: Containerization platform for isolating applications and their dependencies.
- **Vim**, **Nano**, and **Visual Studio Code**: Command-line and graphical text editors for coding and configuration.

All of those tools should run seamlessly on the SKC, enabling developers to create, test, and deploy applications without additional setup.

## 🛠️ Pre-installed Applications

To verify that the kernel is functional, the following pre-installed applications should be able to run (But they should not be included in the distribution)

- **File Manager:** A simple file manager to navigate the filesystem.
- **Archive Manager:** An application to create and extract compressed archives.
- **Terminal Emulator:** A basic terminal emulator to run shell commands.
- **Text Editor:** A text editor for creating and editing files.
- **Media Player:** A media player for audio and video playback.
- **System Monitor:** A system monitor to view CPU, memory, and disk usage.
- **Email Client:** A basic email client for sending and receiving emails.
- **Screenshot Tool:** A tool to capture screenshots of the desktop.
- **Voice Recorder:** An application to record audio from the microphone.
- **Calculator:** A simple calculator for basic arithmetic operations.
- **Camera:** An application to view the camera feed from a webcam and take pictures.
- **System Settings:** A control panel to configure system settings and preferences.
- **Calendar:** A calendar application to manage events and appointments.
- **Print Manager:** An application to manage printing tasks and printers.
- **Package Manager:** A package manager to install, update, and remove software packages.
- **Disk Cleaner:** An application to clean up temporary files and free up disk space.
- **Notes:** A note-taking application to jot down quick notes and reminders.

## 🌱 APIs

There are several APIs that should be available to developers to create applications that interact with the system:

### Window creation and management

The API allows developers to create and manage multiple windows for an application, handling features such as resizing, minimization, and maximization. It also supports child and modal windows.

#### Basic Window Initialization

```cpp
Window* window = Window::create("My Application", 800, 600, WindowFlags::Resizable | WindowFlags::Centered);
window->show();
```

#### Window Flags

Flags control window behavior and appearance:

- `WindowFlags::Resizable`: Allows the window to be resized by the user.
- `WindowFlags::Fullscreen`: Opens the window in fullscreen mode.
- `WindowFlags::Maximized`: Opens the window maximized.
- `WindowFlags::Minimized`: Opens the window minimized.
- `WindowFlags::Centered`: Centers the window on the screen.
- `WindowFlags::Modal`: Opens the window as a modal dialog.
- `WindowFlags::Borderless`: Removes the window border and title bar.
- `WindowFlags::AlwaysOnTop`: Keeps the window on top of other windows.
- `WindowFlags::Transparent`: Makes the window background transparent.

#### Window Methods

- `window->resize(width, height)`: Resizes the window to the specified dimensions.
- `window->move(x, y)`: Moves the window to the specified position.
- `window->setTitle(title)`: Sets the window title.
- `window->minimize()`: Minimizes the window.
- `window->maximize()`: Maximizes the window.
- `window->restore()`: Restores the window to its previous state.
- `window->close()`: Closes the window.

### Window Rendering and Drawing

SKC uses a vector-based rendering engine that supports hardware acceleration, making it ideal for rendering 2D graphics, UIs, and animations.

#### Rendering Context

A rendering context is automatically created with each window. You can draw directly onto the window or use layers and compositing techniques.

```cpp
Renderer* renderer = window->getRenderer();
renderer->clear(Color::White);
renderer->drawRectangle(100, 100, 200, 200, Color::Red);
renderer->present();
```

#### Drawing Primitives

- `drawRectangle(x, y, width, height, color)`: Draws a filled rectangle.
- `drawCircle(x, y, radius, color)`: Draws a filled circle.
- `drawLine(x1, y1, x2, y2, color)`: Draws a line.
- `drawText(text, font, x, y, color)`: Draws text using a specified font.
- `drawImage(image, x, y)`: Draws an image at the specified position.
- `drawPolygon(points, color)`: Draws a filled polygon.

#### Image Support

You can load and display images in various formats (PNG, JPEG, BMP, etc.).

```cpp
Image* image = Image::loadFromFile("icon.png");
renderer->drawImage(image, 50, 50);
```

### Widget System

The API provides a robust widget system that includes pre-built components for common UI elements. Widgets can be customized or extended to create new components.

#### Button Example

```cpp
Button* button = new Button(window, "Click Me");
button->setPosition(50, 50);
button->onClick([](){
    std::cout << "Button clicked!" << std::endl;
});
```

#### Other available widgets

- `Label`: Displays text.
- `TextBox`: Allows text input.
- `CheckBox`: A checkable box.
- `RadioButton`: A radio button.
- `Slider`: A draggable slider.
- `ProgressBar`: Displays progress.
- `ComboBox`: A drop-down list.
- `Menu`: A menu bar or context menu.
- `TabBar`: A tabbed interface.
- `Dialog`: A modal dialog box.
- `Canvas`: A drawing canvas.

#### Custom Widgets

You can extend base widget classes to create custom UI elements:

```cpp
class CustomWidget : public Widget {
    void draw(Renderer* renderer) override {
        // Custom drawing logic
    }
};
```

### Window Event Handling

The API provides a unified system for handling user input events, including mouse, keyboard, and touch events.

#### Mouse Events

```cpp
window->onMouseClick([](int button, int x, int y) {
    std::cout << "Mouse clicked at " << x << ", " << y << std::endl;
});
```

#### Keyboard Events

```cpp
window->onKeyPress([](int key) {
    if (key == Key::Escape) {
        window->close();
    }
});
```

#### Touch and Gesture support

```cpp
window->onSwipe([](int direction) {
    std::cout << "Swipe detected: " << direction << std::endl;
});
```

### Layout Management

The API includes a flexible layout management system, allowing for dynamic, responsive UIs.

#### Grid Layout

```cpp
GridLayout* layout = new GridLayout(window, 3, 2);
layout->addWidget(new Button(window, "Button 1"), 0, 0);
layout->addWidget(new Label(window, "Label"), 1, 1);
```

#### Stack LAyout

Widgets can be layered on top of one another, useful for modals or overlays:

```cpp
StackLayout* layout = new StackLayout(window);
layout->addWidget(new Image(window, "background.jpg"));
layout->addWidget(new Button(window, "Start Game"));
```

### Compositing and Transparency

The windowing API supports compositing, allowing windows and widgets to be layered with transparency effects.

```cpp
window->setOpacity(0.8f); // Set window opacity to 80%
```

### Multi-Screen and High-DPI Support

The API fully supports multiple screens and high-DPI displays, automatically scaling content for crisp, clear rendering.

#### Multi-Screen Handling

```cpp
Screen* primaryScreen = Screen::getPrimary();
std::vector<Screen*> screens = Screen::getAllScreens();
for (Screen* screen : screens) {
    std::cout << "Screen: " << screen->getResolution() << std::endl;
}
```

### Accessibility Features

The API has built-in accessibility support, including screen readers, high-contrast modes, and keyboard navigation.

#### Screen Reader Integration

Text-based widgets can automatically provide content for screen readers:

```cpp
Label* label = new Label(window, "This is accessible text.");
label->setAccessible(true);
```

#### Keyboard Navigation

Widgets can be navigated using keyboard controls, with support for focus management:

```cpp
button->setFocusable(true);
```

### Desktop Widgets

Widgets are rendered in the background, often behind desktop icons, but can be set to be interactive.

#### Simple Desktop Widget

```cpp
DesktopWidget* desktopWidget = new DesktopWidget("ClockWidget");
desktopWidget->setPosition(100, 100);  // Position on the desktop
desktopWidget->setSize(150, 150);      // Size of the widget
desktopWidget->setBackgroundColor(Color::Transparent);
desktopWidget->show();
```

#### Rendering Contents in Widgets

Widgets use the same rendering context as windows but are often simpler:

```cpp
desktopWidget->onRender([](Renderer* renderer) {
    renderer->clear(Color::Transparent);
    renderer->drawText("12:00", 10, 10, Font::Default, Color::White);
});
```

#### Updating Widget Content

Widgets can dynamically update their content:

```cpp
desktopWidget->onUpdate([]() {
    std::string currentTime = getCurrentSystemTime();  // Custom function
    desktopWidget->updateText(currentTime);
});
```

### Taskbar Widgets (Modular Islands)

Taskbar widgets are part of the floating islands concept, allowing users to dock widgets to a taskbar-like interface. These islands are modular and can be moved or resized.

#### Creating a Taskbar Widget

```cpp
TaskbarWidget* taskbarWidget = Taskbar::createWidget("WeatherWidget");
taskbarWidget->setSize(200, 50);  // Example: Weather info widget
taskbarWidget->show();
```

#### Interaction in Taskbar Widgets

Taskbar widgets support user interaction, such as clicks or hover states:

```cpp
taskbarWidget->onClick([](){
    // Show detailed weather info when clicked
});
```

#### Dynamic Island Configuration

Islands can be added, removed, or reconfigured at runtime:

```cpp
Taskbar::addIsland("WeatherWidget", 0);  // Add a new widget to the taskbar
Taskbar::removeIsland("ClockWidget");    // Remove an existing widget
Taskbar::moveIsland("WeatherWidget", 1); // Move a widget to a different position
```

Islands can house multiple widgets and can be detached or rearranged by the user.

### System Notifications

System tray notifications provide a way to deliver important updates to the user without interrupting their workflow. Notifications appear as small pop-ups in the system tray area and can be interactive.

#### Simple Notification

System notifications are lightweight, usually showing text, icons, or progress bars.

```cpp
Notification* notification = new Notification("Update Available", "A new system update is ready to install.");
notification->setIcon("update_icon.png");  // Optional icon
notification->setTimeout(5000);  // Auto-hide after 5 seconds
notification->show();
```

#### Interactive Notifications

Notifications can include buttons or allow user interaction:

```cpp
notification->addButton("Install Now", []() {
    startUpdateProcess();  // Custom action for installing the update
});
```

#### Notification Categories and Priority

Notifications can be categorized and prioritized based on urgency:

```cpp
// Categorize as a system notification
notification->setCategory(NotificationCategory::System);

// Set high priority for urgent notifications
notification->setPriority(NotificationPriority::High);
```

### System Tray

The system tray provides a centralized location for system and application icons, allowing users to access important information and controls.

#### Adding Icons to the System Tray

```cpp
SystemTray* systemTray = new SystemTray();
systemTray->setIcon("app_icon.png");
systemTray->setTooltip("My Application");
systemTray->show();
```

#### System Tray Menu

System tray icons can have context menus for additional functionality:

```cpp
systemTray->addMenuItem("Open", []() {
    openApplicationWindow();
});
```

### Pop-up Dialogs

Pop-up windows and dialogs are modal or non-modal UI elements that capture user attention for interactions such as file selection, prompts, or system alerts.

#### Open File Dialog

Open file dialogs allow users to browse the filesystem and select files.

```cpp
FileDialog* fileDialog = new FileDialog(FileDialog::Open);
fileDialog->setTitle("Select a file to open");
fileDialog->setFilters({".txt", ".pdf", ".png"});
fileDialog->onFileSelected([](const std::string& filepath) {
    std::cout << "File selected: " << filepath << std::endl;
});
fileDialog->show();
```

#### Prompt Dialog

Prompt dialogs are used to request input from the user, such as entering a password or confirming an action.

```cpp
PromptDialog* prompt = new PromptDialog("Enter your password:");
prompt->setPasswordMode(true);  // Masks input for privacy
prompt->onSubmit([](const std::string& input) {
    std::cout << "Password entered: " << input << std::endl;
});
prompt->show();
```

#### Splash Screens

Splash screens are temporary, non-interactive windows that are typically displayed when an application starts.

```cpp
SplashScreen* splash = new SplashScreen("MyAppLogo.png");
splash->setTimeout(3000);  // Display for 3 seconds
splash->show();
```

### Access to the Desktop

The OS supports both static and animated wallpapers, allowing users to apply different formats, including PNG, JPEG, MP4, and GIF. Animated wallpapers can seamlessly loop or stop after playback.

#### Setting a Static Wallpaper

```cpp
Desktop::setWallpaper("background.jpg");
```

#### Settings Desktop Layout

The desktop layout can be customized with icons, widgets, and other elements:

```cpp
Desktop::setIconSpacing(10);  // Set spacing between icons
Desktop::moveIcon("MyApp", 100, 100);  // Move an icon to a specific position
```

## 🍒 Conclusion

The SKC is designed to provide a secure, reliable, and user-friendly computing environment. By focusing on security, performance, and ease of use, the OS aims to meet the needs of both individual users and enterprise customers. With a robust set of features, APIs, and applications, the OS offers a complete solution for modern computing needs. The project is open-source, allowing for community contributions and customization to suit specific requirements. By following industry standards and best practices, the SKC aims to be a trusted platform for a wide range of users and applications.
