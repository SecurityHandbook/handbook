# FAQ &ndash; OS Android
Android ...


#### FAQ are divided into several sections:
- Android security model
- general recommendations
- secure devices
- secure OS configuration
- recommended applications
- secure ROMs

<br>

## Android security model:
Android has a robust layered security model. It's based on linux kernel, implements <abbr title="Mandatory Access Control">MAC</abbr> and mitigations against *memory corruption* exploits  &ndash; Android is the only linux distribution that disallows exectuing *non-<abbr title="Position Independent Executable">PIE</abbr>* code. Each application is assigned its own unique user ID and sandboxed, therefore cannot operate with any other application and is only allowed to operate with files/OS components to which it gains permission from the device owner.

![Android Security Model](https://faq.mople71.cz/img/en/and.png)

> A little more theory on the Android security model

#### Kernel:
Android is based on the linux kernel. While linux kernel may not the best available option when it comes to security, it offers Android a decent permission model based on users and user groups, process isolation etc. Furthermore the security perspective of the kernel has been gaining more attention recently and it's constantly getting better.

#### MAC:
Android **Kitkat** and above use a modified version of the linux MAC *SELinux* &ndash; **SEAndroid**. SEAndroid significantly reduces the attack surface and also plays a major role in Android's permission model. Only a tiny piece of code now runs with full root permissions because of SEAndroid. The MAC implementation received significant enhancements in versions **Lollipop** and **Oreo**.

#### Apps:
Android requires every application to be digitally signed &ndash; an unsigned application cannot be installed. In addition, it implements several security check points for apps, based on which an app can be marked as malicious and prevented from installing (this feature requires Google services). Furthermore the default configuration only allows installation from the preinstalled app store &ndash; usually **Google Play**.

All applications are confined in a sandbox (*IsolatedProcess*), meaning each application is isolated from other applications and the OS. Android implements a **seccomp** sandbox that offers advanced isolation capabilities and results in better security. This sandbox is internally used eg. by *Google Chrome*.

Android **Marshmallow** and above offer an enhanced permission model &ndash; user can configure which files/components the application gains access. The stock permission manager is still imperfect as it doesn't offer configuration of several important permissions, but othervise works flawlessly unlike the third-party permission managers (such as *XPrivacy*).

Features dependent on Google services (eg. *VerifyApps*, *Google Play Protect*) will not be discussed here.

<br><br><hr><br>

## General Recommendations:
- use the newest patched Android release, at least **Nougat**
- don't root your device &ndash; root breaks the security model discussed above
- don't unlock your device's bootloader and don't flash potentially unsecure recovery partitions (eg. *TWRP*)
- use stock Android with minimal vendor bloatware
- don't flash unsafe ROMs with broken root implementation (eg. LineageOS)
- only install apps from trusted sources &ndash; Google Play, Amazon, F-Droid
- don't use applications requiring absurd permissions (Flashlight+++ requesting SMS and contacts access)
- consider using open-source applications instead of proprietary (FOSS &ndash; free and open-source software)
- don't connect to unknown/unsafe networks (eg. at the airport), consider using a VPN
- carry out all risky actions under the Guest account
- encrypt and lock your device, don't forget the physical security aspect

### General Recommendations for advanced:
-
