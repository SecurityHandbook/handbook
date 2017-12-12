# FAQ &ndash; OS Android
Android is a dominant OS on the smartphone market (>88% share) developed by **Google, Inc.** Because of it's share, Android gets a lot of focus from hackers.

Android has a robust security model which assesses all apps as untrusted. The biggest security problem Android faces is the diversity and decetralization of its ecosystem, where most devices don't receive regular security updates and/or run on outdated OS versions.

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

Android **Marshmallow** and above offer an enhanced permission model &ndash; user can configure to which files/components the application gains access. The stock permission manager is still imperfect as it doesn't offer configuration of several important permissions, but othervise works flawlessly unlike the third-party permission managers (such as *XPrivacy*).

Features dependent on Google services (eg. *VerifyApps*, *Google Play Protect*) will not be discussed here.

<br><br><hr><br>

## General Recommendations:
- use the newest patched Android release, at least **Nougat**
- don't root your device &ndash; root breaks the security model discussed above
- don't unlock your device's bootloader and don't flash potentially insecure recovery partitions (eg. *TWRP*)
- use stock Android with minimal vendor bloatware
- don't flash unsafe ROMs with broken root implementation (eg. LineageOS)
- only install apps from trusted sources &ndash; Google Play, Amazon, F-Droid
- don't use applications requiring absurd permissions (Flashlight+++ requesting SMS and contacts access)
- consider using open-source applications instead of proprietary (FOSS &ndash; free and open-source software)
- don't connect to unknown/unsafe networks (eg. at the airport), consider using a VPN
- carry out all risky actions under the Guest account
- encrypt and lock your device, don't forget the physical security aspect

### General Recommendations for advanced:
- don't root and never grant root access to any application, you're breaking the Android security model and extending attack surface by doing so &ndash; if an app with root privileges is exploited, your device is pwned
- use vendor's up-to-date ROM without bloatware
- don't flash things such as *Open GApps* &ndash; it's substantially less secure than a proper implementation of Google services by device vendor
- compile the ROM (+ kernel) and applications by yourself, you can then remove any ugly app permission directly in *AndroidManifest.xml*

<br><br><hr><br>

## Secure Devices:
As stated above, the diversity of Android devices may be an advantage from a certain point of view, it's a huge problem from the security's point view though.

Today you can get a device running OS Android for a very low price. What nobody cares about though, is support and OS updates. Most cheap devices won't ever get any security update, never mind OS version updates. These devices therefore may contain hundreds of vulnerabilities which can be easily exploited if there's no patch for them. Needless to say, the situation doesn't have to be any better with more expensive devices.

Here're a few key requirements the device should comply with in order to be addressed as secure. You'll also find here a list of devices that meet the requierements.

### Security requirements for a device running OS Android:
- 64-bit architecture (x86/ARM)
- kernel >= 3.18 (ideally 4.4)
- full verified boot (ideally even for a custom ROM)
- *Treble* support
- frequent (monthly, at least quarterly) security updates for firmware and proprietary components
- guarantee of security updates for device's life span period (at minimum 1 year from purchase)

<br>

