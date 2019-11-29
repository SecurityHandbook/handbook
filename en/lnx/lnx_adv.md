# FAQ – OS Linux
Thanks to its minor share on desktop installations, Linux OS on desktop gets little attention from hackers – majority of Linux malware's targeted towards servers. Malware for desktops does exist, but in considerably lower numbers. As a result, while some Linux distributions are in horrendous condition from security perspective, the risk of infection's in practice lower than with different OSs. Yet, modern *exploit kits* are often multiplatform and their numbers are rising. Sufficient OS security is therefore essential.

This chapter focuses on advanced techniques of securing Linux (not only) desktop, taking the **Arch Linux** distro hostage, a distro which can be turned into a fairly secure installation with appropriate configuration. Steps described below can be applied on most distributions with proper modification of syntax.

It's expected you've read FAQ [OS Linux for less advanced](https://securityhandbook.cz/en/lnx/index.php#lnx) users and have at least the knowledge discussed there.

#### FAQ is divided into several sections:
- [Malware protection](#lnx1)
- [Measurements against exploitation](#lnx2)
- [Audit](#lnx3)

<br>

## Malware protection:
### Firewall:
Simply disabling FORWARD and properly configuring INPUT chains is sufficient for everyday users.

As for whitelisting outgoing communication (application FW), *nftables* isn't the most comfortable option. Implementing app FW through <abbr title="Mandatory Access Control">MAC</abbr> would be considerably easier.

> Ruleset example for an ordinary desktop

<pre><code>/etc/nftables.conf
-----------------------------------

table inet filter {
    chain input {
        type filter hook input priority 0; policy drop;
        ct state invalid drop
        ct state established,related accept
        iif "lo" accept
    }

    chain forward {
        type filter hook forward priority 0; policy drop;
    }

    chain output {
        type filter hook output priority 0; policy accept;
    }
}</code></pre>

<br>

### MAC:
<abbr title="Mandatory Access Control">MAC</abbr>'s become an important layer of Linux distributions' security model.

**SELinux** provides a robust MAC implementation, but the configuration can be tricky. It's used by e.g. **<span class="fe">Fedora</span>** and plays an important role in Android's security model.

**AppArmor** is a MAC implementation offering lesser protection means than (e.g. cannot restrict ioctls). It's used by e.g. **<span class="os">openSUSE</span>** or **<span class="ub">Ubuntu</span>**.

**TOMOYO Linux** is a solid MAC implementation offering better security capabilities than AppArmor and considerably simpler configuration than SELinux.

It's easy to use TOMOYO or AppArmor with Arch Linux, whilst TOMOYO doesn't require compiling custom kernel. Using SELinux isn't that simple.

> TOMOYO Linux installation

<div class="alert info"><p><em class="icon-info-circled"></em>**Info**<br>
TOMOYO Linux isn't a very widespread MAC and you'll have a hard time finding profiles for apps. As such, the only option's creating them yourself (or rewriting AppArmor profiles – those are everywhere). You will find the documentation [here](https://tomoyo.osdn.jp/2.6/index.html.en).</p></div>

- Enable TOMOYO Linux using GRUB:
<li style="list-style-type: none"><pre><code>/etc/default/grub
-----------------------------------

GRUB_CMDLINE_LINUX_DEFAULT="quiet security=tomoyo TOMOYO_trigger=/usr/lib/systemd/systemd"</code></pre></li>
- Update GRUB config (grub-mkconfig -o /boot/grub/grub.cfg).
- Install **tomoyo-tools**:
<li style="list-style-type: none"><pre><code>sudo pacman -S gnupg
gpg --recv-keys 43C83369623D7AD3A96C2FC7425F128D0C64F52A
git clone https://aur.archlinux.org/tomoyo-tools.git
cd tomoyo-tools
gedit PKGBUILD</code></pre></li>
- Check the file content and run the installation:
<li style="list-style-type: none"><pre><code>makepkg -si</code></pre></li>
- Reboot.

> Using TOMOYO Linux as an application FW

- After successful installation and reboot, initialize TOMOYO:
<li style="list-style-type: none"><pre><code>sudo /usr/lib/tomoyo/init_policy</code></pre></li>
- Edit TOMOYO policy:
<li style="list-style-type: none"><pre><code>/etc/tomoyo/policy/current/profile.conf
-----------------------------------

PROFILE_VERSION=20110903
0-COMMENT=-----Disabled Mode-----
0-PREFERENCE={ max_audit_log=1024 max_learning_entry=2048 }
0-CONFIG={ mode=disabled grant_log=no reject_log=yes }
0-CONFIG::network::unix_stream_bind={ mode=disabled grant_log=no reject_log=no }
0-CONFIG::network::unix_stream_listen={ mode=disabled grant_log=no reject_log=no }
0-CONFIG::network::unix_stream_connect={ mode=disabled grant_log=no reject_log=no }
0-CONFIG::network::unix_dgram_bind={ mode=disabled grant_log=no reject_log=no }
0-CONFIG::network::unix_dgram_send={ mode=disabled grant_log=no reject_log=no }
0-CONFIG::network::unix_seqpacket_bind={ mode=disabled grant_log=no reject_log=no }
0-CONFIG::network::unix_seqpacket_listen={ mode=disabled grant_log=no reject_log=no }
0-CONFIG::network::unix_seqpacket_connect={ mode=disabled grant_log=no reject_log=no }
0-CONFIG::network={ mode=enforcing grant_log=no reject_log=yes }
1-COMMENT=-----Disabled Mode (net access)-----
1-PREFERENCE={ max_audit_log=1024 max_learning_entry=2048 }
1-CONFIG={ mode=disabled grant_log=no reject_log=no }
2-COMMENT=-----Learning Mode-----
2-PREFERENCE={ max_audit_log=1024 max_learning_entry=2048 }
2-CONFIG={ mode=learning grant_log=no reject_log=yes }
3-COMMENT=-----Permissive Mode-----
3-PREFERENCE={ max_audit_log=1024 max_learning_entry=2048 }
3-CONFIG={ mode=permissive grant_log=no reject_log=yes }
4-COMMENT=-----Enforcing Mode-----
4-PREFERENCE={ max_audit_log=1024 max_learning_entry=2048 }
4-CONFIG={ mode=enforcing grant_log=no reject_log=yes }</code></pre></li>
- Reboot.
- Open TOMOYO policy config editor for applications:
<li style="list-style-type: none"><pre><code>sudo tomoyo-editpolicy</code></pre></li>

<div class="alert exclaim"><p><em class="icon-attention"></em>**Warning**<br>
TOMOYO only detects apps run at least once after being enabled.</p></div>

-  Use arrows to navigate between apps. Change selected app profile by pressing <span class="red">S</span>, inputing the profile number and hitting **Enter**.
<li style="list-style-type: none"><pre><code>0     #  no internet access
1     #  internet access
</code></pre></li>
- You'll exit the config editor via <span class="red">Q</span> key.
- Afer finishing the config, save and enforce it:
<li style="list-style-type: none"><pre><code>sudo tomoyo-savepolicy</code></pre></li>

<br><br><hr><br>

## Measurements against exploitation:
### Hardened allocator:
- https://github.com/grapheneos/hardened_malloc
- not working: man, on some installations **netfilter** or gnome-control-center,&#8230;

<br>

### App hardening:
Packages can be compiled with *memory corruption* mitigations (ASLR, PIE, RELRO, Canary,&#8230;) which makes them considerably harder to exploit later on.

For ASLR to work properly, all running processes need to be compiled as **PIE**. The combination then forms a rather solid mitigation – that is on the *64-bit* architecture anyway. Canaries are not so great, their potential absence can be forgiven.

*Arch Linux*'s packages contain mentioned mitigations. Same applies to e.g. *Fedora*, however the situation may be different with other distributions. Packages lacking the mentioned mitigations require manual compilation.

> Audit of running processes

<pre><code>checksec --proc-all</code></pre>

<div class="alert info"><p><em class="icon-info-circled"></em>**Info**<br>
**Checksec** script's presented further below.</p></div>

> Compiling an app with mitigations

- Install **ASP** and **GPG**:
<li style="list-style-type: none"><pre><code>sudo pacman -S asp gnupg
asp export extra/networkmanager
cd ./networkmanager</code></pre></li>
- Initiate compilation & automatic install:
<li style="list-style-type: none"><pre><code>makepkg -si</code></pre></li>
- Reboot after the successful installation.

> Automating compilation of problematic packages

- Use **srcpac**.
<li style="list-style-type: none"><pre><code>sudo pacman -S srcpac
man srcpac</code></pre></li>

<br><br><hr><br>

## Audit:
### Rootkit Hunter:
Rootkit Hunter's an on-demand rootkit scanner capable of capturing changes in critical OS files etc. It's a decent application primarily intended for servers but can fulfill its role on a desktop as well.

> Guide

- Installation and running an audit:
<li style="list-style-type: none"><pre><code>pacman -S rkhunter
rkhunter --versioncheck
rkhunter --propupd
rkhunter -c --enable all --disable none --rwo</code></pre></li>
- Rkhunter shall print all the warnings, most likely false positives. These should be fixed so they aren't shown in future.
- Example of my changes:
<li style="list-style-type: none"><pre><code>gedit /etc/rkhunter.conf
-----------------------------------
#
# FP Fix
SCRIPTWHITELIST="/usr/bin/egrep"
SCRIPTWHITELIST="/usr/bin/fgrep"
SCRIPTWHITELIST="/usr/bin/ldd"
SCRIPTWHITELIST="/usr/bin/vendor_perl/GET"
ALLOWDEVFILE="/dev/shm/pulse-shm-*"
ALLOWDEVFILE="/dev/shm/user-Shm_*"
ALLOWDEVFILE="/dev/shm/user-Valve*"
ALLOWHIDDENFILE="/etc/.updated"
ALLOWHIDDENFILE="/usr/share/man/man5/.k5identity.5.gz"
ALLOWHIDDENFILE="/usr/share/man/man5/.k5login.5.gz"</code></pre></li>
- Now there should be zero false positives and rkhunter should work as intended. It creates a database of critical OS files, any change will therefore prompt a warning. Feel free to put the scan into cron.
- You'll find more details on the [official website](http://rkhunter.sourceforge.net/) and [here](https://www.digitalocean.com/community/tutorials/how-to-use-rkhunter-to-guard-against-rootkits-on-an-ubuntu-vps).

<br>

### Lynis:
Lynis is an outstanding app capable of auditing many UNIX-based OSs, including Linux. It commences a detailed audit of the OS and afterwards prints recommendations for enhancing security.

> Guide

- Installation and running an audit:
<li style="list-style-type: none"><pre><code>pacman -S lynis
lynis update info
lynic -c</code></pre></li>

<br>

### Checksec:
Checksec's a script enabling kernel security config checkup and review of *memory corruption* mitigations of executables.

> Guide

- Install:
<li style="list-style-type: none"><pre><code>pacman -S checksec</code></pre></li>
- Auditing kernel security config:
<li style="list-style-type: none"><pre><code>checksec --kernel</code></pre></li>
- Auditing security features of packages:
<li style="list-style-type: none"><pre><code>checksec --proc-all</code></pre></li>
- You will find more details on the [official website](https://github.com/slimm609/checksec.sh).

<br><br><hr>

<h3 class="nocol">That's all. Stay safe! <img class="smile" src="https://securityhandbook.cz/img/sm/smile.svg" alt="smile"></h3>
