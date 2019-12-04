# FAQ – Linux OS
Thanks to its minor share on desktop installations, Linux OS on desktop gets little attention from hackers – majority of Linux malware's targeted towards servers. Malware for desktops does exist, but in considerably lower numbers. As a result, while some Linux distributions are in horrendous condition from security perspective, the risk of infection's in practice lower than with different OSs. Yet, modern *exploit kits* are often multiplatform and their numbers are rising. Sufficient OS security is therefore essential.

This FAQ chapter's designed for everyday and intermediate users. Chapter for the advanced can be found [here](https://securityhandbook.cz/en/lnx/adv.php#lnx).

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

Inside Linux OS chapter, you'll mostly find tips for **Fedora** distribution.

**<span class="fe">Fedora</span>** is the best choice for everyday user as it's quite secure by default. It uses GNOME, offers simple Flatpak apps installation, contains a robust SELinux implementation and has high standards for its packages – all must be compiled with important memory corruption mitigations. Apart from technical features, the distribution provides stable up-to-date software. The only caveat are occasional slow web browser updates due to the large amount of distro-specific changes (patches), which must be updated with every new release.

At some places, you'll also find steps for the **<span class="os">openSUSE</span>** & **<span class="ub">Ubuntu</span>** distributions, of which the latter's very popular – but less suitable in terms of security.

Most of the information are valid for other distributions as well, the only difference's in syntax.

### Recommended graphical interface:
From the security perspective, [GNOME](https://www.gnome.org/) interface appears to be the most reasonable choice, as it uses Wayland instead of X.org and participates in Flatpak development. *GNOME Classic*'s an exception as it primarily uses X.org – therefore isn't recommended.

<br><br><hr><br>

## Elementary Security Configuration:
### Separating /tmp partition at installation and its secure mount:
Malware's often executed from temporary folders. As a result, disabling execution in temporary folders (namely /tmp) incapacitates whole families of malware.

> Guide

- ...


<br>

### Secure network configuration:

> DNS configuration

If you're not familiar with the word DNS, take a look at the following [short video](https://www.youtube.com/watch?v=HsQOWfc3Wic).

- Open your <span class="green">Settings</span>.
- Choose <span class="green">Wi-Fi</span> or <span class="green">Network</span> from the menu, depending on your connection type.
- Find the desired connection in the list and open its configuration.
<li style="list-style-type: none">![lnxnet](https://securityhandbook.cz/img/en/lnxnet.png)
![lnxnet1](https://securityhandbook.cz/img/en/lnxnet1.png)</li>
- Switch to the **IPv4** card and turn off <span class="green">Automatic</span> DNS in the **DNS** section.
- Input following DNS servers into the empty line:
<li style="list-style-type: none"><pre><code>193.17.47.1,185.43.135.1</code></pre></li>
<li style="list-style-type: none">![lnxnet2](https://securityhandbook.cz/img/en/lnxnet2.png)</li>
- For *IPv6* repeat the process using the following servers:
<li style="list-style-type: none"><pre><code>2001:148f:ffff::1,2001:148f:fffe::1</code></pre></li>
- Click <span class="green">Apply</span> and close the settings.

> Disabling IPv6

In case you don't need IPv6 (if unsure you can try this [test](https://test-ipv6.com/)), it's not a bad idea to disable the protocol for attack surface reduction.

- Open the <span class="green">Terminal</span>. Run the following commands:
<li style="list-style-type: none"><pre><code>sudo -i
dnf -y install nano
nano /etc/default/grub</code></pre></li>
- Find the line starting with <span class="green">GRUB_CMDLINE_LINUX_DEFAULT</span> and write "<span class="red"> ipv6.disable=1</span>" just before the last quote mark. The line will now look like this:
<li style="list-style-type: none"><pre><code>GRUB_CMDLINE_LINUX_DEFAULT="quiet splash ipv6.disable=1"</code></pre></li>
- Press <span class="green">Ctrl + X</span>. Save the changes by pressing <span class="red">Y</span> and then <span class="green">Enter</span>.
- You'll be returned to the console. Run the following commands:
<li style="list-style-type: none"><pre><code>grub2-mkconfig -o /boot/grub2/grub.cfg
exit
exit</code></pre></li>
- Reboot.

<br>

### Miscellaneous security configuration:
- Disable AutoPlay/AutoRun:
  - Open your <span class="green">Settings</span> and choose **Devices** from the menu.
  - Click on <span class="green">Removable Media</span>
  - Tick the <span class="green">Never prompt or start programs on media insertion</span> option.
  <li style="list-style-type: none">![lnxar](https://securityhandbook.cz/img/en/lnxar.png)</li>
- Disable sharing:
  - Open your <span class="green">Settings</span> and choose <span class="green">Sharing</span> from the menu.
  - Check the sharing's turned off and correct if necessary.
  <li style="list-style-type: none">![lnxshare](https://securityhandbook.cz/img/en/lnxshare.png)</li>

<br><br><hr><br>

## Malware Protection:
Configuration consisting of several layers (*&bdquo;layered config&ldquo;*) is considered the best means of protection against malware – should one layer fail, another comes into play. The OS itself provides a certain level of malware protection which varies across distributions. However, not all security features are usually enabled and/or properly configured by default.

<br>

### OS & SW Updates:
It's crucial to run the latest version of all SW as new releases often address security vulnerabilities. Outdated SW's implicitely insecure.

In **<span class="fe">Fedora</span>**, you can hypothetically leave updates to the **GNOME Software** app, or run them manually once in a while using a simple command:
<pre><code>sudo dnf update</code></pre>

The same applies to **<span class="os">openSUSE</span>**, with a slight modification of command syntax:
<pre><code>sudo zypper up</code></pre>

The same applies to **<span class="ub">Ubuntu</span>**, with a slight modification of command syntax:
<pre><code>sudo apt update && sudo apt upgrade</code></pre>

<br>

### Firewall:
Firewall's an essential OS security layer providing protection against network attacks. Its use on public WiFi connections is a must. *Side note: the basis of home network security's a solid router.*

**<span class="fe">Fedora</span>** integrates a fully functional firewall by default.

**<span class="os">openSUSE</span>** integrates a fully functional firewall by default.

**<span class="ub">Ubuntu</span>** integrates a firewall but disabled by default, can be turned on with the following command:
<pre><code>sudo ufw enable</code></pre>

<br>

### MAC:
<abbr title="Mandatory Access Control">MAC</abbr>'s become an important layer of Linux distributions' security model. For detailed explanation take a look at e.g. [Wikipedia – MAC](https://en.wikipedia.org/wiki/Mandatory_access_control).

**<span class="fe">Fedora</span>** implements **SELinux**.

**<span class="os">openSUSE</span>** implements **AppArmor**, a MAC offering lesser protection means than e.g. SELinux.

**<span class="ub">Ubuntu</span>** implements **AppArmor**, a MAC offering lesser protection means than e.g. SELinux.

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

<h3 class="nocol">That's all. Stay safe! <img class="smile" src="https://securityhandbook.cz/img/sm/smile.svg" alt="smile"></h3>
