# FAQ – Android OS
Android's the dominant mobile OS (>88% share) developed by **Google, Inc.** Due to its major share, Android enjoys a lot of attention from hackers.

Android has a robust security model which treats all apps as implicitly untrusted, its main security issue being the diversity of devices running Android, of which only a minority gets periodical security updates and/or runs on newest OS version.

> A little theory regarding Android OS security model

Android has a robust multilayer security model. It uses the Linux kernel, implements a <abbr title="Mandatory Access Control">MAC</abbr> and mitigations against *memory corruption* exploits – Android's the only linux distribution not supporting running *non-<abbr title="Position Independent Executable">PIE</abbr>* code. Each app's assigned their unique user ID and runs in sandbox, thus can't intervene with other apps and only is allowed to operate with files/OS components for which the user gives their permission.

![Android Security Model](https://securityhandbook.cz/img/en/and.png)
<p class="imgsrcf">*The Android security model (modified).* Source: [Android Security 2015 Annual Report](http://source.android.com/security/reports/Google_Android_Security_2015_Report_Final.pdf)</p>

#### Kernel:
Android's built on the Linux kernel. Linux kernel arguably might not be the best choice from security perspective, but offers a decent permission model based on users and user groups, process isolation etc.

#### MAC:
Android **Kitkat** and above uses a significantly modified Linux MAC implementation – *SEAndroid*. SEAndroid considerably reduces the attack surface and also plays an important role in Android's permission model. Thanks to the MAC implementation, only a tiny portion of code now runs with full root permissions. Major enhancements regarding MAC have been introduced in **Lollipop** and **Oreo** releases.

#### Apps:
Android requires all apps to be digitally signed – unsigned apps won't run. By default, apps can only be installed from a preinstalled app store – typically **Google Play**. Each app's confined in its own sandbox (*IsolatedProcess*), effectively being isolated from other apps and the OS. Android implements **seccomp** sandbox, providing advanced means isolation and higher degree of security. Seccomp sandbox's internally used e.g. by *Google Chrome* browser.

Android **Marshmallow** and above implements an app permission model – user chooses to which files/components apps gain access. Several enhancements've been introduced with every OS release, the last being **Q** right now. <span class="red">Using third-party permission managers (such as *XPrivacy*) is strongly discouraged.</span>

Features dependent on Google services (e.g. *VerifyApps*, *Google Play Protect*) shall be omitted.

#### FAQ is divided into several sections:
- [Secure Devices](#andr1)
- [Elementary Security Configuration](#andr2)
- [Recommended Apps](#andr3)

<br>

## Secure Devices:
As mentioned above, variety and diversity of devices running Android OS is a major security issue. Only a few manufacturers provide periodical security patches and OS updates for their models, for different reasons. As a result, brand new devices with old OS version and many known vulnerabilities – significantly raising the risk of exploitation – can be found on the market. Such practise unfortunately isn't only limited to cheap models, but more expensive ones as well. Users are therefore encouraged to consider security parametres when picking their device. Below you'll find several parametres a device should offer in order to be considered for selection.

### Security criteria for devices running Android OS:
- bundled OS version at least **Q** (*10*)
- periodical (monthly, at minimum quarterly) security updates for firmware and SoC
- guarantee of security updates for device's life span
- full verified boot
- 64-bit architecture (x86/ARM)
- kernel >= 4.4
- *Treble* support

<div class="alert info"><p><em class="icon-info-circled"></em>**Info**<br>
There're two levels of monthly security patches – **1st** day of the month and **5th** day of the month. Both levels are relevant for most devices on the market. If the manufacturer provides frequent updates for their device, but only implements the first patch level (e.g. *1 November 2019*), this may pose an issue.</p></div>

> Why OS version matters

Each new OS release introduces significant security and other enhancements. For example, **Marshmallow** introduced app permission model, empowering users to choose what each app can access. **Nougat** introduced a rewritten *MediaServer*, effectively incapacitating several families of exploits such as *Stagefright*. **Oreo** elevated sandboxing to a whole new level by introducing *Project Treble* and flat use of *seccomp* for apps. Above that enhanced *WebView* and app permission model. The list goes on for every release. It can be said with a clear conscience that <span class="red">no OS Android release prior to *Pie* is secure and shouldn't be used.</span>

> Why security updates matter

Let's look at one example. You install a malicious app on older <span class="green">8.1</span> Android – you've got control over app's permissions and can disable shady permissions. However, you don't have the newest security patches. The app can therefore exploit the OS using a known vulnerability – and user won't notice a thing, ever. Such practise's daily bread for Android malware as it's the simplest and cheapest way of device infection – more than **90 % of the devices hasn't got critical security patches**.

<br>

### Acceptable models meeting the criteria:
- **any model** of the **<span class="go">Pixel</span>** family
- **any model** of the [Android One](https://www.android.com/one/) project
- **any model** of the Nokia brand
- flagships of known manufacturers such as **SONY**, **<span class="sam">Samsung</span>**, **<span class="lg">LG</span>**, **<span class="hu">Huawei</span>** etc.
- higher **<span class="sam">Samsung</span>**'s and **SONY**'s models

<div class="alert info"><p><em class="icon-info-circled"></em>**Tip**<br>
You can also find inspiration in the [list of recommended devices for enterprises](https://androidenterprisepartners.withgoogle.com/devices/) od Google.</p></div>

<br><br><hr><br>

## Elementary Security Configuration:
Android's typically safely configured by default, but it never hurts to check your configuration.

> Security config check

- Open the <span class="green">Settings</span>.
- Find **Security & location** subcategory and enter it.
- Check secure config of the **Screen lock** – <span class="green">Password</span> or at least <span class="green">PIN</span>
- Check your **Device admin apps**. There should be none, except for Google's if you use them.
- Check **Encryption & credentials** status of your device.
- Close the app.

> Up-to-date OS check

- Open the <span class="green">Settings</span>.
- Find **System** subcategory and enter it.
- Tap on the <span class="green">About phone</span>.
- Check whether your **Android OS version** is up-to-date – **10.0** or above.
- Check whether your **Android security patch level** is the newest available.
<li style="list-style-type: none">![andinf](https://securityhandbook.cz/img/en/andinf.png)</li>
- Should your device run older *Android OS version* than **9.0** and the manufacturer hasn't confirmed an update, it's inherently insecure – consider looking for a replacement. Should your device contain older *Android security patch level* than **3 months**, it's unsafe to use – consider looking for a replacement.
- Close the app.

<br>

### Permissions manager:
Permissions manager empowers user to configure what information and components can each application access.

> App permissions configuration

- Open the <span class="green">Settings</span>.
- Find **Apps & notification** subcategory and enter it.
- Tap <span class="green">App permissions</span>.
- Go through the categories one by one and deny unnecessary access to all apps.
<li style="list-style-type: none">![andapp](https://securityhandbook.cz/img/en/andapp.png)</li>
<li style="list-style-type: none">![andapp1](https://securityhandbook.cz/img/en/andapp1.png)</li>
- Upon finishing go up a level from *App permissions* and expand **Advanced** options.
- Scroll down and enter <span class="green">Special app access</span>.
- Here you can set e.g. which apps have access to premium SMS or modifying system settings.
<li style="list-style-type: none">![andapp2](https://securityhandbook.cz/img/en/andapp2.png)</li>
- Close the app.

<br>

### Guest account:
Guest account provides a relatively safe means of e.g. browsing the web. Installing shady apps is discouraged even from the Guest account as apps' arsenal for exploiting the OS is considerably larger than a website's. Not even factory reset would help in such scenario.

> Switching to Guest account

- Open the <span class="green">Settings</span>.
- Find **Users & accounts** subcategory and enter it.
- Tap <span class="green">Users</span>.
- Switch to **Guest** account by tapping it in the list.
- Should you wish to return, pull down the notification bar and extend **Android system · Guest user**.
- Tap <span class="green">Remove Guest</span>.
<li style="list-style-type: none">![andg1](https://securityhandbook.cz/img/en/andg1.png)</li>
- Confirm the action.

<br><br><hr><br>

## Recommended Apps:
The following section contains recommended security apps and apps closely related to security. Applications are divided into FOSS (free & open source) and proprietary.

### App Store:
As the source of installed apps, an application store should be considered a crucial security component.

#### FOSS:
- F-Droid: https://f-droid.org/
- *Aurora Store – open-source frontend for Google Play*

#### Proprietary:
- Google Play: https://play.google.com/

Stores like *Amazon* or *Samsung* don't always have the latest app releases, especially of the frequently updated apps. Namely Amazon has an extremely long process of checking applications (done manually).

<br>

### Firewall:
Firewall's an essential OS security layer providing protection against network attacks. Its use on public WiFi connections is a must.

Integrated FW makes for the best option, unfortunately few ROMs offer any enhancements to the basic firewall. Abusing *VPN API* (NetGuard, NoRoot Data Firewall,&#8230;) may not be the nicest and most reliable option, but at least doesn't require destroying the OS's security model and works quite well.

#### FOSS:
- integrated
- NetGuard (VPN): https://github.com/M66B/NetGuard

#### Proprietary:
- NoRoot Data Firewall (VPN): https://play.google.com/store/apps/details?id=com.jianjia.firewall

<br>

### Ad Blocking:
Ad blocking's become a necessity beacuse of the web's amount of malicious ads. Supporting your favourite websites should be carrited out in a different and more secure way – donations, subscribtions,&#8230;

#### FOSS Local VPN:
- Blokada: http://blokada.org/
- DNS66: https://github.com/julian-klode/dns66

#### Proprietary Local VPN:
- Adguard: https://adguard.com/en/adguard-android/overview.html

#### VPN:
- Freedome: https://play.google.com/store/apps/details?id=com.fsecure.freedome.vpn.security.privacy.android

#### Web Browser:
- Brave: https://play.google.com/store/apps/details?id=com.brave.browser
- Google Chrome
- &#8230;

VPN's a great option for blocking ads, unfortunately Android doesn't natively support *OpenVPN* nor *WireGuard*, and users in most cases have to rely on third-party (typically their provider's) apps. Using a web browser capable of blocking ads appears as the best available option. **Chrome** already blocks aggressive ads. **Brave** browser by default blocks ads and trackers.

<br>

### Web Browser:
Chrome/Chromium's a browser with superior exploit mitigations. Browsers based on *Mozilla Firefox* are still lagging behind Chrome, especially on Android OS.

#### FOSS:
- Chromium: https://www.chromium.org/developers/how-tos/android-build-instructions
- Brave: https://play.google.com/store/apps/details?id=com.brave.browser

<!--- /browsers.md -->

#### Proprietary:
- Google Chrome: https://play.google.com/store/apps/details?id=com.android.chrome

<!--- /browsers.md -->

<br><br><hr>

<h3 class="nocol">That's all. Stay safe! <img class="smile" src="https://securityhandbook.cz/img/sm/smile.svg" alt="smile"></h3>
