# Soubory

Co je to soubor?

Lehce naivní ale přesto užitečná definice je: soubor je něco,
z čeho můžeme číst a/nebo do čeho můžeme zapisovat.

Se soubory se dají dělat i další operace než jen čtení a zápis, ale v tomto
kurzu se jimi většinou nebudeme zabývat.

Pravděpodobně máš největší zkušenosti se soubory, které jsou uložené na disku
pod nějakým jménem.
Třeba následující příkaz zapisuje do souboru `vystup.txt`:

```console
$ ps -Af > vystup.txt
```

Tento příkaz znamená: Bashi, spusť `ps -Af` a řekni mu aby psal do souboru
`vystup.txt`.
`ps` píše na svůj standardní výstup, což je soubor – v příkladu výše je to
soubor `vystup.txt`.

Kdybys výstup nepřesměroval{{a}}, uviděl{{a}} bys ho v terminálu.
Pro program `ps` se nic nemění: pořád píše na svůj standardní výstup,
což je *soubor*.

Je to soubor, který reprezentuje terminál – něco, do čeho může proces zapisovat
(a co se pak objeví na obrazovce) a z čeho může číst (když uživatel něco zadá).
Obsah tohoto souboru není uložen na disku, ale přesto jde o soubor.

Podívej se na tenhle příkaz:

```
$ ps -Af | grep -w ps
```

Příkaz `ps -Af` stále píše na svůj standardní výstup,
což je *soubor*.

V *tomhle* případě je to soubor, který reprezentuje „rouru“ – něco, do čeho
může jeden proces zapisovat a druhý to pak může číst.
Ani obsah roury není uložen na disku – „proudí“ přímo z jednoho procesu do
druhého – ale přesto jde o soubor.

Známe tedy už tři druhy souborů:

* normální souboru uložené na disku,
* terminál,
* rouru.


## Otevřené soubory procesu

Každý proces si může otevírat další soubory - to už znáš z funkce `open`
v Pythonu.
Podíváme se, jak zjistit seznam takto používaných souborů.
Existuje na to program `lsof` (z angl. *list open files*).
Většinou se spouští s přepínačem `-p <číslo procesu>`, aby ukázal jen
otevřené soubory jednoho procesu.

Použijme PID Bashe, které se jednoduše zjišťuje – je v proměnné `$$`:

```console
$ lsof -p $$
COMMAND  PID USER   FD   TYPE DEVICE SIZE/OFF    NODE NAME
bash    5236 user  cwd    DIR    8,1     4096 1310722 /home/user
bash    5236 user  rtd    DIR    8,1     4096       2 /
bash    5236 user  txt    REG    8,1  1113504  524393 /bin/bash
bash    5236 user  mem    REG    8,1    47568 7344943 /lib/x86_64-linux-gnu/libnss_files-2.27.so
bash    5236 user  mem    REG    8,1    26376 6032184 /usr/lib/x86_64-linux-gnu/gconv/gconv-modules.cache
(...)
bash    5236 user    0u   CHR  136,0      0t0       3 /dev/pts/0
bash    5236 user    1u   CHR  136,0      0t0       3 /dev/pts/0
bash    5236 user    2u   CHR  136,0      0t0       3 /dev/pts/0
bash    5236 user  255u   CHR  136,0      0t0       3 /dev/pts/0
```

Jak vidíš, je to poměrně velká tabulka.
* `COMMAND` je jméno programu, který otvírá daný soubor
  (bez `-p` vypisuje `lsof` soubory pro víc programů najednou).
* `PID` je číslo procesu, náš starý známý.
* `USER` je uživatel, jehož jménem proces běží.
* `FD` je zkratka pro **deskriptor souboru** (angl. *file descriptor*),
  což je číslo otevřeného souboru. Toto číslo nás bude dnes nejvíc zajímat.

   * `cwd` je speciální hodnota pro aktuální adresář
     (*current working directory*) – právě tahle hodnota se dá v Bashi změnit
     pomocí `cd`
   * `rtd` je kořenový adresář (*root directory*) - mělo by to být `/`
   * `txt` je kód samotného programu. (Každý program musí být uložený někde
     na disku. Když ho pustíš jako proces, systém soubor načte a začne provádět
     příkazy v něm uložené.)
   * `mem` jsou soubory načtené v paměti, většinou další součásti programu.
   * `0` a dál jsou konečně normální otevřené soubory.
     Písmenka označují mód, např.:
     * `1r` - otevřeno pro čtení (angl. *read*)
     * `1w` - otevřeno pro zápis (angl. *write*)
     * `1u` - otevřeno „univerzálně“, pro čtení i zápis
* `TYPE` může být např.
    * `DIR` - adresář
    * `REG` - normální soubor
    * `CHR` - speciální soubor, např. terminál
* `DEVICE` - číslo zařízení (disku), na kterém soubor je
* `SIZE/OFF` - velikost / pozice v souboru
* `NODE` - číslo souboru (unikátní v rámci `DEVICE`)
* `NAME` - jméno souboru


## Terminál jako soubor

Soubor, který má Bash otevřený jako `0u`, `1u` i `2u`, je za normálních
okolností terminál, ve kterém Bash běží.
Zjisti z výstupu výše, který to je.
V našem příkladu je to `/dev/pts/0`, u tebe může být jméno jiné.

Jak už víš, terminál je soubor, do kterého můžeš zapisovat.
Otevři si další okno terminálu a zadej následující příkaz. (Za `/dev/pts/0` doplň „svoje“ jméno terminálu):

```console
$ echo abc > /dev/pts/0
```

Všimni si, že se `abc` objeví ve druhém terminálovém okénku!

