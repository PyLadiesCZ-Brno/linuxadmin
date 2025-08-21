# Virtuální počítač

V tomto kurzu se budeme učit pracovat s operačním systémem Linux.
To je možné i v případě, že aktuálně používáš jiný operační systém - díky tzv. virtuálnímu počítači. To je program, který se tváří jako opravdový počítač a dá se do něj nainstalovat jiný operační systém.

To je velmi výhodné pro různé testování a objevování. Když si virtuální počítač rozbiješ, smažeš ho stejně snadno jako soubor a máš uklizeno.
Nebo si můžeš uložit stav a později se k němu vrátit.

Protože v kurzu budeme testovat, objevovat a občas i rozbíjet,
vytvoř si virtuální počítač i v případě, že už Linux používáš.

Hned na začátku tě čeká malá terminologická nepříjemnost:
**Hostitel** (anglicky **host**) je termín označující operační systém/počítač, v rámci kterého budeš provozovat ten virtuální – tedy to, co máš na počítači nainstalováno už teď.
Virtuálnímu systému se česky říká **host** (anglicky **guest**).
Slovo **host** má tedy v češtině úplně opačný význam než v angličtině.

{{ anchor('stazeni-obrazu') }}
## Stažení obrazu 

Na opravdový počítač se dá Linux nainstalovat z DVD nebo USB disku („flashky“).
Pro virtuální počítač budeš potřebovat virtuální DVD – soubor, který
obsahuje stejná data jako disk.
Říká se mu *obraz disku* nebo *ISO soubor*.

