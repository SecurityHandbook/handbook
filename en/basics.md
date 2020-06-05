# FAQ – Security Basics

## Glossary:
- <span class="green">hacker</span> – an individual misusing their knowledge, e.g. in computer security, for personal gain (definition originally comes from the *cracker*)
- <span class="green">malware</span> – generic term for malicious software which further divides into many categories
- <span class="green">ransomware</span> – software preventing user from accessing their data and demanding payment to reinstate such access
- **adware** – software containing ads and displaying them to the user
- **rootkit** – code intended to mask the presence of other malware in OS and aggravate their detection
- <span class="green">exploit</span> – code taking advantage of a software vulnerability in order to perform a specific (typically malicious) action
- **zero-day (0-day)** – vulnerability exploited at the day of its disclosure (or prior to it)
- **payload** – core part of malware code responsible for the key malicious action

<br>

## Basic Security Guidelines:
- Periodically backup user data.
- Always use the latest patched **original** version of the OS.
- Refrain from using illegal software – most cracks are infected.
- Prior to performing any action, double-check its autencity.
- Install applications exclusively from trusted sources: *official website* / *Microsoft Store*.
  - on mobile devices: *Google Play* / *Apple Store*
- Use strong passwords that are easy to remember. Use different passwords for various services, consider using a [password manager](#basics7).
<li style="list-style-type: none"><p class="imgsrc">*Password Strength.* Source: [xkcd](https://xkcd.com/936/) | [CC BY-NC 2.5](https://creativecommons.org/licenses/by-nc/2.5/)</p>
![password_strength_sm](https://securityhandbook.cz/img/en/passwd.png)</li>
- **On mobile devices:**
  - don’t perform *root* / *jailbreak* – such action destroys the respective OS’s security model
  - avoid installing apps requesting unreasonable permissions (e.g. Flashlight+ demanding access to your SMS and contacts)
- Pay attention to where you enter your data – selling personal data is a highly profitable business.
- Don’t forget the physical security factor – lock your device, set a UEFI password, disable boot menu, refrain from unlocking the bootloader,&#8230;

<br>

## Secure Web Browsing:
- Don’t connect to unknown/public networks and avoid using unsafe protocols – HTTP, FTP,&#8230; – or at least don’t send any personal data through them. Consider using a VPN.
- Use a securely configured web browser.
- Consider using a separate browser for sensitive business (e.g. online banking).
- Don’t visit unknown/untrusted sites and never download any files from them.
- Reduce the visits of pornographic sites, it’s quite common for them to be a victim of malwaretising and serve malicious code.
- Don’t use social buttons outside the respective social network as it’s trivial to mimick these.
- Avoid the **short URLs** – like https://bit.ly/tinyurlwiki – as they can easily mask dangerous links.
- Only open email attachments / links from trusted senders.

<div class="alert success"><p><em class="icon-ok-circled"></em><strong>Tip</strong><br>
The safest way to browse the web: <span class="green">securely configured live OS</span>. However, it should be pointed out that this option doesn’t have to be 100% safe as well – for example if the device has been hacked in the past, the EFI may be infected.</p></div>

<br>

## Security News Sources:
- [BleepingComputer](https://www.bleepingcomputer.com/)
- [The Hacker News](http://thehackernews.com/)
- [Threatpost](https://threatpost.com/)

<br>

## Online File Analysis:
- [VirusTotal](https://www.virustotal.com/) – AV database
- [Metadefender](https://www.metadefender.com/) – AV database
- [Hybrid Analysis](https://www.reverse.it/) – sandbox + VT
- [Malwr](https://malwr.com/submission/) – sandbox

<br>

## Recommended VPNs:
- [Freedome VPN](https://www.f-secure.com/en/web/home_global/freedome/) – blocks malware, trackers and ads
- [IVPN](https://www.ivpn.net/)
- [Cryptostorm](https://cryptostorm.is/)

<br>

## Recommended Password Managers:
- [1Password](https://1password.com/) – paid
- [Bitwarden](https://bitwarden.com/) – free/paid
