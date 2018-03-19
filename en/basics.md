# FAQ &ndash; Security Basics

## Glossary:
- <span class="green">hacker</span> &ndash; person (mis)using their knowledge (eg. in computer security area) for personal, usually illegal, profit; this definition was originally taken from the word *cracker*
- <span class="green">malware</span> &ndash; generic term for malicious software further split into many (more or less malicious) categories
- **adware** &ndash; malware category; SW containing ads and showing them to the user
- **bundleware** &ndash; superfluous (not necessarily malicious) software bundled to other software
- **foistware** &ndash; SW installed without user's knowledge designed to obtain money from user, usually by prompting that the OS is infected/broken and offering remedy for a price
- <span class="green">ransomware</span> &ndash; SW blocking user from accessing to user data and demanding payment to allow such access
- **rootkit** &ndash; code designed to hide presence of other malware on the device and aggravate their detection
- **exploit** &ndash; code taking advantage of a vulnerability in SW (including OS) in order to perform a specific action
- **zero-day (0-day)** &ndash; vulnerability exploited at the day of its disclosure or prior to it
- **APT** &ndash; &bdquo;Advanced Persistent Threat&ldquo;; advanced threat usually tailored for a specific target, common users don't bump into these
- <span class="green">payload</span> &ndash; core part of malware code that's responsible for the crucial malicious action

<br>

## Security Basics:
- Periodically backup your data.
- Don't use illegal software &ndash; most cracks found on internet are infected
- Prior to any action, double-check its autencity.
- Download SW only from its official website.
- Use strong passwords that are easy to remember:
<li style="list-style-type: none"><p class="imgsrc">*Password Strength.* Source: https://xkcd.com/936/</p>
![password_strength_sm](https://faq.mople71.cz/img/en/passwd.png)</li>
- Use different passwords for different services, consider using a [keyring](#basics7).
- Don't connect to unknown/unsafe networks, or at least never send any personal data through them and avoid using dangerous protocols (HTTP, FTP atc.). Ideally use a VPN.
- Pay attention to what data you enter and where you enter them &ndash; selling personal data is a profitable business.
- Don't forget the physical security factor &ndash; lock your device, set a UEFI password, disable boot menu etc.

<br>

## Safe Web Browsing:
- Use a securely configured web browser (see other FAQ chapters).
- Consider using a separate browser for personal things (eg. online banking).
- Don't visit unknown/untrusted sites and never download any files from them.
- Reduce visiting 18+ sites as it's quite common for them to serve malicious ads and code.
- Don't use social buttons outside the specific social network, these can be trivially mimicked.
- Avoid the **short URLs** &ndash; like https://bit.ly/tinyurlwiki etc. &ndash; as they can easily mask dangerous links.
- Refrain from using unsafe network SW such as <span class="red">Flash Player</span> or <span class="red">Java</span>, its exploitation is very common. At least disable it inside your browser.
- Only open email attachments from trusted senders.
- If you suspect a file to be malicious, always scan it before opening with eg.  [VirusTotal](https://www.virustotal.com/).

<div class="alert success"><p><img src="https://mople71.cz/img/success.png" alt="success"> <strong>Tip</strong><br>
The safest way to browse the web: <span class="green">securely configured live OS</span>. However, it should be pointed out that this option doesn't have to be 100% safe as well &ndash; for example the EFI can be exploited if the device was infected in the past.</p></div>

<br>

## Security Info Sources:
- [BleepingComputer](https://www.bleepingcomputer.com/)
- [The Hacker News](http://thehackernews.com/)
- [Threatpost](https://threatpost.com/)
- [Naked Security](https://nakedsecurity.sophos.com/)
- [LinuxSecurity](http://www.linuxsecurity.com/)

<br>

## Online File Analysis:
- [VirusTotal](https://www.virustotal.com/) &ndash; AV database
- [Metadefender](https://www.metadefender.com/) &ndash; AV database
- [Hybrid Analysis](https://www.reverse.it/) &ndash; sandbox + VT
- [Malwr](https://malwr.com/submission/) &ndash; Cuckoo sandbox

<br>

## Recommended VPN:
- [Freedome VPN](https://www.f-secure.com/en/web/home_global/freedome/) &ndash; blocks malware, trackers and ads
- [AirVPN](https://airvpn.org/) &ndash; advanced features, quite trustworthy
- [IVPN](https://www.ivpn.net/) &ndash; trustworthy
- [Cryptostorm](https://cryptostorm.is/) &ndash; trustworthy

<br>

## Recommended Keyrings:
- [1Password](https://1password.com/) &ndash; perfect platform, paid
- [KeePassX](https://www.keepassx.org/) &ndash; free
- [Encryptr](https://spideroak.com/solutions/encryptr/) &ndash; free
