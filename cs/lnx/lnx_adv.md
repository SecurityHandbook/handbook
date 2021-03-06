# OS Linux pro pokročilé
Linux se díky svému minoritnímu zastoupení na desktopech v porovnání s OS Windows těší řádově menší pozornosti hackerů – většina malware pro Linux je směřována pouze na servery. Malware pro desktopové linuxové distribuce také existuje, akorát v mnohonásobně menším množství. Ačkoliv je tedy stav mnohých desktopových linuxových distribucí z pohledu bezpečnosti tristní, v praxi je riziko infikace nižší nežli u jiných OS. Moderní *exploit kity* jsou ovšem často multiplatformní a jejich počet roste. Dostatečné zabezpečení OS je proto nezbytné.

Tato kapitola využívá distribuci **Arch Linux**.

Tato část příručky počítá s tím, že jste pročetli kapitolu [OS Linux pro méně pokročilé](https://securityhandbook.cz/cs/lnx/index.php#lnx) a máte minimálně znalosti v kapitole rozebírané.

#### Sekce kapitoly:
- [Základní bezpečnostní nastavení](#lnx1)
- [Ochrana proti malware](#lnx2)
- [Audit](#lnx3)

<br>

## Základní bezpečnostní nastavení:
### Sudo:
<pre><code>/etc/sudoers
-----------------------------------

Defaults   !visiblepw
Defaults    always_set_home
Defaults    match_group_by_gid
Defaults    always_query_group_plugin

Defaults    env_reset
Defaults    env_keep =  "COLORS DISPLAY HOSTNAME HISTSIZE KDEDIR LS_COLORS"
Defaults    env_keep += "MAIL QTDIR USERNAME LANG LC_ADDRESS LC_CTYPE"
Defaults    env_keep += "LC_COLLATE LC_IDENTIFICATION LC_MEASUREMENT LC_MESSAGES"
Defaults    env_keep += "LC_MONETARY LC_NAME LC_NUMERIC LC_PAPER LC_TELEPHONE"
Defaults    env_keep += "LC_TIME LC_ALL LANGUAGE LINGUAS _XKB_CHARSET XAUTHORITY"

Defaults    secure_path = /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
Defaults    use_pty

root        ALL=(ALL)    ALL
uživatel    ALL=(ALL)    ALL
</code></pre>
# atom underscore __

### Uzamknutí roota:
<pre><code>sudo passwd -l root</code></pre>

<br><br><hr><br>

## Ochrana proti malware:
### Firewall:
Pro běžné počítače stačí zakázat *forward* chain a bezpečně nastavit *input*. Nejjednodušší konfiguraci pro ipv4/6 nabízí **nftables**. Aplikační FW lze implementovat skrz <abbr title="Mandatory Access Control">MAC</abbr>.

> Příklad pravidel pro běžný počítač

<pre><code>/etc/nftables.conf
-----------------------------------

table inet filter {
    chain input {
        type filter hook input priority 0; policy drop;
        ct state invalid drop
        ct state established,related accept
        iif "lo" accept
    }

    chain forward {
        type filter hook forward priority 0; policy drop;
    }

    chain output {
        type filter hook output priority 0; policy accept;
    }
}</code></pre>

<br>

### MAC:
<abbr title="Mandatory Access Control">MAC</abbr> se stal důležitou součástí bezpečnostního modelu linuxových distribucí. Implementací existuje více.

**SELinux** je velmi robustní implementace MAC využívána např. distribucí **<span class="fe">Fedora</span>** nebo OS Android. **AppArmor** je implementace MAC poskytující nižší úroveň ochrany než SELinux (mj. neumí omezit ioctl) využívána distribucemi **<span class="os">openSUSE</span>** či **<span class="ub">Ubuntu</span>**. **TOMOYO Linux** je zajímavou méně známou alternativou, poskytující vyšší úroveň ochrany než AppArmor a zároveň nabízející mnohem jednodušší konfiguraci nežli SELinux.

Na Arch Linux lze bez problému provozovat TOMOYO nebo AppArmor, přičemž pro TOMOYO není třeba kompilovat vlastní kernel. SELinux je o něco složitější.

> Instalace TOMOYO Linux

<div class="alert info"><p><em class="icon-info-circled"></em>**Info**<br>
TOMOYO Linux není příliš rozšířený MAC a velmi těžko někde naleznete profily pro aplikace. Budete si je tedy muset sami vytvořit (příp. přepsat z AppArmor profilů – ty jsou všude). Dokumentaci naleznete [zde](https://tomoyo.osdn.jp/2.6/index.html.en).</p></div>

- Povolte TOMOYO Linux v GRUB:
<li style="list-style-type: none"><pre><code>/etc/default/grub
-----------------------------------

GRUB_CMDLINE_LINUX_DEFAULT="quiet security=tomoyo TOMOYO_trigger=/usr/lib/systemd/systemd"</code></pre></li>
- Aktualizujte GRUB (grub-mkconfig -o /boot/grub/grub.cfg).
- Nainstalujte **tomoyo-tools**:
<li style="list-style-type: none"><pre><code>sudo pacman -S gnupg
gpg --recv-keys 43C83369623D7AD3A96C2FC7425F128D0C64F52A
git clone https://aur.archlinux.org/tomoyo-tools.git
cd tomoyo-tools
gedit PKGBUILD</code></pre></li>
- Zkontrolujte instrukce a následně spusťte instalaci:
<li style="list-style-type: none"><pre><code>makepkg -si</code></pre></li>
- Restartujte OS.

> Použití TOMOYO Linux jako aplikační FW

- Po úspěšné instalaci a restartu OS inicializujte TOMOYO:
<li style="list-style-type: none"><pre><code>sudo /usr/lib/tomoyo/init_policy</code></pre></li>
- Následně upravte pravidla TOMOYO:
<li style="list-style-type: none"><pre><code>/etc/tomoyo/policy/current/profile.conf
-----------------------------------

PROFILE_VERSION=20110903
0-COMMENT=-----Disabled Mode-----
0-PREFERENCE={ max_audit_log=1024 max_learning_entry=2048 }
0-CONFIG={ mode=disabled grant_log=no reject_log=yes }
0-CONFIG::network::unix_stream_bind={ mode=disabled grant_log=no reject_log=no }
0-CONFIG::network::unix_stream_listen={ mode=disabled grant_log=no reject_log=no }
0-CONFIG::network::unix_stream_connect={ mode=disabled grant_log=no reject_log=no }
0-CONFIG::network::unix_dgram_bind={ mode=disabled grant_log=no reject_log=no }
0-CONFIG::network::unix_dgram_send={ mode=disabled grant_log=no reject_log=no }
0-CONFIG::network::unix_seqpacket_bind={ mode=disabled grant_log=no reject_log=no }
0-CONFIG::network::unix_seqpacket_listen={ mode=disabled grant_log=no reject_log=no }
0-CONFIG::network::unix_seqpacket_connect={ mode=disabled grant_log=no reject_log=no }
0-CONFIG::network={ mode=enforcing grant_log=no reject_log=yes }
1-COMMENT=-----Disabled Mode (net access)-----
1-PREFERENCE={ max_audit_log=1024 max_learning_entry=2048 }
1-CONFIG={ mode=disabled grant_log=no reject_log=no }
2-COMMENT=-----Learning Mode-----
2-PREFERENCE={ max_audit_log=1024 max_learning_entry=2048 }
2-CONFIG={ mode=learning grant_log=no reject_log=yes }
3-COMMENT=-----Permissive Mode-----
3-PREFERENCE={ max_audit_log=1024 max_learning_entry=2048 }
3-CONFIG={ mode=permissive grant_log=no reject_log=yes }
4-COMMENT=-----Enforcing Mode-----
4-PREFERENCE={ max_audit_log=1024 max_learning_entry=2048 }
4-CONFIG={ mode=enforcing grant_log=no reject_log=yes }</code></pre></li>
- Restartujte OS.
- Otevřete konfiguraci TOMOYO pro aplikace:
<li style="list-style-type: none"><pre><code>sudo tomoyo-editpolicy</code></pre></li>

<div class="alert exclaim"><p><em class="icon-attention"></em>**Varování**<br>
TOMOYO detekuje pouze aplikace, které byly od jeho aktivace alespoň 1x spuštěny.</p></div>

- Šipkami se posunujete mezi aplikacemi. Profil aplikace změníte klávesou <span class="red">S</span>, zadáním čísla profilu a stisknutím **Enter**.
<li style="list-style-type: none"><pre><code>0     #  bez přístupu k internetu
1     #  s přístupem k internetu
</code></pre></li>
- Klávesou <span class="red">Q</span> konfiguraci ukončíte.
- Po dokončení konfigurace ji následně uložte:
<li style="list-style-type: none"><pre><code>sudo tomoyo-savepolicy</code></pre></li>

<br>

### Hardened alokátor:

<div class="alert info"><p><em class="icon-info-circled"></em>**Info**<br>
Hardened malloc může působit problémy s aplikacemi, instalací znefunkčníte ze standardně využívaných např. *man*.</p></div>

- Stáhněte si [nejnovější verzi zdrojového kódu](https://github.com/GrapheneOS/hardened_malloc/releases/latest).
- Rozbalte, přesuňte se do extrahované složky a otevřete terminál. Instalace:
<li style="list-style-type: none"><pre><code>make
sudo cp libhardened_malloc.so /usr/local/lib</code></pre></li>
- Vyvořte potřebné konfigurační soubory:
<li style="list-style-type: none"><pre><code>/etc/ld.so.preload
-----------------------------------

/usr/local/lib/libhardened_malloc.so</code></pre></li>
<li style="list-style-type: none"><pre><code>/etc/sysctl.d/hardened_malloc.conf
-----------------------------------

vm.max_map_count = 524240</code></pre></li>
- Restartujte OS.

<br>

### Hardening aplikací:
Balíčky mohou být kompilovány s *memory corruption* mitigacemi (ASLR, PIE, RELRO, Canary,&#8230;), které následně významně ztěžují jejich exploitaci. Většina balíčků by standardně měla důležité mitigace obsahovat. Balíčky neobsahující zmíněné mitigace je nutné zkompilovat ručně.

> Audit mitigací běžících procesů

<pre><code>checksec --proc-all</code></pre>

<div class="alert info"><p><em class="icon-info-circled"></em>**Info**<br>
Skript **checksec** je podrobněji rozebírán níže.</p></div>

> Kompilace aplikace s mitigacemi

- Nainstalujte si **ASP** a **GPG**:
<li style="list-style-type: none"><pre><code>sudo pacman -S asp gnupg
asp export extra/networkmanager
cd ./networkmanager</code></pre></li>
- Zahajte kompilaci + automatickou instalaci:
<li style="list-style-type: none"><pre><code>makepkg -si</code></pre></li>
- Po úspěšné instalaci restartujte OS.

> Automatizace kompilace problémových balíčků

- Použijte **srcpac**.
<li style="list-style-type: none"><pre><code>sudo pacman -S srcpac
man srcpac</code></pre></li>

<br><br><hr><br>

## Audit:
### Rootkit Hunter:
Rootkit Hunter je on-demand skener rootkitů, který umí zachytávat změny v důležitých souborech OS atd. Jedná se o vcelku solidní aplikaci určenou primárně pro servery, neztratí se ovšem ani na desktopu.

> Návod

- Instalace a spuštění auditu:
<li style="list-style-type: none"><pre><code>pacman -S rkhunter
rkhunter --versioncheck
rkhunter --propupd
rkhunter -c --enable all --disable none --rwo</code></pre></li>
- Rkhunter vypíše veškerá svá varování, pravděpodobně false positives. Ty je potřeba opravit, aby se již v budoucnu nezobrazovaly.
- Příklad mých úprav:
<li style="list-style-type: none"><pre><code>gedit /etc/rkhunter.conf
-----------------------------------
#
# FP Fix
SCRIPTWHITELIST="/usr/bin/egrep"
SCRIPTWHITELIST="/usr/bin/fgrep"
SCRIPTWHITELIST="/usr/bin/ldd"
SCRIPTWHITELIST="/usr/bin/vendor_perl/GET"
ALLOWDEVFILE="/dev/shm/pulse-shm-*"
ALLOWDEVFILE="/dev/shm/user-Shm_*"
ALLOWDEVFILE="/dev/shm/user-Valve*"
ALLOWHIDDENFILE="/etc/.updated"
ALLOWHIDDENFILE="/usr/share/man/man5/.k5identity.5.gz"
ALLOWHIDDENFILE="/usr/share/man/man5/.k5login.5.gz"</code></pre></li>
- Nyní byste již měli být bez false positive varování a rkhunter by měl být plně funkční. Má uloženou databázi kritických souborů OS, takže v případě jakékoli změny (např. pomocí malware) zobrazí varování. Sken můžete dát do cronu.
- Více informací naleznete na [oficiálních stránkách](http://rkhunter.sourceforge.net/) a [zde](https://www.digitalocean.com/community/tutorials/how-to-use-rkhunter-to-guard-against-rootkits-on-an-ubuntu-vps).

<br>

### Lynis:
Lynis umožňuje bezpečnostní audit mnoha OS založených na UNIXu. Provádí velmi detailní audit OS a po dokončení auditu zobrazí doporučení pro zvýšení bezpečnosti.

> Návod

- Instalace a spuštění auditu:
<li style="list-style-type: none"><pre><code>pacman -S lynis
lynis update info
lynic -c</code></pre></li>

<br>

### Checksec:
Checksec je skript určený pro kontrolu nastavení kernelu a zobrazení *memory corruption* mitigací spustitelných souborů.

> Návod

- Instalace:
<li style="list-style-type: none"><pre><code>pacman -S checksec</code></pre></li>
- Můžete auditovat bezpečnost nastavení kernelu:
<li style="list-style-type: none"><pre><code>checksec --kernel</code></pre></li>
- Dále můžete auditovat bezpečnostní funkce balíčků:
<li style="list-style-type: none"><pre><code>checksec --proc-all</code></pre></li>
- Více informací naleznete na [oficiálních stránkách](https://github.com/slimm609/checksec.sh).

<br><br><hr>

<h3 class="nocol">To je vše. Stay safe! ![smile](https://securityhandbook.cz/img/sm/smile.svg)</h3>
