# Instalace na Apple Silicon
## Potřebuješ vůbec tento návod?
Tento návod budeš potřebovat, pokud používáš počítač od Apple s Apple procesory řady M (také známa jako Apple Silicon). 

Tyto procesory se v Apple počítačích začaly objevovat v roce 2020.

Jestli už víš, že Tvé zařízení používá procesor Intel, můžeš přestat číst tento návod a přejdi [sem]({{ subpage_url('virtualbox') }}).

Pokud jsi stále na pochybách, raději zkontroluj, jaké zařízení vlastně máš.

{{ anchor('jak-poznat-ktery-procesor-mas') }}
### Jak poznat který procesor máš
Cvakni na logo jablka.
{{ figure(
    img=static('apple-silicon/apple-logo.png'),
    alt='Ikonka jablka v horní liště',
) }}
Vyber možnost "O tomto Macu"
{{ figure(
    img=static('apple-silicon/about-mac.png'),
    alt='Výběr "O tomto Macu" z lišty',
) }}
Vyskočí na Tebe okno s informacemi o Tvém zařízení.
Tebe zajímá kolonka "Čip". 
{{ figure(
    img=static('apple-silicon/cpu-info.png'),
    alt='Okno s informacemi o procesoru',
) }}
- Pokud obsahuje nějakou zmínku o "Intelu", pak se tě tento návod netýká a můžeš pokračovat [na tomto odkaze]({{ subpage_url('virtualbox') }}).
- Pokud zmiňuje Apple a řadu M jako na obrázku, tak čti dál...

## Instalace UTM
Vzhledem k omezením spojených s architekturou Apple Silicon procesorů bude nejlepší použít nástroj zvaný [UTM](https://mac.getutm.app).

UTM je svobodný software, což mimo jiné znamená, že je zcela zdarma.

Pokud náhodou používáš balíčkovací nástroj brew, UTM nainstaluješ v terminálu pomocí příkazu 
`brew install --cask utm` a můžeš pokračovat [další kapitolou]({{ subpage_url('apple-silicon#vytvoreni-virtualniho-pocitace') }}).

Jinak UTM můžeš stáhnout z [oficiálních stránek](https://mac.getutm.app) kliknutím na tlačítko "Download".
{{ figure(
    img=static('apple-silicon/download-utm.png'),
    alt='Stažení UTM',
) }}

Stažení je nutné povolit cvaknutím na "Povolit".
{{ figure(
    img=static('apple-silicon/utm-download-window.png'),
    alt='Povolení stažení UTM',
) }}

Mělo by začít stahování a po chvíli by se v doku ve spodní části obrazovky měl objevit soubor nazvaný "UTM", případně "UTM.dmg".
{{ figure(
    img=static('apple-silicon/utm-in-dock.png'),
    alt='Stažený utm.dmg soubor v doku',
) }}

Na ten cvakni a vyskočí na tebe instalační okno.
{{ figure(
    img=static('apple-silicon/utm-install.png'),
    alt='Instalace UTM',
) }}
Nyní přetáhni UTM do složky "Applications".
Tím by měla být instalace dokončena.

{{ anchor('vytvoreni-virtualniho-pocitace') }}
## Vytvoření virtuálního počítače
{{ figure(
    img=static('apple-silicon/utm-create-vm.png'),
    alt='Vytvoření virtuálního stroje v UTM',
) }}
{{ figure(
    img=static('apple-silicon/utm-virtualize.png'),
    alt='Výběr virtualizace v UTM',
) }}
{{ figure(
    img=static('apple-silicon/utm-choose-linux.png'),
    alt='Výběr Linuxu v UTM',
) }}
{{ figure(
    img=static('apple-silicon/utm-setup-vm.png'),
    alt='Nastavení virtuálního stroje v UTM',
) }}
Obraz by už měl být stažen z [dřívější kapitoly]({{ subpage_url('index#stazeni-obrazu') }}).
Pokud si nic takového nepamatuješ, znovu si přečti [dřívější kapitolu]({{ subpage_url('index#stazeni-obrazu') }}) a poté se znovu vrať sem.

Obraz by v názvu měl obsahovat "Fedora" a mít koncovku `.iso`, případně být typu "ISO Disk Image".
{{ figure(
    img=static('apple-silicon/utm-choose-iso.png'),
    alt='Výběr obrazu v UTM',
) }}
{{ figure(
    img=static('apple-silicon/utm-ram.png'),
    alt='Výběr velikosti paměti v UTM',
) }}
{{ figure(
    img=static('apple-silicon/utm-storage.png'),
    alt='Výběr velikosti úložiště v UTM',
) }}
{{ figure(
    img=static('apple-silicon/utm-shared-dir.png'),
    alt='Nastavení sdílené složky v UTM',
) }}
{{ figure(
    img=static('apple-silicon/utm-summary.png'),
    alt='Shrnutí parametrů nového virtuálního stroje v UTM',
) }}

Tím by mělo být vytvoření virtuálního počítače dokončeno!

Nyní by mělo být možné jej spustit kliknutím na ikonku "Start".
{{ figure(
    img=static('apple-silicon/utm-start-vm.png'),
    alt='Spuštění virtuálního stroje v UTM',
) }}

## Instalace Fedory
Samotná instalace je popsána v kapitole [instalace systému]({{ subpage_url('index#install-system') }}).

Po jejím přečtení a provedení všech instrukcí se ještě vrať na poslední krok zpátky sem.

## Dokončení instalace
Nyní by Fedora měla být úspěšně nainstalována.

Po vypnutí virtuálního stroje ještě klikni na "External Drive" a vyber možnost "Clear" jako na obrázku.
{{ figure(
    img=static('apple-silicon/utm-finish.png'),
    alt='Odstraněni externího disku v UTM',
) }}

Poté by se po kliknutí na ikonku start měla spouštět nainstalovaná Fedora. 


Tohle by už mělo být opravdu všechno a můžeš pokračovat dále. 