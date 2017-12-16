# FAQ &ndash; OS Android
Android is the dominant OS on smartphone market (>88% share) developed by **Google, Inc.** Because of it's major share, Android gets a lot of attention from hackers.

Android has a robust security model which treats all apps as untrusted. The most critical security issue Android faces, is the diversity and partial decetralization of its ecosystem, where most devices don't receive regular security updates and/or run on outdated OS versions.

#### FAQ are divided into several sections:
- Android security model
- general recommendations
- secure devices
- secure OS configuration
- recommended applications
- secure ROMs

<br>

## Android security model:
Android has a robust layered security model. It's based on linux kernel, implements <abbr title="Mandatory Access Control">MAC</abbr> and mitigations against *memory corruption* exploits  &ndash; Android is the only linux distribution that disallows exectuing *non-<abbr title="Position Independent Executable">PIE</abbr>* code. Each application is assigned its own unique user ID and sandboxed, thus cannot operate with any other application and is only allowed to operate with files/OS components to which it gains permission from the device owner.

![Android Security Model](https://faq.mople71.cz/img/en/and.png)

> More theory regarding the Android security model

#### Kernel:
Android is based on the linux kernel. While linux kernel may not be the best available option when it comes to security, it offers Android a decent permission model based on users and user groups, process isolation etc. Furthermore, the security perspective of the kernel has been getting more attention lately and it's constantly getting better.

#### MAC:
Android **Kitkat** and above use a modified version of the linux MAC **SELinux** &ndash; *SEAndroid*. SEAndroid significantly reduces the attack surface and also plays a major role in Android's permission model. Only a tiny piece of code now runs with full root permissions thanks to SEAndroid. The MAC implementation received significant enhancements in versions **Lollipop** and **Oreo**.

#### Apps:
Android requires all applications to be digitally signed &ndash; an unsigned app cannot be installed. In addition, it implements several security checks for apps, based on which the app can be marked as malicious and prevented from installing (this feature requires Google services). Furthermore, the default configuration only allows installation from the preinstalled app store &ndash; usually **Google Play**.

All apps are confined in a sandbox (*IsolatedProcess*), meaning each app is isolated from others and the OS. Android **Oreo** and above widely implements a **seccomp** sandbox that offers advanced isolation capabilities and results in better security. Seccomp sandbox is internally used eg. by *Google Chrome*.

Android **Marshmallow** and above offers an advanced permission model &ndash; user can configure to which files/components the application gains access. The stock permission manager is still imperfect as it doesn't offer configuration of several important permissions, but othervise works flawlessly unlike the third-party permission managers (such as *XPrivacy*).

Features dependent on Google services (eg. *VerifyApps*, *Google Play Protect*) will not be discussed here.

<br><br><hr><br>

## General Recommendations:
- use the newest patched Android release, at least **Nougat**
- don't root your device &ndash; root breaks the security model discussed above
- don't unlock your device's bootloader and don't flash potentially insecure recovery partitions (eg. *TWRP*)
- don't flash unsafe ROMs with broken root implementation (eg. LineageOS)
- only install apps from trusted sources &ndash; Google Play, Amazon, F-Droid
- don't use apps requiring absurd permissions (like Flashlight+++ requesting SMS and contacts access)
- consider using open-source applications instead of proprietary (FOSS &ndash; free and open-source software)
- don't connect to unknown/unsafe networks (eg. at the airport), consider using a VPN
- carry out all risky actions under the Guest account
- encrypt and lock your device, don't forget the physical security aspect

### General Recommendations for advanced:
- don't root and never grant root access to any app, by doing so you're breaking the security model and extending attack surface &ndash; if an app with root privileges is exploited, your device is pwned
- use vendor's up-to-date ROM without bloatware
- don't flash things such as *Open GApps* &ndash; it's substantially less secure than a proper implementation of Google services by device vendor
- compile the ROM (+ kernel) and applications by yourself, you can then remove any ugly app permission directly in *AndroidManifest.xml*

<br><br><hr><br>

## Secure Devices:
As stated above, while the diversity of Android devices may be an advantage from a certain point of view, it's a huge issue from a security perspective.

Today, you can get a device running OS Android for a very low price. What nobody cares about though, are support and OS updates. Cheap devices typically won't ever get any security update, never mind OS version updates. In result, these devices contain hundreds of vulnerabilities which can be easily exploited unless they're patched. Needless to say, the situation doesn't have to be any better with more expensive and flagship devices $ndash; depends on the vendor.

Here're few key requirements the device should comply with in order to be evaluated as secure. You'll also find here a list of devices that meet the requierements.

### Security requirements for a device running OS Android:
- 64-bit architecture (x86/ARM)
- kernel >= 3.18 (ideally 4.4)
- full verified boot (ideally even for a custom ROM)
- *Treble* support
- frequent (monthly, at least quarterly) security updates for firmware and proprietary components
- guarantee of security updates for device's life span period (how long you're going to use the device)

