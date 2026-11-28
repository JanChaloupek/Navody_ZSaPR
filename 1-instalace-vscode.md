# 1. Instalace a nastavení Visual Studio Code

Tento průvodce vás provede instalací editoru **Visual Studio Code (VS Code)**, stažením projektu kurzu a jeho přípravou. Většinu práce za vás udělá instalační skript projektu (`setup.bat` / `setup.sh`).

---

## 1. Instalace Visual Studio Code

1. Navštivte oficiální web [code.visualstudio.com/download](https://code.visualstudio.com/download).
2. Stáhněte instalátor pro váš operační systém (**Windows**, **macOS** nebo **Linux**).
3. Spusťte instalátor a dokončete instalaci (ve Windows doporučujeme zaškrtnout volby *„Přidat akci Otevřít pomocí Code do kontextové nabídky“* a *„Přidat do proměnné PATH“*).
4. Po instalaci spusťte VS Code.

---

## 2. Rozšíření VS Code

Rozšíření potřebná pro kurz **nemusíte instalovat ručně** – nainstaluje je instalační skript projektu v [kroku 4](#4-otevření-projektu-ve-vs-code-a-rychlá-příprava-setupbat--setupsh) (Python, Pylance, CircuitPython, Run on Save, PlantUML, kontrola pravopisu s češtinou a další). Jejich seznam je v souboru `.vscode/extensions.json` projektu.

> [!CAUTION]
> **Pozor na záměnu rozšíření CircuitPython!**  
> Kurz používá rozšíření **`CircuitPython v2 Cursor AI`** od autora `wmerkens` (verze **0.3.3**).  
> **NEINSTALUJTE** obecné rozšíření „CircuitPython v2“ (od joedevivo ani jiné s vyšším číslem verze) – s naším prostředím a deskou Pico:ed **nefunguje**! Pokud ho již máte nainstalované, odinstalujte ho.

### Nepovinná rozšíření (skript je neinstaluje)

Hodí se při práci s Gitem a odevzdávání úkolů ([4. Práce s Git a GitHubem](4-prace-s-gitem.md)). Instalují se v panelu **Extensions** (`Ctrl+Shift+X`) vyhledáním podle názvu:

- **GitLens – Git supercharged** (`GitKraken`) – historie změn řádek po řádku přímo v editoru, porovnání commitů a větví. Bezplatná edice *Community* plně postačuje.
- **GitHub Pull Requests** (`GitHub`) – kontrola a správa Pull Requestů přímo z postranního panelu VS Code.

---

## 3. Získání výchozí struktury projektu

Celá připravená struktura projektu je v repozitáři kurzu na GitHubu: programy `code.py` (CircuitPython) a `main.py` (MicroPython), knihovny v `lib/`, `lib_cpy/` a `lib_mpy/`, nástroje `cpy` a `mpy`, instalační skript a podrobné návody ve složce `docs/`. Přehled všech souborů najdete v souboru **`README.md`** projektu.

### Jak projekt získat do počítače:

Máte k dispozici dvě cesty podle toho, zda již ovládáte Git, nebo chcete začít rychle bez něj:

#### Varianta A: Přes Git (doporučený a profesionální postup)
Pokud již pracujete s Git a GitHubem (podrobný návod pro odevzdávání přes Pull Requesty najdete v [4. Práce s Git a GitHubem](4-prace-s-gitem.md)):
1. Otevřete terminál (PowerShell / Bash) a přejděte do složky pro projekty (např. `cd C:\Projekty`).
2. Naklonujte repozitář kurzu:
   ```bash
   git clone https://github.com/Global-Classes-CZE/robot-programming3.git joyCarProjekt
   ```
   *(Pokud již máte vytvořený svůj vlastní fork podle [4. Práce s Git a GitHubem](4-prace-s-gitem.md), naklonujte URL svého forku).*
3. Klonovat lze také přímo z prostředí VS Code: stiskněte zkratku `Ctrl+Shift+P`, vyberte **Git: Clone**, vložte adresu repozitáře a vyberte složku na disku.

#### Varianta B: Ruční stažení ZIP archivu z GitHubu (pro úplné začátečníky)
Pokud zatím Git neovládáte a chcete si nejprve osahat hardware a psaní kódu:
1. Otevřete v prohlížeči oficiální repozitář kurzu na GitHubu (např. [github.com/Global-Classes-CZE/robot-programming3](https://github.com/Global-Classes-CZE/robot-programming3)).
2. V pravé horní části klikněte na zelené tlačítko **`<> Code`**.
3. V rozbalené nabídce zvolte položku **`Download ZIP`**.
4. Stažený soubor ZIP rozbalte na svůj disk (např. do složky `joyCarProjekt`).
5. K nastavení Gitu a odevzdávání úkolů přes Pull Requesty se můžete vrátit kdykoliv později podle [4. Práce s Git a GitHubem](4-prace-s-gitem.md).

---

## 4. Otevření projektu ve VS Code a rychlá příprava (`setup.bat` / `setup.sh`)

1. Ve VS Code zvolte **File** → **Open Folder...** (zkratka `Ctrl+K Ctrl+O`) a vyberte složku projektu (např. `joyCarProjekt`).
2. Spusťte instalační skript:
   - **Windows:** dvojklikem na **`setup.bat`** v kořeni projektu, nebo v terminálu VS Code (`Ctrl+~`) příkazem `.\setup.bat`.
   - **Linux a macOS:** v terminálu VS Code příkazem **`./setup.sh`**. Když hlásí `Permission denied`, spusťte ho jako `bash setup.sh` (stává se, když se projekt rozbalil na Windows nebo leží na flashce či disku s FAT/NTFS).
3. Skript vypisuje kroky `[1/8]` až `[8/8]`:

   | Krok | Co dělá |
   |---|---|
   | 1 | zkontroluje Python 3 (na Windows ho v případě potřeby sám nainstaluje) |
   | 2 | vytvoří ve složce projektu virtuální prostředí **`.venv`** (knihovny patří jen k tomuto projektu) |
   | 3 | nainstaluje do `.venv` knihovny `mpremote` (komunikace s MicroPython deskou), `python-minifier` (zmenšení souborů při nahrávání) a `matplotlib` (graf hodnot) |
   | 4 | zapíše do `.vscode/settings.json` tlačítka panelu a `Run on Save` (nahrávání po `Ctrl+S`) |
   | 5 | najde příkaz `code` (VS Code) |
   | 6 | nainstaluje rozšíření **MicroPython & CircuitPython Panel** |
   | 7 | nainstaluje rozšíření z Marketplace (viz [krok 2](#2-rozšíření-vs-code)) |
   | 8 | vypíše připojené desky (USB disk `CIRCUITPY` i sériové porty) |

4. Na konci musí být **`Instalace je KOMPLETNI!`**. Okno VS Code není potřeba znovu načítat.
5. Pokud skript **právě nainstaloval Python**, zavřete VS Code a otevřete ho znovu – editor si seznam programů načítá jen při spuštění a nový Python by jinak nenašel (nefungovalo by `Ctrl+S` ani tlačítka panelu).
6. Kontrola:
   - v Průzkumníku vidíte složky `.vscode`, `docs`, `lib`, `pc` a soubory `code.py` i `main.py`,
   - v levém svislém pruhu přibyla ikona čipu – postranní panel **MicroPython & CircuitPython Panel** s připojenými deskami a tlačítky pro nejčastější akce (nahrát projekt, spustit nebo restartovat program, konzole, smazat desku).

> ⚠️ **Na Linuxu a macOS je `./setup.sh` povinný.** Nastavení v `.vscode/settings.json` je připravené pro Windows a nástroje spouští příkazem `python`. Na Linuxu a macOS se Python 3 obvykle jmenuje `python3` a příkaz `python` neexistuje – `./setup.sh` nastavení přepíše na `python3`. Bez něj **nefunguje nahrávání po `Ctrl+S`** ani tlačítka panelu (v okně *Output* → *Run On Save* uvidíte chybu `python: command not found`).
>
> Když Python 3 nebo balíček `python3-venv` chybí, `./setup.sh` vypíše příkaz, kterým je nainstaluje (Ubuntu/Debian `apt`, Fedora `dnf`, openSUSE `zypper`, Arch `pacman`, macOS `brew`), a zeptá se **„Nainstalovat teď? [a/N]“**. Po odpovědi `a` ho spustí přes `sudo` – zadejte svoje heslo (při psaní se nezobrazuje).

### Když `setup.bat` / `setup.sh` nejde: ruční postup

U kroku, který selže, skript vypíše `ERROR`, `[CHYBA]` nebo `Upozorneni` s důvodem (při chybě v krocích 1–3 skončí, ostatní kroky doběhnou). Proveďte ručně jen to, co neprošlo, a pak skript spusťte znovu – hotové kroky jen zkontroluje.

> [!TIP]
> Příkazy pište do terminálu VS Code (`Ctrl+~`), který je otevřený ve složce projektu. Na Linuxu a macOS pište `python3` místo `python`.

**A. Python 3 (krok 1)**
- **Windows:** stáhněte instalátor z [python.org/downloads](https://www.python.org/downloads/) a při instalaci **zaškrtněte `Add python.exe to PATH`**. Pak zavřete a znovu otevřete VS Code a ověřte příkazem `python --version`.
  - Když se místo verze otevře Microsoft Store nebo se nic nevypíše, vypněte zástupce: *Nastavení Windows → Aplikace → Upřesnit nastavení aplikací → Aliasy spouštění aplikací* → vypněte `python.exe` a `python3.exe`.
- **Ubuntu / Debian:** `sudo apt install python3 python3-venv`
- **macOS:** `brew install python`

**B. Virtuální prostředí a knihovny (kroky 2 a 3)**
```powershell
# Windows
python -m venv .venv
.venv\Scripts\python -m pip install mpremote python-minifier matplotlib
```
```bash
# Linux a macOS
python3 -m venv .venv
.venv/bin/python -m pip install mpremote python-minifier matplotlib
```
Když vytvoření `.venv` na Linuxu selže s hláškou o `ensurepip`, chybí balíček `python3-venv` (viz bod A). Nepovedenou složku `.venv` před dalším pokusem smažte.

**C. Tlačítka panelu a `Run on Save` (krok 4)**
```powershell
python .vscode/deska.py vscode        # Linux a macOS: python3 .vscode/deska.py vscode
```

**D. Příkaz `code` (krok 5)**

Když skript nenašel příkaz `code`, proveďte ručně body E a F. Na Linuxu a macOS můžete místo toho ve VS Code stisknout `F1` → *Shell Command: Install 'code' command in PATH* a `./setup.sh` spustit znovu.

**E. Rozšíření MicroPython & CircuitPython Panel (krok 6)**
1. Otevřete **Extensions** (`Ctrl+Shift+X`).
2. Nahoře v panelu klikněte na **`…`** (*Views and More Actions*) → **Install from VSIX…** (totéž přes `F1` → *Extensions: Install from VSIX…*).
3. Vyberte soubor **`.vscode/dist/micropython-panel.vsix`** ve složce projektu.

**F. Rozšíření z Marketplace (krok 7)**
1. Otevřete **Extensions** (`Ctrl+Shift+X`) a do vyhledávání napište **`@recommended`**.
2. V části *Workspace Recommendations* klikněte na ikonu **Install Workspace Recommended Extensions** (mrak se šipkou), nebo instalujte jedno po druhém.
3. ⚠️ Pozor na správné rozšíření CircuitPython – viz [krok 2](#2-rozšíření-vs-code).

**G. Kontrola (krok 8)**
```powershell
.\cpy devices          # Linux a macOS: ./cpy.sh devices
```
Vypíše připojené desky s CircuitPythonem i MicroPythonem.

---

Nyní máte připravený editor i kompletní strukturu projektu. V dalším kroku připojíme desku Pico:ed:  
👉 **Pokračujte na: [2. Práce s Pico:ed a CircuitPythonem](2-nastaveni-picoed.md)**
