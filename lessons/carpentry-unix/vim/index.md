# Textový editor vim

Pokud bychom potřebovali nějaký soubor upravit, popř. vytvořit nový soubor s
nějakým obsahem, budeme potřebovat textový editor.

V profesionálním světe linuxové příkazové řádky se pro tyto případy nejčastěji
používá editor `vim`. Důležité je vědět, že editor [Vim](https://www.vim.org/)
se svým ovládáním významně liší od běžných textových editorů, se kterými jste
se doposud nejspíše setkali při psaní a editaci nějakého kódu (např. [Visual
Studio Code](https://code.visualstudio.com/) nebo [Sublime
Text](https://www.sublimetext.com/))

Editor Vim je profesionální nástroj a je nutné věnovat určitý čas naučení se s
ním pracovat. Odměnou nám bude mnohem efektivnější a rychlejší editace
textových souborů (požadované operace lze vykonat mnohem rychleji za použití
menšího počtu úhozů). Výhody vznikají pouze při psaní 10 prsty bez sledování
klávesnice.

Běžné textové editory obsahují jediný mód použití, a to režim vkládání textu
(zmáčknutá posloupnost písmen daný text napíše do okna editoru). O pohyb
kurzoru se v běžných editorech starají kurzorové šipky, navigační blok
<kbd>Home</kbd>, <kbd>End</kbd>, <kbd>PageUP</kbd>, <kbd>PageDown</kbd>, popř.
ještě s klávesou <kbd>Ctrl</kbd>. Mnoho činností lze vykonat pomocí myši.

Editor Vim vznikl jako následovník staršího editoru Vi, který se používal na
UNIXových systémech vybavených monitorem. Klávesnice u terminálů tehdy běžně
neměly kurzorové šipky ani navigační klávesy. Proto vznikl editor, který má
oddělené režimy vkládání textu od režimu pohybu kurzoru a manipulace s textem.

U vimu rozlišujeme 3 hlavní režimy práce:

* Editační mód (Normal mode)
    * Slouží k pohybu kurzoru, přesouvání částí textu
    * V tomto režimu není možné psát text
    * Výchozí mód při spuštění Vimu
    * Vstup do editačního módu: klávesa <kbd>Esc</kbd>
* INSERT mód
    * Slouží ke vkládání znaků do souboru
    * Vstup do INSERT módu: klávesa <kbd>i</kbd>
    * Ukončení INSERT módu: klávesa <kbd>Esc</kbd>
* Příkazový mód
    * Vim zobrazí vlastní příkazovou řádku, kam je možné napsat složitější
      příkaz
    * Vstup do příkazového módu: klávesa <kbd>:</kbd>
    * Ukončení příkazového módu: klávesa <kbd>Esc</kbd>

## Jak to spustím a jak to vypnu

Editor Vim spustíme příkazem `vim`. Zobrazí se nám "Welcome screen", kde si
můžeme povšimnout dobré rady, jak editor vlastně ukončit. Editor zavřeme
vstupem do příkazového módu pomocí dvojtečky <kbd>:</kbd> následované příkazem
<kbd>q</kbd> a <kbd>Enter</kbd>.

Pokud editor není nainstalovaný, spusť následující příkaz k jeho instalaci:

```console
$ sudo dnf install vim -y
```
Následně budeš vyzvána k zadání hesla, napiš jej do příkazové řádky a stiskni
<kbd>Enter</kbd>. Neboj se, že se heslo nezobrazuje.

Vyzkoušej si několikrát otevřít a bezpečně zavřít prázdný editor Vim.

```console
$ vim
```

```console
  1                                                        
~                                                          
~                                                          
~                    VIM - Vi IMproved                     
~                                                          
~                     version 8.2.3512                     
~                 by Bram Moolenaar et al.                 
~            Modified by <bugzilla@redhat.com>             
~       Vim is open source and freely distributable        
~                                                          
~              Help poor children in Uganda!               
~      type  :help iccf<Enter>       for information       
~                                                          
~      type  :q<Enter>               to exit               
~      type  :help<Enter>  or  <F1>  for on-line help      
~      type  :help version8<Enter>   for version info      
~                                                          
~                                                          
utf-8 unix  [No Name]                              0/1   1
```

Pokud chceme v editoru něco napsat, zmáčkneme klávesu <kbd>i</kbd>, která nás
přepne do INSERT módu. V tu chvíli klávesy dělají to, co od nich očekáváme -
text se zobrazuje v okně editoru. Znak tilda `~` zde znamená prázdný řádek.

```console
  1 Ahoj vime!                                             
~                                                          
~                                                          
~                                                          
~                                                          
~                                                          
~                                                          
~                                                          
~                                                          
~                                                          
~                                                          
~                                                          
~                                                          
~                                                          
~                                                          
~                                                          
~                                                          
~                                                          
utf-8 unix  [No Name] +                            1/1  11 
-- INSERT --                                               
```

Do editoru napiš pár řádek textu:
{{ figure(
  img=static('vim.png'),
  alt='Editor vim s otevřeným souborem',
) }}

Pokud jsme něco napsali, ale text nechceme ukládat do souboru, musíme Vim
ukončit příkazem `:q!`, abychom dali najevo, že opravdu nechceme soubor
ukládat.

```console
  1 Ahoj vime!                                             
~                                                          
~                                                          
~                                                          
~                                                          
~                                                          
~                                                          
~                                                          
~                                                          
~                                                          
~                                                          
~                                                          
~                                                          
~                                                          
~                                                          
~                                                          
~                                                          
~                                                          
utf-8 unix  [No Name] +                            1/1  10 
:q!
```

V opačném případě musíme soubor uložit příkazem `:w <název souboru>`.

```console
  1 Ahoj vime!                                             
~                                                          
~                                                          
~                                                          
~                                                          
~                                                          
~                                                          
~                                                          
~                                                          
~                                                          
~                                                          
~                                                          
~                                                          
~                                                          
~                                                          
~                                                          
~                                                          
~                                                          
utf-8 unix  [No Name] +                            1/1  10 
:w pozdrav.txt
```

Po ukončení editoru pomocí `:q` si můžeme obsah souboru vypsat na terminál

```console
$ cat pozdrav.txt
Ahoj vime!
```

Námi vytvořený soubor si můžeme opět otevřít ve Vimu tak, že název souboru
zadáme jako parametr. Stejně můžeme otevřít ve Vimu i neexistující soubor a
editor nám ho při uložení souboru vytvoří.

```console
$ vim pozdrav.txt
```

Příkazy, které už umíme jako `:w` a `:q` je možné i zkombinovat do jednoho
`:wq`.

## Další funkce Vimu

Vyhledávání zapneme klávesou lomítko <kbd>/</kbd> v editačním módu a napíšeme
text, který chceme v souboru vyhledat. Na další výskyt vyhledávaného řetězce se
přesuneme pomocí <kbd>n</kbd> a na předchozí pomocí <kbd>N</kbd>. Toto funguje
stejně jako v programech `less` a `man`.

Vim je profesionální editor pro editaci programů a konfiguračních souborů. Je
velmi ergonomický, protože při jeho používání není nutné, aby prsty opustily
prostřední řadu klávesnice. Není nutné používat kurzorové šipky, navigační blok
nebo myš. Pohyb kurzoru a editace existujícího textu se provádí v editačním
módu (Normal mode).

Pokud ti editor Vim přijde děsivý, je důležité vědět, že po tobě nikdo
nevyžaduje, abys ho používala výlučně. Pro dobrou znalost práce v linuxové
příkazové řádce je však velmi vhodné znát alespoň minimum editoru Vim. Je
důležité znát alespoň:

* Otevřít soubor ve Vimu: `$ vim <název souboru>`
* Vyhledat text v souboru: <kbd>/</kbd>
* Upravit slovo nebo řádek v souboru: INSERT mód zapneme klávesou <kbd>i</kbd>
* Ukončit Vim: ukončíme INSERT mód pomocí <kbd>Esc</kbd> a uložíme a ukončíme
  práci pomocí `:wq`

Pro zájemce doporučuji vestavěný tutoriál

```console
$ vimtutor
```

Pokud tě editor Vim zaujme a naučíš se s ním pracovat, odměnou ti bude
mnohem vyšší rychlost úprav textových souborů, zdravější ergonomie práce na
klávesnici a doživotní závislost na vimovském způsobu ovládání textového
editoru 😄.
