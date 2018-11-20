# FAQ &ndash; Security Basics

## Glossary:
- <span class="green">hacker</span> &ndash; an individual misusing their knowledge (in e.g. computer security area) for personal profit; this definition originally comes from the term *cracker*
- <span class="green">malware</span> &ndash; general term for malicious software further split into many (more or less malicious) categories
- **adware** &ndash; type of malware which contains ads and shows them to the user
- **bundleware** &ndash; superfluous (not necessarily malicious) software bundled to a valid software
- **foistware** &ndash; software installed without user's knowledge designed to obtain money from user, usually by prompting the OS is infected/broken and offering remedy for a price
- <span class="green">ransomware</span> &ndash; software preventing user from accessing their data and demanding payment to allow such access
- **rootkit** &ndash; code designed to hide the presence of other malware on the device and aggravate their detection
- <span class="green">exploit</span> &ndash; code taking advantage of a vulnerability in SW (including OS) in order to perform a specific action
- **zero-day (0-day)** &ndash; vulnerability exploited at the day of its disclosure (or prior to it)
- **APT** &ndash; &bdquo;Advanced Persistent Threat&ldquo;; advanced threat tyúically tailored for a specific target, common user doesn't bump into these
- <span class="green">payload</span> &ndash; core part of malware code that's responsible for the malicious action

<br>

## Security basics:
- Periodically backup your data.
- Don't use illegal software &ndash; most cracks generally found on internet are infected.
- Prior to any action, double-check its autencity.
- Download all SW only from its official website.
- Use strong passwords that are easy to remember:
<li style="list-style-type: none"><p class="imgsrc">*Password Strength.* Source: https://xkcd.com/936/ | [CC BY-NC 2.5](https://creativecommons.org/licenses/by-nc/2.5/)</p>
![password_strength_sm](https://faq.mople71.cz/img/en/passwd.png)</li>
- Use a different password for each service, consider using a [password manager](#basics8).
- Avoid connecting to unknown/unsafe networks, or at least don't send any personal data through them and avoid using unsafe protocols (HTTP, FTP atc.). Ideally use a VPN.
- Pay attention to what data you enter where &ndash; selling personal data is a highly profitable business.
- Don't forget the physical security factor &ndash; lock your device, set a UEFI password, disable boot menu etc.

<br>

## Surfing securely:
- Use a securely configured web browser (see other FAQ chapters).
- Consider using a separate browser for personal things (e.g. online banking).
- Don't visit unknown/untrusted sites and never download any files from them.
- Reduce visiting 18+ sites as it's quite common for them to be a victim of malwaretising and serve malicious code.
- Don't use social buttons outside the specific social network as these buttons can be trivially mimicked.
- Avoid the **short URLs** &ndash; like https://bit.ly/tinyurlwiki etc. They can easily mask dangerous links.
- Refrain from using unsafe network SW such as <span class="red">Flash Player</span> or <span class="red">Java</span>, their exploitation is popular and very common. At minimum, disable it inside your browser.
- Only open email attachments from trusted senders.
- If you suspect a file to be malicious, always scan it before opening with e.g.  [VirusTotal](https://www.virustotal.com/).

<div class="alert success"><p><img src="https://mople71.cz/img/success.png" alt="success"> <strong>Tip</strong><br>
The safest way to browse the web: <span class="green">securely configured live OS</span>. However, it should be pointed out that this option doesn't have to be 100% safe as well &ndash; for example the EFI can be infected if the device has been hacked in the past.</p></div>

<br>

## Using mobile devices securely:
- Use an updated, patched and **original** OS version.
- Don't *root* / *jailbreak* your device &ndash; such action breaks the security model of mobile OSs.
- Install apps only from trusted sources &ndash; *Google Play, F-Droid* / *Apple Store* / *Microsoft Store*.
- Refrain from installing apps requiring unreasonable permissions (someting like Flashlight+ demanding access to SMS and contacts).
- Perform risky activities exclusively under a Guest account.
- Don't forget the physical security factor &ndash; lock your device, don't unlock the bootloader etc.

<br>

## Security news sources:
- [BleepingComputer](https://www.bleepingcomputer.com/)
- [The Hacker News](http://thehackernews.com/)
- [Threatpost](https://threatpost.com/)
- [LinuxSecurity](http://www.linuxsecurity.com/)

<br>

## Online file analysis:
- [VirusTotal](https://www.virustotal.com/) &ndash; AV database
- [Metadefender](https://www.metadefender.com/) &ndash; AV database
- [Hybrid Analysis](https://www.reverse.it/) &ndash; sandbox + VT
- [Malwr](https://malwr.com/submission/) &ndash; Cuckoo sandbox

<br>

## Recommended VPNs:
- [Freedome VPN](https://www.f-secure.com/en/web/home_global/freedome/) &ndash; blocks malware, trackers and ads
- [IVPN](https://www.ivpn.net/) &ndash; trustworthy
- [Cryptostorm](https://cryptostorm.is/) &ndash; trustworthy
- [AirVPN](https://airvpn.org/) &ndash; advanced features, quite trustworthy

<br>

## Recommended password managers:
- [1Password](https://1password.com/) &ndash; impeccable ecosystem, paid access
- [Bitwarden](https://bitwarden.com/) &ndash; free of charge
- [KeePassX](https://www.keepassx.org/) &ndash; free of charge