Existuje velké množství tzv. distribucí, tj. variant Linuxů. Ty se liší typicky
v dostupném software, grafickém prostředí, způsobu instalace softwarových
balíčků a spoustě dalších detailů.
Mezi nejznámější patří např. Ubuntu, Mint, Fedora, Arch nebo Debian.
Pro jednotnost si budeme všechno ukazovat na distribuci Fedora, kterou
si stáhni z [getfedora.org](https://getfedora.org/cs/workstation/download) –
stáhnout soubor ISO.

Je to velký soubor (zhruba 2 GB) s názvem `Fedora-Workstation-Live-x86_64-39-1.5.iso`.

### Poznámka pro uživatele macOS

Pokud máš macOS a nevíš, jestli máš procesor Intel, přečti si nejdříve [Jak poznat který procesor máš]({{ subpage_url('apple-silicon#jak-poznat-ktery-procesor-mas') }}) a poté se vrať zpět sem.
Jestli máš procesor od Apple řady M, pak si budeš muset stáhnout obraz pro systémy ARM aarch64.

Tedy něco jako `Fedora-Workstation-Live-aarch64-39-1.5-respin.iso`.


# Příprava hosta

Existuje několik programů, které umí simulovat virtuální počítač.
Vyber si jeden podle svého hostitelského systému:

* Pokud máš macOS a nevíš, jestli máš procesor Intel, přečti si [instalace na Apple Silicon]({{ subpage_url('apple-silicon') }})
* Pokud máš Windows nebo macOS s procesorem Intel, použij Virtualbox: [instalace Virtualboxu]({{ subpage_url('virtualbox') }}).
* Pokud máš Linux s GNOME, bude lépe fungovat Gnome Boxes: [instalace Gnome Boxes]({{ subpage_url('gnome-boxes') }}).

Nevíš-li, poraď se s někým zkušenějším – nebo zkus jeden z nich.


{{ anchor('install-system') }}
# Instalace systému

Při prvním spuštění je (virtuální) pevný disk zatím prázdný a ve virtuálním
počítači vsunut do virtuální DVD mechaniky ISO obraz, který obsahuje
soubory potřebné k samotné instalaci. 

{{ figure(
    img=static('fedora-install-01.png'),
    alt='Instalace #1',
) }}

V černém okně vyber šipkami na klávesnici (myš zatím nelze použít)
**Start Fedora-Workstation-Live 39** a potvrď klávesou Enter. 

{{ figure(
    img=static('fedora-install-02.png'),
    alt='Instalace #2',
) }}

Po chvilce se zobrazí grafické okno, kde myší klepni na **Install Fedora**. Tím se spustí samotná instalace. (Druhá volba *Not now* ti spustí
operační systém rovnou z DVD k vyzkoušení - tu ale nyní nevyužijeme).

## Instalační obrazovky

* **Výběr jazyka** - V levém panelu vyber *Čeština*, poté klepni na *Pokračovat*.
  (Můžeš vybrat i jiný jazyk, ale tyto materiály budou v češtině.)

  {{ figure(
    img=static('fedora-install-03.png'),
    alt='Instalace #3',
  ) }}


* **Přehled instalace** - Instalátor potřebuje potvrdit, kde se bude instalace
  provádět. Klepni na *Cíl instalace*, která ti nabídne dostupné pevné disky.

  {{ figure(
    img=static('fedora-install-04.png'),
    alt='Instalace #4',
  ) }}


* **Cíl instalace** - U virtuálního počítače je situace jednoduchá, není tu
  potřeba nic měnit.
  Vlevo nahoře najdeš tlačítko *Hotovo*, kterým obrazovku potvrdíš.

  {{ figure(
    img=static('fedora-install-05.png'),
    alt='Instalace #5',
 ) }}


* **Přehled instalace** - Nyní už instalátor ví vše potřebné. Vpravo dole
 klepni na tlačítko *Zahájit instalaci*. Od tohoto okamžiku se začne
 zapisovat na vybraný pevný disk.
 
  {{ figure(
    img=static('fedora-install-06.png'),
    alt='Instalace #6',
  ) }}


* **Průběh instalace** - tento krok bude trvat nejdéle. V závislosti na
 rychlosti tvého počítače to může být od pár minut po malé desítky minut.
 Nakonec se vpravo dole objeví tlačítko *Dokončit instalaci*. Tím dojde k 
 uzavření instalačního programu a je třeba provést restart.
 
  {{ figure(
    img=static('fedora-install-07.png'),
    alt='Instalace #7',
  ) }}

* **Vypnutí** - K tomu je potřeba kliknout na sadu ikonek úplně vpravo nahoře,
 poté na symbol ⏻ a nakonec na tlačítko *Restart*. Volbu potvrď.

   {{ figure(
    img=static('restart-01.png'),
    alt='Restart #1',
  ) }}
   {{ figure(
    img=static('restart-02.png'),
    alt='Restart #2',
  ) }}
   {{ figure(
    img=static('restart-03.png'),
    alt='Restart #3',
  ) }}

* **Vysunutí DVD** - Až se virtuální počítač vypne, je potřeba vysunout
  virtuální DVD, aby instalace nezačala znovu.
  GNOME Boxes to dělá automaticky, ale ve VirtualBoxu je to potřeba udělat
  ručně: klikni na Settings (Nastavení), Storage (Úložiště), disk
  "Fedora Worsktation Live" a tlačítko s DVD napravo.
  Z menu pak vyber "Remove Disk from Virtual Drive".

  {{ figure(
    img=static('vbox-settings.png'),
    alt='Settings',
  ) }}

  {{ figure(
    img=static('vbox-settings-storage.png'),
    alt='Nastavení DVD',
  ) }}

  {{ figure(
    img=static('vbox-settings-remove-dvd.png'),
    alt='Odstranění DVD',
  ) }}

* **Zapnutí** - Virtuální počítač potom znovu zapni a počkej než naběhne.

#### Dokončení instalace

V této části už je operační systém nainstalovaný,
 zbývá akorát provést posledních několik nastavení. To se děje formou průvodce,
 kde je vždy vpravo nahoře tlačítko *Další*.

* **Vítejte v prostředí Fedora Linux 39!** - klikni na "Začít nastavovat".

  {{ figure(
    img=static('fedora-install-09.png'),
    alt='Instalace #09',
  ) }}

* **Soukromí**
  * Geolokační služby - můžeš klidně vypnout
  * Automatické hlášení problémů - radši taky vypni; ať nikdo neví, jakou
    neplechu na virtuálním počítači napácháš

  {{ figure(
    img=static('fedora-install-10.png'),
    alt='Instalace #10',
  ) }}

* **Repozitáře třetích stran** - repozitáře není nutné povolovat, nebudeme je využívat.

  {{ figure(
    img=static('fedora-install-11.png'),
    alt='Instalace #11',
  ) }}
  
* **Účty online** - tento krok můžeš klidně přeskočit (a třeba provést později)

  {{ figure(
    img=static('fedora-install-12.png'),
    alt='Instalace #12',
  ) }}

  
* **O vás** - Nejdůležitější krok. Tady doplň *Celé jméno* (diakritika
 nevadí) a především *Uživatelské jméno* (pouze znaky `a-z`, `_`, `-`, číslice
 ). To je nejdůležitější. Tím se budeš přihlašovat do systému. Oba údaje lze
 změnit i později, avšak byť je změna *Uživatelského jména* v budoucnu
 technicky vzato možná, jde o problematický úkon. Proto je velmi důležité si
 ho dobře rozmyslet hned na začátku. (*Celé jméno* slouží jen jako popisek
  k uživatelskému jménu.) Pokračuj tlačítkem *Další*.

  {{ figure(
    img=static('fedora-install-13.png'),
    alt='Instalace #13',
  ) }}


 * **Nastavení hesla** - zde si nastavíš heslo k uživatelskému jménu vyplněném v předchozím
 kroku. Heslo je potřeba zadat do obou polí stejné.
 
 Navzdory obecným radám o heslech tady doporučuji zadat jednoduché heslo,
 třeba `123` nebo slovo `heslo`.
 Jde o *virtuální* počítač, který není potřeba nějak zvlášť chránit.

 Určitě ale nepoužívej heslo, které používáš i jinde!

  {{ figure(
    img=static('fedora-install-14.png'),
    alt='Instalace #14',
  ) }}

  Heslo si dobře zapamatuj (nebo, navzdory radám k bezpečným heslům, zapiš).

 * **Nastavení dokončeno** - Výborně, všechno je již nastaveno a můžeš se
  pustit do objevování. Klepni na *Začít používat systém Fedora Linux*.

  {{ figure(
    img=static('fedora-install-15.png'),
    alt='Instalace #15',
  ) }}

Virtuální počítač můžeš vypnout přes menu v pravém horním rohu obrazovky.
