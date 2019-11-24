# FAQ – OS Linux
Thanks to its minor share on desktop installations, Linux OS enjoys little attention from hackers – majority of Linux malware is targeted towards servers. Malware for desktops does exist, but in significantly lower numbers. As a result, while some Linux distributions are in horrendous condition from security perspective, the risk of infection is in practice lower than with different OSs. Yet, modern *exploit kits* are often multiplatform and their numbers are rising. Sufficient OS security is therefore essential.

This FAQ chapter is designed for everyday and intermediate users. Chapter for the advanced can be found [here](https://faq.mople71.cz/en/lnx/adv.php#lnx).

#### FAQ is divided into several sections:
- [Recommended Distributions](#lnx1)
- [Elementary Security Configuration](#lnx2)
- [Malware Protection](#lnx3)
- [Web Browser Security](#lnx4)

<br>

## Recommended Distributions:
- **<span class="fe">Fedora</span>**: https://getfedora.org/en/workstation/
- **<span class="os">openSUSE</span>** (Leap): https://www.opensuse.org/#Leap
- **<span class="ub">Ubuntu</span>**: https://www.ubuntu.com/desktop

Inside Linux OS chapter, you'll mostly find tips for the **Fedora** distribution.

**<span class="fe">Fedora</span>** is the best choice for everyday user as it's quite secure by default. It uses GNOME, offers simple Flatpak apps installation, contains a robust SELinux implementation and has high standards for its packages – all must be compiled with important memory corruption mitigations. Apart from technical features the distribution provides stable up-to-date software. The only caveat are occasional slow web browser updates due to the large amount of distro-specific changes (patches) which must be updated with every new release.

At some places, you'll also find steps for the **<span class="os">openSUSE</span>** distribution and **<span class="ub">Ubuntu</span>** distribution, of which the latter is very popular but less suitable in terms of security.

Most of the information are valid for other distributions as well, the only difference's in syntax.

### Recommended graphical interface:
From the security perspective, the most reasonable choice is the [GNOME](https://www.gnome.org/) interface as it uses Wayland instead of X.org and participates in Flatpak development. *GNOME Classic* is an exception as it primarily uses X.org – therefore isn't recommended.

<br><br><hr><br>

## Elementary Security Configuration:
### Separating /tmp partition at installation and its secure mount:
Malware's often executed from temporary folders. As a result, disabling execution in temporary folders (namely /tmp) incapacitates many families of malware.

> Guide

- ...


<br>

### Secure network configuration:

> DNS configuration

...

> Disabling IPv6

...

<br>

### Miscellaneous security configuration:
- Disable AutoPlay/AutoRun:
  - ...
- Disable sharing:
  - ...

<br><br><hr><br>

## Malware Protection:
...

<br>

### OS & SW Updates:
...

<br>

### Firewall:
...

<br>

### MAC:
...

<br>

### Virtualization:
...

#### Flatpak:
...

<br>

#### Virtual machine:
...

<br><br><hr><br>

## Web Browser Security:
...

<!--- /browsers.md -->

<br><br><hr>

<h3 class="nocol">That's all. Stay safe! ![smile](https://mople71.cz/img/sm/smile.svg)</h3>