<br>

### Devices compliant with security requirements:
You can find the list in the following guide: [Choosing a phone &ndash; OS Android](https://guide.mople71.cz/en/iot/andr_vyber.php#choo2).

<br><br><hr><br>

## Secure OS Configuration:
Android is (usually) configured with security in mind out of stock, however there's no harm in manually checking the configuration.

> Checking the security settings

- Open the <span class="green">Settings</span>.
- Find a subcategory **Security & location** and enter it.
- Check if you've got securely configured **Screen lock** &ndash; <span class="green">PIN</span> or <span class="green">Password</span>.
- Check your **Device admin apps**. There shouldn't be any except Google apps if you use them.
- Check the **Encryption** of your device.
- Close the application.

> Checking up-to-date OS

- Open the <span class="green">Settings</span>.
- Find a subcategory **System** and enter it.
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
- You'll automatically be switched to Guest account.
- To leave the Guest account, pull down the notification bar and tap <span class="green">Remove Guest</span>.
<li style="list-style-type: none">![andg1](https://faq.mople71.cz/img/en/andg1.png)</li>
- Confirm the action.

<br><br><hr><br>

## Recommended Applications:
The following section contains a list of recommended security applications or applications related to security. Apps are organized into two sections &ndash; proprietary and FOSS (free and open source). The reason is simple: some people don't trust proprietary applications and view using a closed source security app as absurd.

### App Store:
App store is closely related to security as it's (usually) the source of downloaded and installed apps. Therefore, it must be trustworthy and safe.

#### FOSS:
- F-Droid: https://f-droid.org/

#### Proprietary:
- Google Play: https://play.google.com/
- Amazon: https://www.amazon.com/appstore

*Amazon* has a lengthy process of application checking (manual) so it typically contains outdated app versions, at least those which are being frequently updated.

<br>

### Firewall:
Firewall is an essential security layer providing protection against network attacks. It's a must-have on public WiFi networks.

Integrated FW is the best option, yet very few ROMs provide it. Abusing the *VPN API* (NetGuard, NoRoot Data Firewall etc.) isn't the best and the most reliable option, but at least it doesn't require destroying the Android security model. Sadly, it seems almost noone's interested in implementing things correctly &ndash; directly into OS.

#### FOSS:
- integrated (CopperheadOS)
- NetGuard (VPN): https://github.com/M66B/NetGuard

#### Proprietary:
- NoRoot Data Firewall (VPN): https://play.google.com/store/apps/details?id=com.jianjia.firewall

<br>

### Ad Blocking:
Ad blocking is a necessary evil from a security perspective because of the tremendous amount of malicious ads around the web. It's recommended to support your favourite websites using a more secure (eg. financial) method.

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

DNS is a simple method of blocking most ads, but requires full trust in the DNS' provider. VPN is a good method as well, however *OpenVPN* implementation on Android is quite imperfect. Using a web browser with adblocking feature is the best option at the moment. **Chrome(ium)** will soon contain its own adblocker.

<br>

### Permission Manager:
Permission manager offers configuration which files/components can an app access.

#### FOSS:
- integrated (Marshmallow and above)

> Using the integrated permission manager

- Open the <span class="green">Settings</span>.
- Find a subcategory **Apps & notifications** and enter it.
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
Chrome(ium) is a very secure browser with modern mitigations on Linux, and on Android as well. Browsers based on *Mozilla Firefox* are still behind Chrome when it comes to exploit mitigations and code age/quality. It's getting better though.

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