### Devices compliant with security requirements:
You can find the list in the following guide: [Choosing a phone &ndash; OS Android](https://guide.mople71.cz/en/iot/andr_vyber.php#choo2).

<br><br><hr><br>

## Secure OS Configuration:
Android is (usually) configured with security in mind out of stock, however there's no harm in opening settings and checking the configuration.

> Checking up-to-date OS

- Open the <span class="green">Settings</span>.
- Find a subcategory **System** and open it.
- Tap on <span class="green">About phone</span>.
- Check if your **Android version** is the newest &ndash; **8.1**
- Check if you've got recent **Android security patch level**.
 <li style="list-style-type: none">![andinf](https://faq.mople71.cz/img/en/andinf.png)</li>
- In case the *Android version* is older than **8.0** and the vendor hasn't confirmed the OS update, your device is implicitly insecure &ndash; look for a replacement. If the *Android security patch level* is older than **3 months**, your device is insecure &ndash; look for a replacement.
- You can find more about this in the following guide: [Choosing a phone &ndash; OS Android](https://guide.mople71.cz/en/iot/andr_vyber.php).
- Close the application.

<br>

### Using Guest account:
Guest account provides a relatively secure option to eg. surf the web. Installation of potentially unsafe applications is discouraged even uder Guest account because an app can exploit the whole OS way more easily than a website. Should the app gain root privileges (using eg. *CVE-2015-1805* aka KingRoot), you're *pwned*.

> Switching to Guest account

- Pull down the status bar using two fingers or extend it by tapping the arrow in the lower right corner.
- Tap your user account icon in the lower right column.
- A list of user account will appear. Tap on the <span class="green">Add guest</span> button.
<li style="list-style-type: none">![andg](https://faq.mople71.cz/img/en/andg.png)</li>
- You'll be automatically switched to Guest account.
- To leave the Guest account, pull down the notification bar and tap <span class="green">Remove Guest</span>.
<li style="list-style-type: none">![andg1](https://faq.mople71.cz/img/en/andg1.png)</li>
- Confirm the action.

<br><br><hr><br>

## Recommended Applications:
The following section contains a list of recommended security applications or applications related to security. Apps are divided to proprietary and FOSS (free and open source). The reason is simple: some people just don't trust proprietary applications and assess using a closed source security app as absurd.

### App Store:
App store is closely related to security as it's the source of most downloaded and installed apps. Therefore, it must be trustworthy and safe.

#### FOSS:
- F-Droid: https://f-droid.org/

#### Proprietary:
- Google Play: https://play.google.com/
- Amazon: https://www.amazon.com/appstore

*Amazon* has a lengthy process of application checking (manual) so it typically contains outdated app versions, at least those which are being frequently updated.

<br>

### Firewall:
Firewall is an essential OS security layer providing protection against network attacks. It's a must-have on public WiFi networks.

Integrated FW is the best option, however very few ROMs provide it. Abusing the *VPN API* (NetGuard, NoRoot Data Firewall etc.) isn't the best and the most reliable FW implementation, but at least it doesn't require the destruction of Android security model. Sadly, it seems almost noone's interested in implementing these things correctly &ndash; directly into OS.

#### FOSS:
- integrated (CopperheadOS)
- NetGuard (VPN): https://github.com/M66B/NetGuard

#### Proprietary:
- NoRoot Data Firewall (VPN): https://play.google.com/store/apps/details?id=com.jianjia.firewall

<br>

### Ad Blocking:
Ad blocking is a necessary evil from the security's point of view because of the tremendous amount of malicious advertisements around the web. It's recommended to support your favourite websites using a different more secure &ndash; financial &ndash; method.

#### FOSS local VPN:
- DNS66: https://github.com/julian-klode/dns66
- Blokada: http://blokada.org/

#### Proprietary local VPN:
- Adguard: https://adguard.com/en/adguard-android/overview.html

#### VPN:
- Freedome: https://play.google.com/store/apps/details?id=com.fsecure.freedome.vpn.security.privacy.android

#### Web Browser:
- Google Chrome / Chromium
- Brave: https://play.google.com/store/apps/details?id=com.brave.browser
- etc.

#### DNS:
- Adguard DNS: https://adguard.com/en/adguard-dns/overview.html

DNS is a simple method of blocking most ads, but trust in the DNS' provider is mandatory. VPN is a good method as well, however *OpenVPN* implementation on Android is quite imperfect. Using a web browser with adblocking feature is the best option. **Chrome(ium)** will soon contain its own adblocker.

<br>

### Permission Manager:
Permission manager offers configuration to which files/components the application has access. It's related to security in terms of privacy.

#### FOSS:
- integrated (Marshmallow and above)

> Using the integrated permission manager

- Open the <span class="green">Settings</span>.
- Find a subcategory **Apps & notifications** and open it.
- Tap on <span class="green">App permissions</span>.
- Go through all categories and remove all unnecessary permissions.
<li style="list-style-type: none">![andapp](https://faq.mople71.cz/img/en/andapp.png)</li>
<li style="list-style-type: none">![andapp1](https://faq.mople71.cz/img/en/andapp1.png)</li>
- Upon finishing configuration move from **App permissions** one level above and tap on **Advanced**.
- Open <span class="green">Special app access</span>.
- Here you can configure eg. which apps can modify system settings or display over other apps.
<li style="list-style-type: none">![andapp2](https://faq.mople71.cz/img/en/andapp2.png)</li>
- Review the configuration and then close the application.

<br>

### Web Browser:
Chrome(ium) is a very secure browser with modern mitigations on Linux &ndash; therefore on Android as well. Browsers based on *Mozilla Firefox* are still behind Chrome when it comes to exploit mitigations and code age/quality.

#### FOSS:
- Chromium: https://www.chromium.org/developers/how-tos/android-build-instructions
- Brave: https://play.google.com/store/apps/details?id=com.brave.browser

#### Proprietary:
- Google Chrome: https://play.google.com/store/apps/details?id=com.android.chrome

> JavaScript whitelisting in Google Chrome / Chromium

- Open <span class="green">Google Chrome</span> / <span class="green">Chromium</span>.
- Expand the menu by tapping three dots on the panel and open <span class="green">Settings</span>.
- Open **Site settings** and tap on <span class="green">JavaScript</span>.
- Block JS.
<li style="list-style-type: none">![chmandrjs](https://faq.mople71.cz/img/en/chmandrjs.png)</li>
- Tap on <span class="green">Add site exception</span>.
- Enter the address of a trustworthy website which can run JS. The syntax is slightly reduced compared to desktop version.
<li style="list-style-type: none">![chmandrjs1](https://faq.mople71.cz/img/en/chmandrjs1.png)</li>
- Click on <span class="green">Add</span>.

<br><br><hr><br>

## Secure ROMs:
The list is ordered from the most secure to the least secure.

- CopperheadOS: https://copperhead.co/android/
- stock Android &ndash; Nexus / Pixel
- vendor's Android without low-level bloatware
- vendor's Android with vendor's bloatware
- custom ROM without root implementation
- ...

<br><br><hr>

<h3 class="nocol">That' all. Stay safe! ![smile](https://mople71.cz/img/sm/smile.gif)</h3>
