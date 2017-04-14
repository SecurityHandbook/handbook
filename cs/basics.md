# FAQ &ndash; Základní informace

## Základní pojmy:
- <span class="green">hacker</span> &ndash; člověk zneužívající svých znalostí (např. v oblasti počítačové bezpečnosti) za účelem osobního zisku, tento význam je původně převzatý ze slova cracker
- <span class="green">malware</span> &ndash; termín pro škodlivý software, jež se dělí na mnoho (méně či více škodlivých) podskupin
- **adware** &ndash; malware, který obsahuje reklamy a zobrazuje je uživateli
- **bundleware** &ndash; nadbytečný (ne nutně škodlivý) software, který je přibalen k validnímu software
- **foistware** &ndash; software nainstalovaný bez vědomí uživatele, který se snaží přesvědčit uživatele o chybách v OS a nabízí jejich odstranění za poplatek
- <span class="green">ransomware</span> &ndash; software, který zabraňuje uživateli v přístupu ke svým datům a za obnovení přístupu požaduje poplatek
- **rootkit** &ndash; kód, který skrývá přítomnost malware v OS a ztěžuje jeho detekci
- **exploit** &ndash; kód využívající chyby v jiném SW (klidně přímo v OS) za účelem provedení požadované akce
- **zero-day (0-day)** &ndash; zranitelnost, která byla zneužita v den jejího zveřejnění (příp. před ním)
- **APT** &ndash; &bdquo;Advanced Persistent Threat&ldquo;; pokročilejší hrozba, většinou vytvářená na míru, běžný uživatel s ní obvykle nepřijde do styku
- <span class="green">payload</span> &ndash; část kódu malware, která vykonává klíčovou škodlivou akci

<br>

## Základy bezpečnosti:
- Pravidelně zálohujte data.
- Nepoužívejte nelegální software &ndash; většina cracků běžně dostupná na internetu je infikována.
- Používejte silná hesla dostatečně jednoduchá na zapamatování. <a href="https://csirt.cz/files/csirt/password_strength_sm.png" target="_blank">Jak má vypadat silné a jednoduché heslo?</a>
- Používejte více hesel na různé služby, zvažte použití klíčenky (např. <a href="https://www.keepassx.org/" target="_blank">KeePassX</a> nebo <a href="https://spideroak.com/solutions/encryptr" target="_blank">Encryptr</a>).
- Nepřipojujte se k neznámým/veřejným bezdrátovým sítím, případně přes ně neposílejte citlivé údaje a vyvarujte se nebezpečným protokolům (HTTP, FTP apod.). Ideálně použijte VPN.
- Dávejte si pozor, kam jaké údaje zadáváte &ndash; s osobními údaji se dobře obchoduje.
- Omezte citlivé informace na sociálních sítích a zkontrolujte, pro koho jsou jaké informace viditelné.
- Nezapomeňte na fyzické zabezpečení PC &ndash; nastavte BIOS heslo, vypněte boot menu apod.

<br>

## Bezpečný pohyb na internetu:
- Používejte bezpečně nastavený prohlížeč (viz. níže).
- Nenavštěvujte pochybné/neznámé stránky a nestahujte z nich žádné soubory.
- Omezte navštěvování erotických stránek, velmi často jsou oběti malwaretisingu a obsahují škodlivý kód.
- Nepoužívejte sociální tlačítka na žádných stránkách kromě stránek dané sociální sítě. Falšování sociálních tlačítek je triviální a velmi oblíbené.
- Vyvarujte se tzv. **zkráceným odkazům** &ndash; např. http://bit.ly/tinyurlwiki apod. Mohou jednoduše maskovat nebezpečné odkazy.
- Programy stahujte výhradně ze stránek výrobce, vyvarujte se stránkám třetích stran jako Stahuj/Slunečnice apod.
- Vyvarujte se nebezpečnému síťovému SW jako <span class="green">Flash Player</span> a <span class="green">Java</span>, jeho exploitace je oblíbená a velmi častá. Případně jej alespoň zakažte ve vašem prohlížeči.
- Otevírejte pouze důvěryhodné e-mailové přílohy.
- Máte-li podezření na infikovaný soubor, vždy jej před otevřením otestujte pomocí např. <a href="https://www.virustotal.com/" target="_blank">VirusTotal</a>.

![idea](https://mople71.cz/sm/idea.gif) Nejbezpečnější možnost prohlížení internetu: <span class="green">zabezpečený live OS</span>. Nutno podotknout, že také není 100% &ndash; v případě, že PC, ze kterého je OS spouštěn, byl dříve napaden, může být infikován BIOS.

<br>

## Informace o aktuálních bezpečnostních hrozbách:
- <a href="https://csirt.cz/news/security/" target="_blank">CSIRT.cz</a>
- <a href="http://www.root.cz/bezpecnost/" target="_blank">Root.cz &ndash; bezpečnost</a>
- <a href="http://www.zive.cz/bezpecnost/sc-120/default.aspx?tags=1" target="_blank">Živě.cz &ndash; bezpečnost</a></li>
- <a href="http://cdr.cz/rubriky/bezpecnost" target="_blank">CDR.cz &ndash; bezpečnost</a>

<h3 id="basics4.1" class="nocol">Anglické zdroje:</h3>
- <a href="http://thehackernews.com/" target="_blank">The Hacker News</a>
- <a href="http://www.bleepingcomputer.com/" target="_blank">BleepingComputer</a>
- <a href="https://threatpost.com/" target="_blank">Threatpost</a>
- <a href="http://www.securityweek.com/" target="_blank">SecurityWeek</a>
- <a href="http://securityaffairs.co/wordpress/" target="_blank">Security Affairs</a>
- <a href="https://nakedsecurity.sophos.com/" target="_blank">Naked Security</a>
- <a href="http://linuxsecurity.com/" target="_blank">LinuxSecurity</a>

<br>

## Online analýza souborů:
- <a href="https://www.virustotal.com/" target="_blank">VirusTotal</a> &ndash; AV databáze
- <a href="https://malwr.com/submission/" target="_blank">Malwr</a> &ndash; Cuckoo sandbox
- <a href="https://www.reverse.it/" target="_blank">Hybrid Analysis</a> &ndash; sandbox + VT

<br>

## Doporučené VPN:
- <a href="https://www.f-secure.com/en/web/home_global/freedome?icid=1545" target="_blank">Freedome VPN</a> &ndash; blokuje malware, trackery a reklamy
- <a href="https://airvpn.org/" target="_blank">AirVPN</a> &ndash; pokročilé funkce, vcelku důvěryhodná
- <a href="https://www.ivpn.net/" target="_blank">IVPN</a> &ndash; důvěryhodná
