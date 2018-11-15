# FAQ &ndash; Základní informace

## Základní pojmy:
- <span class="green">hacker</span> &ndash; člověk zneužívající svých znalostí (např. v oblasti počítačové bezpečnosti) za účelem osobního zisku, tento význam je původně převzatý z pojmu *cracker*
- <span class="green">malware</span> &ndash; termín pro škodlivý software, jež se dělí na mnoho (méně či více škodlivých) podskupin
- **adware** &ndash; malware, který obsahuje reklamy a zobrazuje je uživateli
- **bundleware** &ndash; nadbytečný (ne nutně škodlivý) software, který je přibalen k validnímu software
- **foistware** &ndash; software nainstalovaný bez vědomí uživatele, který se zpravidla snaží přesvědčit uživatele o chybách v OS a nabízí jejich odstranění za poplatek
- <span class="green">ransomware</span> &ndash; software, který zabraňuje uživateli v přístupu ke svým datům a za obnovení přístupu požaduje poplatek
- **rootkit** &ndash; kód, který skrývá přítomnost malware v OS a ztěžuje jeho detekci
- <span class="green">exploit</span> &ndash; kód využívající chyby v jiném SW (klidně přímo v OS) za účelem provedení požadované akce
- **zero-day (0-day)** &ndash; zranitelnost, která byla zneužita v den jejího zveřejnění (příp. před ním)
- **APT** &ndash; &bdquo;Advanced Persistent Threat&ldquo;; pokročilejší hrozba, většinou vytvářená na míru, běžný uživatel s ní obvykle nepřijde do styku
- **payload** &ndash; část kódu malware, která vykonává klíčovou škodlivou akci

<br>

## Základy bezpečnosti:
- Pravidelně zálohujte data.
- Nepoužívejte nelegální software &ndash; většina cracků běžně dostupná na internetu je infikována.
- Před vykonáním libovolné akce dvakrát zkontrolujte její autenticitu.
-	Veškerý SW stahujte výhradně ze stránek výrobce.
- Používejte silná hesla dostatečně jednoduchá na zapamatování:
<li style="list-style-type: none"><p class="imgsrc">*Password Strength.* Zdroj: https://xkcd.com/936/ | [CC BY-NC 2.5](https://creativecommons.org/licenses/by-nc/2.5/)</p>
![password_strength_sm](https://faq.mople71.cz/img/en/passwd.png)</li>
- Používejte více hesel na různé služby, zvažte použití [klíčenky](#basics7).
- Nepřipojujte se k neznámým/veřejným bezdrátovým sítím, případně přes ně neposílejte citlivé údaje a vyvarujte se nebezpečným protokolům (HTTP, FTP apod.). Ideálně použijte VPN.
- Dávejte si pozor, kam jaké údaje zadáváte &ndash; s osobními údaji se dobře obchoduje.
- Nezapomeňte na fyzické zabezpečení zařízení &ndash; nastavte UEFI heslo, vypněte boot menu apod.

<br>

## Bezpečný pohyb na internetu:
- Používejte bezpečně nastavený prohlížeč (viz. ostatní kapitoly FAQ).
-	Zvažte využití odděleného prohlížeče pro citlivé věci (např. bankovnictví).
- Nenavštěvujte pochybné/neznámé stránky a nestahujte z nich žádné soubory.
- Omezte navštěvování erotických stránek, velmi často jsou oběti malwaretisingu a obsahují škodlivý kód.
-	Nepoužívejte sociální tlačítka na žádných stránkách mimo stránky dané sociální sítě. Falšování sociálních tlačítek je triviální a velmi oblíbené.
- Vyvarujte se tzv. **zkráceným odkazům** &ndash; např. https://bit.ly/tinyurlwiki apod. Mohou jednoduše maskovat nebezpečné odkazy.
- Vyvarujte se nebezpečnému síťovému SW jako <span class="red">Flash Player</span> a <span class="red">Java</span>, jeho exploitace je oblíbená a velmi častá. Případně jej alespoň zakažte ve vašem prohlížeči.
- Otevírejte pouze důvěryhodné e-mailové přílohy.
- Máte-li podezření na infikovaný soubor, vždy jej před otevřením otestujte pomocí např. [VirusTotal](https://www.virustotal.com/).

<div class="alert success"><p><em class="icon-ok-circled"></em>**Tip**<br>
Nejbezpečnější možnost prohlížení internetu: <span class="green">bezpečně nastavený live OS</span>. Také ovšem nemusí být 100% – např. pokud zařízení, ze kterého je OS spouštěn, bylo dříve napadeno, může být infikováno EFI.</p></div>

<br>

## Bezpečné používání mobilních zařízení:
- Používejte aktuální záplatovanou **originální** verzi OS.
- Neprovádějte na své zařízením *root* / *jailbreak* &ndash; touto akcí rozbíjíte bezpečnostní model mobilních OS.
- Instalujte aplikace pouze z důvěryhodných zdrojů &ndash; *Google Play, F-Droid* / *Apple Store* / *Microsoft Store*.
- Neinstalujte aplikace vyžadující nesmyslná oprávnění (např. Flashlight+ vyžadující přístup k SMS a kontaktům).
- Všechny rizikové činnosti provádějte pod účtem hosta.
- Nezapomeňte na fyzické zabezpečení zařízení &ndash; nastavte zamykací heslo, neodemykejte bootloader apod.

<br>

## Informace o aktuálních událostech v počítačové bezpečnosti:
- [CSIRT.cz](https://csirt.cz/news/security/)
- [Root.cz &ndash; bezpečnost](https://www.root.cz/bezpecnost/)
- [Twitter &ndash; #ITbezpecnost](https://twitter.com/hashtag/ITbezpecnost)

<h3 class="nocol">Anglické zdroje:</h3>
- [BleepingComputer](https://www.bleepingcomputer.com/)
- [The Hacker News](http://thehackernews.com/)
- [Threatpost](https://threatpost.com/)
- [LinuxSecurity](http://www.linuxsecurity.com/)

<br>

## Online analýza souborů:
- [VirusTotal](https://www.virustotal.com/) &ndash; AV databáze
- [Metadefender](https://www.metadefender.com/) &ndash; AV databáze
- [Hybrid Analysis](https://www.reverse.it/) &ndash; sandbox + VT
- [Malwr](https://malwr.com/submission/) &ndash; Cuckoo sandbox

<br>

## Doporučené VPN:
- [Freedome VPN](https://www.f-secure.com/en/web/home_global/freedome/) &ndash; blokuje malware, trackery a reklamy
- [AirVPN](https://airvpn.org/) &ndash; pokročilé funkce, vcelku důvěryhodná
- [IVPN](https://www.ivpn.net/) &ndash; důvěryhodná
- [Cryptostorm](https://cryptostorm.is/) &ndash; důvěryhodná

<br>

## Doporučené klíčenky:
- [1Password](https://1password.com/) &ndash; špičková platforma, placená
- [Bitwarden](https://bitwarden.com/) &ndash; bezplatná
- [KeePassX](https://www.keepassx.org/) &ndash; bezplatná
