# Co je to ten „Linux“?

Máme tu kurz Linuxové administrace, ale co je vlastně Linux?

Striktně řečeno, *Linux* je název *jádra* (angl. *kernel*) operačního systému,
tedy softwaru, který se stará o nejzákladnější funkčnost počítače:
o komunikaci s hardwarem (klávesnicí, obrazovkou, diskem, síťovou kartou atd.),
a o to, aby na počítači mohly běžet ostatní programy.

Celý systém se pak skládá ze spousty dalších komponent, které se starají např.
o spouštění programů, vykreslování grafických okýnek, připojování k internetu,
editaci souborů nebo přehrávání hudby.

Na to všechno existuje software s *otevřeným zdrojovým kódem* (Open Source),
což znamená, že si kdokoli může stáhnout kód daného programu a upravit si ho
podle sebe (nebo někomu zaplatit, aby ho upravil).
Případné opravy pak může poslat zpět původním autorům, aby mohly
sloužit ostatním.
A nebo – třeba pokud původní autor se změnou nesouhlasí – může svoji novou
verzi dát k dispozici zvlášť, typicky pod jiným názvem.

Historie Linuxu ukazuje, jak se z jednoduchého projektu stal jeden
z nejvýznamnějších operačních systémů. V roce 1991 finský student Linus
Torvalds začal vyvíjet vlastní svobodný operační systém jako hobby projekt
a první verzi jádra zveřejnil 17. září téhož roku na FTP serveru ftp.funet.fi.
Původně chtěl projekt pojmenovat „Freax“ (free + freak + x), ale správce
serveru jej přejmenoval na „Linux“, což se stalo oficiálním názvem.

V té době již existoval projekt GNU, jehož cílem bylo vytvořit kompletní
svobodný operační systém, avšak chybělo mu stabilní jádro. Torvaldsovo jádro se
ukázalo jako ideální řešení, a tak vznikl systém známý jako GNU/Linux,
kombinující nástroje a knihovny z projektu GNU s linuxovým jádrem. V roce 1992
Linus Torvalds uvolnil Linux pod licencí GNU General Public License (GPL), čímž
zajistil, že kdokoli může software používat, studovat, upravovat a šířit.
To umožnilo rychlý rozvoj systému a vznik prvních distribucí, jako byly
Slackware, Debian, Red Hat Linux či SUSE Linux. V roce 1994 byla vydána první
stabilní verze jádra Linux 1.0.0, která položila základ pro další rozvoj
a postupnou expanzi Linuxu do serverového, vestavěného i mobilního prostředí.

Linux dnes běží na webových serverech, databázových systémech, cloudových
infrastrukturách, vestavěných zařízeních, mobilních telefonech, například
Android, i na superpočítačích. Aktivní komunita vývojářů a podpora organizací
jako Linux Foundation zajišťují, že Linux zůstává moderním, flexibilním
a spolehlivým operačním systémem, který se neustále vyvíjí a přizpůsobuje novým
technologiím.


Pro všechno, co budeme v tomto kurzu probírat, existuje několik variant
(kde ne, tam může kdokoli vytvořit svoji):

* Jádro systému – Linux, FreeBSD, OpenBSD, …
* Shell – Bash, zsh, csh, Fish, Xonsh, sh, …
* Základní nástroje – GNU coreutils, BusyBox, …
* Balíčkovací systém – DNF, APT, pacman, …
* Správce služeb – systemd, upstart. openrc, init, …
* Grafické prostředí – GNOME, KDE Plasma, XFCE, Mate, Sugar, …
* Textový editor – Gedit, Kate, vim, Emacs, Atom, nano, …
* Webový prohlížeč – Firefox, Chromium, qutebrowser, links, …
* Správce souborů – Nautilus, Dolphin, Konqueror, Thunar, …
* Kancelářské programy – LibreOffice, OpenOffice, Calligra Suite, …
* … a tak dále

Teoreticky si můžeš vybrat jednotlivé části podle sebe, nainstalovat si je
a propojit.
Existují ale i tzv *distribuce* (angl. *distros*), jejichž autoři to dělají za
tebe.
Obsahují předpřipravený výběr programů, které spolu fungují.
Různé distribuce se liší nejen výběrem programů, ale i třeba filosofií, s jakou
je vybírají a nastavují, a tím, kde nachází rovnováhu mezi jednoduchostí
a možností si všechno nastavit po svém.

A tak si můžeš vybrat jen z jedné kategorie:

* Distribuce – Fedora, Ubuntu, OpenSUSE, Debian, Arch, Gentoo, Alpine, …

Abychom tento kurz zvládli řídit a neutopili se ve spoustě možností,
jak můžou různé komponenty selhat, vybíráme ze všech těch variant jednu – tu,
se kterou mají autoři tohoto kurzu největší zkušenosti.
Konkrétní technologie, které v těchto materiálech použijeme,
jsou v seznamech výše uvedeny na prvním místě.
Všechno, co se naučíme, se ale – s větší či menší dávkou studia dokumentace –
dá použít i s alternativními technologiemi.

První věc, na kterou se podíváme, je základní ovládání grafického prostředí,
což je (v základní variantě Fedory) *GNOME*.
