# Úkoly - Git

## Teoretické otázky

1. Proč je vhodné nastavit uživatelské jméno a e-mail hned po instalaci?
2. Jaký je rozdíl mezi pracovním adresářem, indexem (staging area) a repozitářem?
3. Co se děje při příkazu git add a co při git commit?
4. Vysvětli, co je to commit hash a proč je důležitý.
5. Jak Git uchovává historii změn? Uveď rozdíl oproti klasickému ukládání souborů.
6. Co znamená, že Git je „distribuovaný systém pro správu verzí“?
7. Proč je doporučeno používat větve místo práce přímo v hlavní větvi (main/master)?
8. Jaký je rozdíl mezi git merge a git rebase? Uveď příklad, kdy bys použil/a který. Co se stane s historií, pokud sloučíš větev pomocí merge? A co při rebase?
   Pozn.: Co je rebase jsme se na kurzu neučili, ale jde taky o způsob slučování větví, který je dobré znát. Zkus si o tom dohledat informace.
9. Jaký je účel pull requestu a proč se používá?
10. Co znamená code review a jaký je jeho přínos?
11. K čemu je soubor .gitignore ?
12. Co se stane, pokud přidáš do .gitignore soubor, který už je ve verzovací historii?
13. Proč je vhodné ignorovat logy, dočasné soubory editorů nebo sestavení?
14. Jak se zapisují vzory do .gitignore? Uveď příklady pro:
    - ignorování všech .log souborů
    - ignorování adresáře build

---

## Praktický úkol: „Cestovní průvodce“

Tento úkol se provádí pouze lokálně na virtuálce, není nutné jej odevzdávat.
Pokud ale chceš, odevzdej například soubor který bude obsahovat změny ve
větvi main:
```console
git log -p main
```

### 1. Inicializace

1. Vytvoř repozitář `pruvodce`.
2. Do `README.md` napiš:
```console
Tento repozitáx obsahuje cestovní průvodce po různých městech a zemích.
```
3. Vytvoř commit v `main` s názvem: Inicializace projektu.
4. Od této chvíle se v `main` již přímo nepracuje – vždy se vytvoří větev.

### 2. Průvodce Paříž
1. Vytvoř větev `pridat-pariz`.
2. Přidej soubor `pariz.txt` s průvodcem (zajímavost, jídlo, doprava).
3. Vytvoř commit (Přidán průvodce po Paříži).
4. Sluč větev do `main`.

### 3. Průvodce Londýn
1. Vytvoř větev `pridat-londyn`.
2. První commit: vytvoř soubor `londyn.txt` (zajímavost, jídlo, doprava).
3. Druhý commit: přidej novou sekci do `README.md`:
```console
Obsahuje: Paříž, Londýn
```
4. Tuto větev zatím neslučuj.

#### 👉 Mezitím
1. Vytvoř větev `pariz-update` z větve `main`.
2. Uprav `README.md`, aby obsahoval text:
```console
Obsahuje: Paříž, Francie
```
3. Vytvoř commit (Rozšířen seznam v README.md).
4. Sluč `pariz-update` do `main`.

#### 👉 Nyní
1. Vrať se do větve `pridat-londyn` a zkus sloučit do `main`.
2. Git nahlásí konflikt v `README.md`.
3. Konflikt vyřeš tak, že výsledný řádek bude:
```console
Obsahuje: Paříž, Francie, Londýn
```
4. Commitni a dokonči merge.

### 4. Průvodce Berlín
1. Vytvoř větev `pridat-berlin`.
2. Přidej soubor `berlin.txt` (zajímavost, jídlo, doprava).
3. Vytvoř commit (Přidán průvodce po Berlíně).
4. Sluč větev do `main`.

### 5. Oprav překlep

1. Vytvoř větev: `oprava-readme`
2. Oprav překlep v **README.md**
3. Vytvoř commit (Opravenen překlep v readme)
4. Sluč větev do `main`.


### 6. Ignorování souborů
1. Vytvoř větev `pridat-gitignore`.
2. Přidej `.gitignore` s pravidly:
```console
*.tmp
pracovni/
```
3. Vytvoř commit (Přidán soubor .gitignore).
4. Sluč větev do `main`.


---

## Praktický úkol: „Playground repo“

Postupuj dle návodu `Readme.md` v gitovém repozitáři.