Když znáš jméno souboru a víš, jak se do něj dostat (znáš cestu), můžeš do něj zapisovat. 
Soubor pro terminál není zas tolik zvláštní: jakmile znáš jméno, můžeš do něj zapisovat jako do jakéhokoli jiného souboru.

> [node] K čemu to je dobré?
> Svého času takhle administrátoři posílali zprávy dalším lidem,
> co zrovna pracovali na tom samém stroji.
> Ale dnes se to už tolik nepoužívá.
> Jen to ukazuje jak věci fungují – „všechno je soubor“.


### Chybový výstup

Tyto tři soubory, `0`, `1` a `2`, má každý proces otevřené.

`0` je náš starý známý *standardní vstup*.
Když nepřesměrováváš, je to terminál: čte se to co napíšeš na klávesnici.
Ale může to být i jiný soubor – třeba následující `grep` má pod
číslem 0 otevřený soubor `soubory.py`:

```console
grep print < soubory.py
```

`1` je standardní výstup – místo, kam program píše informace,
které chce předat světu.


`2` je ale nové: je to standardní *chybový* výstup
(angl. *standard error stream*, *stderr*), místo,
kam programy píší chybové hlášky.
Často to bývá stejný terminál jako *stdout*, ale přesměrovává se samostatně.

Zkus si třeba zkopírovat neexistující soubor pomocí `cp`.
Dostaneš chybovou hlášku:

```console
$ cp a b
cp: cannot stat a no such file or dir
```

Když přesměruješ standardní výstup do souboru, chybová hláška se přesto objeví
v terminálu. Zkus:

```console
$ cp a b > jiny.txt
cp: cannot stat a no such file or dir
```

Zobáček `>` přesměrovává pouze standardní výstup, zatímco chybový výstup
nechá nepřesměrovaný.

A k čemu je to užitečné? 

Na standardní výstup programy většinou píšou výsledky své práce v nějakém
formátu, který se pak dá automaticky zpracovat. 
Když nastane chyba, program ji ohlásí, ale ohlásí ji na jiném místě, než kam
vypíše výstup, aby nekazil další zpracování.

Když zadáš `ps -A | grep ps`, tak `grep` zpracovává výstup z příkazu `ps`:

```console
$  ps -A | grep ps
    776 ?        00:00:00 psimon
    840 ?        00:00:00 cupsd
   5431 pts/1    00:00:00 ps
```

Když ale uděláš chybu a vynecháš pomlčku před `A`,
tak se chyba vypíše na terminál a `grep` zpracuje jen prázdný soubor:

```console
$ ps -A | grep top
[petr@fedora ~]$ ps A | grep top
error: unsupported option (BSD syntax)
(...)
```


### Přesměrovat všechno

Co kdybys ale přece jen chtěl{{a}} přesměrovat ten druhý, chybový, výstup?
Existuje na to speciální operátor `2>` - tedy přesměrování souboru číslo 2.
```console
$ $ cp a b 2> jiny.txt
```

#### Přesměrování obojího

Můžeš přesměrovat i oba výstupy:

```console
$ ls existuje.txt neexistuje.txt > vystup.txt 2> chyby.txt
```

Když přesměrováváš do různých souborů, tak nezáleží na pořadí `>` a `2>`.

Když ale použiješ dvakrát stejný soubor (např. `> jiny.txt 2> jiny.txt`),
narazíš na problém: v souboru se většinou objeví jen jeden z výsledků.
Když je jeden soubor otevřený pro čtení dvakrát, a zapisuje se do obou zároveň, obvykle „vyhraje“ jen jeden.

Bash má na řešení této situace speciální operátor:

```console
$ ls existuje.txt neexistuje.txt > jiny.txt  2>&1
#                                             ^--- chybový směruje tam, kam první
```

Kdyby v příkazu nebyl `&`, výstup se přesměruje do souboru s názvem `1`.
`&1` ale „odkazuje“ na soubor 1, tedy `jiny.txt`.

Tady už záleží v jakém pořadí se skládají příkazy, protože tohle fungovat nebude:

```
#                                ,-------- 1. přesměruje stderr na stdout, tedy na terminál
#                                |   ,--- 2. přesměruje stdout do souboru
#                                ↓   ↓
$ls existuje.txt neexistuje.txt 2>&1 > jiny.txt
```

Proto *stderr* půjde na terminál a *stdout* do souboru.


### Přesměrování vstupu

Pro úplnost si ukážeme i přesměrování standardního vstupu.

```console
$ grep print < soubor.py
print("Hello")
```


## Zahození výstupu

Zvláštní případ použití je přesměrování některého výstupu do speciálního
souboru, který si nic z toho co se do něj píše, neukládá.
Jmenuje se `/dev/null`.

```console
$ ls existuje.txt neexistuje.txt 2> /dev/null
```

Celý chybový výstup se tak „vyhodí“.

> [note]
> `/dev/null` není ani normální soubor, ani terminál, ani roura.
> Je to další druh speciálního souboru.

Jiný příklad - jsou programy, které píšou do terminálu spoustu výstupu.
Třeba `find`.
Pokud chceš vidět jen problémy, ale ne nalezené soubory, můžeš přesměrovat
standardní výstup do `/dev/null` a v terminálu uvidíš jen chybová hlášení
– tady o tom, že k některým souborům nemáš přístup:

```console
$ find /var/cache > /dev/null
find: … Permision denied
```

Nebo naopak můžeš mít tolik souborů k nimž nemáš přístup,
že se ti ani nebude chtít o tom číst; chceš jen dostat ty ke kterým přístup máš.
Pak si do `/dev/null` přesměruješ chybový výstup:

```console
$ find /var/cache 2> /dev/null
```
