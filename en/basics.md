# FAQ – Security Basics

## Glossary:
- <span class="green">hacker</span> – an individual misusing their knowledge (e.g. in computer security area) for personal profit; this definition originally comes from the *cracker* term
- <span class="green">malware</span> – generic term for malicious software which further divides into many (more or less malicious) categories
- <span class="green">ransomware</span> – software preventing user from accessing their data and demanding payment to reinstate such permission
- **rootkit** – code designed to mask presence of malware on the device and aggravate their detection
- <span class="green">exploit</span> – code taking advantage of a vulnerability in SW (including OS) in order to perform a specific action
- **zero-day (0-day)** – vulnerability exploited at the day of its disclosure (or prior to it)
- **adware** – type of malware which contains ads and shows them to the user
- **bundleware** – superfluous (not necessarily malicious) software bundled to a valid software
- **foistware** – software installed without user's knowledge, designed to draw money from user typically by prompting the OS is infected/broken and offering remedy for a price
- **APT** – &bdquo;Advanced Persistent Threat&ldquo;; advanced threat typically tailored for a specific target, everyday user doesn't bump into these
- **payload** – core part of malware code that's responsible for the malicious action

<br>

## Security Basics:
- Periodically backup your data.
- Refrain from using illegal software – most cracks generally found on internet are infected.
- Prior to commencing any action, double-check its autencity.
- Download all SW exclusively from its official website.
- Use strong passwords that are easy to remember:
<li style="list-style-type: none"><p class="imgsrc">*Password Strength.* Source: https://xkcd.com/936/ | [CC BY-NC 2.5](https://creativecommons.org/licenses/by-nc/2.5/)</p>
![password_strength_sm](https://faq.mople71.cz/img/en/passwd.png)</li>
- Use a different password for each service, consider using a [password manager](#basics8).
- Don't connect to unknown/public networks and avoid using unsafe protocols – HTTP, FTP,&#8230; – or at least don't send any personal data through them. Consider using a VPN.
- Pay attention to where you enter what data – selling personal data is a highly profitable business.
- Don't forget the physical security factor – lock your device, set a UEFI password, disable boot menu etc.

<br>

## Surfing Securely:
- Use a securely configured web browser (see other FAQ chapters).
- Consider using a separate browser for personal business (e.g. online banking).
- Don't visit unknown/untrusted sites and never download any files from them.
- Reduce visiting 18+ sites as it's quite common for them to be a victim of malwaretising and serve malicious code.
- Don't use social buttons outside the specific social network, it's trivial to mimick thse.
- Avoid the **short URLs** – like https://bit.ly/tinyurlwiki – as they can easily mask dangerous links.
- Refrain from using unsafe network SW such as <span class="red">Flash Player</span> or <span class="red">Java</span>, their exploitation is popular and very common. At minimum, disable them inside your browser.
- Only open email attachments from trusted senders.
- Should you suspect a file to be malicious, always scan it prior to opening with e.g. [VirusTotal](https://www.virustotal.com/).

<div class="alert success"><p><em class="icon-ok-circled"></em><strong>Tip</strong><br>
The safest way to browse the web: <span class="green">securely configured live OS</span>. However, it should be pointed out that this option doesn't have to be 100% safe as well – for example if the device has been hacked in the past, the EFI may be infected.</p></div>

<br>

## Using Mobile Devices Securely:
- Use an updated, patched and **original** OS version.
- Don't *root* / *jailbreak* your device – such action breaks the security model of the OS.
- Install apps exclusively from trusted sources – *Google Play* / *Apple Store* / *Microsoft Store*.
- Avoid installing apps requesting unreasonable permissions (e.g. Flashlight+ demanding access to your SMS and contacts).
- Don't forget the physical security factor – lock your device, keep the bootloader locked etc.

<br>

## Security News Sources:
- [BleepingComputer](https://www.bleepingcomputer.com/)
- [The Hacker News](http://thehackernews.com/)
- [Threatpost](https://threatpost.com/)
- [LinuxSecurity](http://www.linuxsecurity.com/)

<br>

## Online File Analysis:
- [VirusTotal](https://www.virustotal.com/) – AV database
- [Metadefender](https://www.metadefender.com/) – AV database
- [Hybrid Analysis](https://www.reverse.it/) – sandbox + VT
- [Malwr](https://malwr.com/submission/) – Cuckoo sandbox

<br>

## Recommended VPNs:
- [Freedome VPN](https://www.f-secure.com/en/web/home_global/freedome/) – blocks malware, trackers and ads
- [IVPN](https://www.ivpn.net/) – trustworthy
- [Cryptostorm](https://cryptostorm.is/) – trustworthy

<br>

## Recommended Password Managers:
- [1Password](https://1password.com/) – impeccable service, requires payment
- [Bitwarden](https://bitwarden.com/) – free of charge
