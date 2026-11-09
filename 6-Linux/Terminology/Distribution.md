
## Collection of software making up a Linux-based OS

### Example: Red Hat Enterprise Linux, Fedora, Ubuntu and Gentoo

---
## Linux Distributions — Summary

### 1. What is a Linux distribution?

A Linux distribution (distro) is a complete operating system built around the Linux kernel.

- Linux kernel: The core of the operating system. It manages hardware, CPU, memory, and running programs.
    
- Other components: Libraries, utilities, applications, compilers, debuggers, and desktop environments.
    
- Distribution: Combines these components into an installable, maintainable operating system.
    

Examples include Ubuntu, Fedora, and Red Hat Enterprise Linux (RHEL).

### 2. What does a Linux distribution include?

|Component|Purpose|Examples|
|---|---|---|
|Kernel|Manages hardware and system resources|Linux kernel|
|Compilers|Convert source code into executable programs|GCC, Clang|
|Debuggers|Find and troubleshoot program errors|GDB|
|Libraries|Provide functions that applications use|System libraries|
|Desktop environments|Control the graphical interface|GNOME, KDE, Xfce|
|Package managers|Install, update, and remove software|APT, DNF, Zypper|

Each component may be developed by a different open-source project. The distribution integrates and tests these components to ensure they work together.

Important: Distributions can use different kernel versions. Some prioritize stability, while others adopt newer versions quickly. They may also backport newer improvements to older kernels without replacing the entire kernel version.

### 3. Major Linux distribution families

[Ubuntu 22.04 vs 24.04: What Has Changed?](https://images.openai.com/static-rsc-4/SSEnV7U0-ugoR4uEQmpokE7g6TT3tuAHIldUMOf8PCd1Hdr42hq1q1K6DiJriGsh0a18yI25q0IRe0OdgUrA34hUS-9LmOoa-IU6vtYsTpDsufbWuuporIFL35MqrIjQwDEtWIzUUEkKL66Y-DkAOF3-gKmb683bwraHAO5dEKI?purpose=inline)

Ubuntu

Maintained by Canonical. Popular among developers and educators because it is relatively easy to install, use, and maintain.

[RHEL, Red Hat Enterprise Linux | Piros](https://images.openai.com/static-rsc-4/EjVvGt3mJ4qjZ_lrzyGgIBMGV35FRC6XLF9_SmD_JC8iKHnIw1VoTOsgi5UzQiLbC6Y2ydH1wd0kGHyxS8COY1Oy5mDpGPgsibK-ZLBOOEW1XD9QYT1sq1DV67rsF6x8egnIwIEpvOrYMi2xabKB6F53vex_wsjYUNROPguFcm0?purpose=inline)

Red Hat Enterprise Linux (RHEL)

Maintained by Red Hat. Focuses on enterprise stability, security, and professional support.

[AWS Marketplace: SUSE Linux Enterprise Server for SAP Applications 15 SP5 Reviews](https://images.openai.com/static-rsc-4/-J5R5Cqf_gzJwi3A3A6LedUYKUz5uubsOkjhIINtPNIGLhkPtwiIGlOxqQ3bkADBl9gGUrW-kykJMQY_qJDz6nS4TbEAqTNRx-3lswCFPU_-10i6GkXMnN0Rfe4GjevV5r2LqEcN67qFIItOPSlvEMcMfVfe3dhSx4ihECBHNi8?purpose=inline)

SUSE Linux Enterprise (SLES)

Maintained by SUSE. Provides enterprise-focused Linux solutions and commercial support.

[File:Fedora icon (2021).svg - Wikimedia Commons](https://images.openai.com/static-rsc-4/n2bFh8w_l55uhGT7Q0vfpUfHk2OmwWDVqUxNi16g-RYXE_wRHfT596cIrrv0Ju88ZDTG-YMGn6V16WVktqHibTDwu2vvWmCi1zMP0c7i3wc5-qE18b035MplEsnT57iEto_ApFxnHBu9Kxoao93cPrbrnEMryLqbflUoMhv65sc?purpose=inline)

Fedora

A community distribution known for adopting newer software and technologies relatively quickly.

Other important distributions include:

- CentOS Stream: Tracks development just ahead of corresponding RHEL releases.
    
- Rocky Linux and AlmaLinux: Community-supported distributions designed to be compatible with RHEL.
    
- openSUSE: A community-supported distribution associated with the SUSE ecosystem.
    

### 4. Commercial vs. community support

|Commercial distributions|Community-supported distributions|
|---|---|
|RHEL|Fedora|
|SUSE Linux Enterprise|openSUSE|
|Ubuntu (commercial support available)|Rocky Linux|
||AlmaLinux|

Commercial support typically offers professional technical assistance, maintenance, and enterprise services. Community-supported distributions rely more heavily on community forums, documentation, and volunteer contributions.

Note that some distributions, including Ubuntu, offer both free usage and paid support options.

### 5. Why do Linux distributions matter to developers?

Different distributions can have different:

- Software versions and dependencies.
    
- Default configurations and system services.
    
- Package managers and installation procedures.
    
- Security updates and support lifecycles.
    

Therefore, developers should test their applications across relevant Linux distributions to ensure compatibility, reliability, and consistent performance.

## Key takeaways

1. The Linux kernel manages hardware and system resources.
    
2. A Linux distribution combines the kernel with the software needed for a complete operating system.
    
3. Distributions differ in software versions, package managers, stability, and support.
    
4. APT is associated with Debian-based distributions, DNF with Fedora/RHEL-based systems, and Zypper with SUSE-based systems.
    
5. Choose a distribution based on your needs: stability, newer technologies, ease of use, or professional support.
    
6. As a developer, test your software on the distributions your intended users are likely to use.