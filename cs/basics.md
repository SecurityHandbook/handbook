# FAQ – Základy bezpečnosti

## Základní pojmy:
- <span class="green">hacker</span> – člověk zneužívající svých znalostí, např. v oblasti počítačové bezpečnosti, za účelem osobního zisku (význam původně převzatý z *cracker*)
- <span class="green">malware</span> – termín označující škodlivý software, jež se dělí na mnoho podskupin
- <span class="green">ransomware</span> – software, který zabraňuje uživateli v přístupu ke svým datům a za obnovení přístupu požaduje poplatek
- **adware** – software, který obsahuje reklamy a zobrazuje je uživateli
- **rootkit** – kód, který skrývá přítomnost malware v OS a ztěžuje jeho detekci
- <span class="green">exploit</span> – kód využívající chyby v jiném SW za účelem provedení specifikované (zpravidla škodlivé) akce
- **zero-day (0-day)** – zranitelnost, která byla zneužita v den jejího zveřejnění, příp. před ním
- **payload** – hlavní část kódu malware, která vykonává klíčovou škodlivou akci

<br>

## Základní bezpečnostní pravidla:
- Pravidelně zálohujte uživatelská data.
- Používejte nejnovější záplatovanou **originální** verzi OS.
- Vyvarujte se nelegálnímu software – většina cracků je infikována.
- Před vykonáním libovolné akce dvakrát zkontrolujte její autenticitu.
-	Instalujte aplikace výhradně z důvěryhodných zdrojů: *stránek výrobce* / *Microsoft Store*
  - na mobilních zařízeních: *Google Play* / *Apple Store*
- Používejte silná hesla dostatečně jednoduchá na zapamatování. Používejte více hesel na různé služby, zvažte použití [klíčenky](#basics7).
<li style="list-style-type: none"><p class="imgsrc">*Password Strength.* Zdroj: [xkcd](https://xkcd.com/936/) | [CC BY-NC 2.5](https://creativecommons.org/licenses/by-nc/2.5/)</p>
![password_strength_sm](https://securityhandbook.cz/img/en/passwd.png)</li>
- **Na mobilních zařízeních**:
  - neprovádějte *root* / *jailbreak* – touto akcí rozbíjíte bezpečnostní model OS
  - neinstalujte aplikace vyžadující nesmyslná oprávnění (např. Flashlight+ vyžadující přístup k SMS a kontaktům)
- Dávejte si pozor, kam jaké údaje zadáváte – s osobními údaji se dobře obchoduje.
- Nezapomeňte na fyzické zabezpečení zařízení: nastavte UEFI heslo, vypněte boot menu, neodemykejte bootloader,&#8230;

<br>

## Bezpečný pohyb na internetu:
- Nepřipojujte se k neznámým/veřejným bezdrátovým sítím a vyvarujte se nebezpečným protokolům – HTTP, FTP,&#8230; – případně přes ně neposílejte citlivé údaje. Zvažte použití VPN.
- Používejte bezpečně nastavený prohlížeč.
-	Zvažte využití odděleného prohlížeče pro citlivé věci (např. bankovnictví).
- Nenavštěvujte pochybné/neznámé stránky a nestahujte z nich žádné soubory.
- Omezte navštěvování erotických stránek, velmi často jsou oběti malwaretisingu a obsahují škodlivý kód.
-	Nepoužívejte sociální tlačítka na žádných stránkách mimo stránky dané sociální sítě. Falšování sociálních tlačítek je triviální.
- Vyvarujte se tzv. **zkráceným odkazům** – např. https://bit.ly/tinyurlwiki – mohou jednoduše maskovat nebezpečné odkazy.
- Otevírejte pouze důvěryhodné e-mailové přílohy / odkazy.

<div class="alert success"><p><em class="icon-ok-circled"></em>**Tip**<br>
Nejbezpečnější možnost prohlížení internetu: <span class="green">bezpečně nastavený live OS</span>. Nutno podotknout, že tato možnost také nemusí být 100% – např. pokud zařízení, ze kterého je OS spouštěn, bylo dříve napadeno, může být infikováno EFI.</p></div>

<br>

## Informace o aktuálních událostech v počítačové bezpečnosti:
- [CSIRT.cz](https://csirt.cz/news/security/)
- [Root.cz – bezpečnost](https://www.root.cz/bezpecnost/)
- [Twitter – #ITbezpecnost](https://twitter.com/hashtag/ITbezpecnost)

<h3 class="nocol">Anglické zdroje:</h3>
- [BleepingComputer](https://www.bleepingcomputer.com/)
- [The Hacker News](http://thehackernews.com/)
- [Threatpost](https://threatpost.com/)

<br>

## Online analýza souborů:
- [VirusTotal](https://www.virustotal.com/) – AV databáze
- [Metadefender](https://www.metadefender.com/) – AV databáze
- [Hybrid Analysis](https://www.reverse.it/) – sandbox + VT
- [Malwr](https://malwr.com/submission/) – sandbox

<br>

## Doporučené VPN:
- [Freedome VPN](https://www.f-secure.com/en/web/home_global/freedome/) – blokuje malware, trackery a reklamy
- [IVPN](https://www.ivpn.net/)
- [Cryptostorm](https://cryptostorm.is/)

<br>

## Doporučené klíčenky:
- [1Password](https://1password.com/) – placená
- [Bitwarden](https://bitwarden.com/) – bezplatná/placená
