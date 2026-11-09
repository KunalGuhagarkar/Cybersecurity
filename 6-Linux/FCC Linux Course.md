
YouTube:
https://www.youtube.com/watch?v=sWbUDq4S6Y8

Course:
https://training.linuxfoundation.org/training/introduction-to-linux/


## Major Covering Linux Distributions (Distros)

### 1. Red Hat Family Systems

#### 1. Fedora

#### 2. CentOS

### 2. SUSE Family System

#### 1. OpenSUSE

### 3. Debian Family Systems

#### 1. Ubuntu

#### 2. Linux Mint

---

# Red Hat Family 

## Red Hat Enterprise Linux (RHEL) 

Red Hat Enterprise Linux (RHEL) heads the family that includes CentOS, CentOS Stream, and Fedora

Some of the key facts about the Red Hat distribution family are:

- Fedora serves as an upstream testing platform for RHEL.

- CentOS is a close clone of RHEL; in fact, CentOS has been part of Red Hat since 2014.

- It supports multiple hardware platforms.

- It uses dnf, the RPM-based package manager (covered in detail later) to install, update, and remove packages in the system.

- RHEL is widely used by enterprises that host their own systems.

![[Pasted image 20261030104642.png]]


# SUSE Family

The relationship between SUSE  (SUSE Linux Enterprise Server, or SLES) and openSUSE LEAP is similar to the one described between RHEL, CentOS, and Fedora.

We use openSUSE LEAP as the reference distribution for the SUSE family, as it is available to end users at no cost. Because the two products are highly similar, the material that covers openSUSE LEAP can typically be applied to SLES with few problems.

Some of the key facts about the SUSE family are listed below:

- SUSE Linux Enterprise Server (SLES) is upstream for openSUSE LEAP.

- It uses the RPM-based zypper package manager (we cover it in detail later) to install, update, and remove packages in the system.

- It includes the YaST (Yet Another Setup Tool) application for system administration purposes.

- SLES is widely used in retail and many other sectors.


![[Pasted image 20261030105108.png]]


# Debian Family

The Debian distribution is upstream for several other distributions, including Ubuntu. In turn, Ubuntu is upstream for Linux Mint and several other distributions. It is commonly used on both servers and desktop computers. Debian is a pure open source community project (not owned by any corporation) and has a strong focus on stability.

Debian provides by far the largest and most complete software repository to its users of any Linux distribution.

Ubuntu aims to provide a good balance between long-term stability and ease of use. Since Ubuntu gets most of its packages from Debian’s stable branch, it also has access to a large software repository. For those reasons, we will use Ubuntu LTS (Long-Term Support) as the reference for Debian-family distributions in this course.

Some key facts about the Debian family are listed below:

- The Debian family is upstream for Ubuntu, and Ubuntu is upstream for Linux Mint and others.
    
- It uses the DPKG-based APT package manager (using apt, apt-get, apt-cache, etc., which we cover in detail later) to install, update, and remove packages in the system.
    
- Ubuntu has been widely used for cloud deployments.
    
- While Ubuntu is built on top of Debian and is GNOME-based under the hood, it differs visually from the interface on standard Debian, as well as other distributions.

![[Pasted image 20261030112818.png]]


---

## Linux Terminology

Refer the Terminology Folder

---

## Linux Basics and System Startup

![[Pasted image 20261030123218.png]]


### BIOS (Basic Input/Output System)

When you power on the computer, the Basic Input/Output System (BIOS) begins the startup process.

![[Pasted image 20261030123330.png]]

**BIOS (Basic Input/Output System)** is a small program stored on a read-only memory (ROM) chip on a computer’s motherboard. It is the first software that runs when you power on your computer, even before the operating system is involved.

The BIOS performs a series of checks and initializations known as the **Power-On Self-Test (POST)**.

During POST, the BIOS initializes critical hardware components such as the screen, keyboard, and memory, ensuring that everything is functioning correctly before the operating system loads. 

The BIOS also finds and loads the bootloader, which then starts the operating system.


Once the BIOS finishes its checks, it hands control over to the next stage of the boot process, which is managed by the operating system.

**In short, the BIOS acts as a bridge between the computer’s hardware and its operating system, ensuring that everything is ready for the OS to take over.**


### Master Boot Record (MBR), EFI Partition, and Boot Loader

#### Boot Loader

A boot loader is a small program that loads the operating system's kernel into RAM after BIOS/UEFI completes hardware initialization.

Where is it stored?

- BIOS/MBR: In the MBR (Master Boot Record).

- UEFI: In the EFI System Partition (ESP).


Common boot loaders:

- GRUB: Used by most Linux distributions.

- ISOLINUX: Used for booting from CDs and USB drives.

- U-Boot: Used in embedded systems.


What does it do?

1. Provides a menu to select an operating system or kernel.

2. Loads the Linux kernel into RAM.

3. Loads initramfs, which contains essential drivers and files needed during startup.


#### BIOS vs UEFI

- BIOS: Loads boot code from the MBR.

- UEFI: Loads the boot loader from the EFI System Partition.


![[Pasted image 20261031104456.png]]

