# Úkoly - Zápis údajů o procesech

Na začátku si vytvořte dočasnou složku, ať si zbytečně neděláte nepořádek v souborovém systému. Přesuňte se do této složky.

Vytvořte složku `root` a složku s názvem vašeho `uživatele` (s tím vám může pomoct proměnná `$USER`).
Po zadání příkazu `tree` by ste měli vidět něco podobného:
```
$ tree
.
├── tux
└── root
```

Příkaz `ps` má velké množství přepínačů, nás ale zajímají přepínače `-e` a `-f`. Spusťte příkaz `ps` s těmito přepínači. V prvním sloupci si můžete všimnout jméno vlastníka procesu. Rozdělte tuto tabulku do dvou souborů, `root_ps.txt`, který bude ve složce `root` a `<jméno uživatele>_ps.txt`, který bude ve složce pro `uživatele`.

Teď by nás zajímalo kolik procesů, měl spuštěných `root` i `uživatel`. Zapište počet procesů na **konec** příslušných souborů. Tyto soubory spojte do jednoho souboru `vsechny_ps.txt`, který sa bude nacházet ve vaší dočasné složce. **Obsah oddelte jedním prázdným řádkem**.

Výslední strom by mal vypadat takhle:
```
$ tree
.
├── tux
│   └── tux.txt
├── root
│   └── root_ps.txt
└── vsechny_ps.txt
```
