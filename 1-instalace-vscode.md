# 1. Instalace a nastavení Visual Studio Code

Tento průvodce vás krok za krokem provede instalací editoru **Visual Studio Code (VS Code)**, výběrem správných rozšíření pro náš kurz a přípravou pracovního adresáře.

---

## 1. Instalace Visual Studio Code

1. Navštivte oficiální web [code.visualstudio.com/download](https://code.visualstudio.com/download).
2. Stáhněte instalátor pro váš operační systém (**Windows**, **macOS** nebo **Linux**).
3. Spusťte instalátor a dokončete instalaci (ve Windows doporučujeme zaškrtnout volby *„Přidat akci Otevřít pomocí Code do kontextové nabídky“* a *„Přidat do proměnné PATH“*).
4. Po instalaci spusťte VS Code.

---

## 2. Instalace potřebných rozšíření

Rozšíření instalujete kliknutím na ikonu **Extensions** (čtverce na levé liště, případně zkratkou `Ctrl+Shift+X`) a vyhledáním podle názvu.

### Povinná rozšíření:

1. **Python**
   - Základní podpora pro jazyk Python (zvýrazňování syntaxe, linting, ladění).
   - *Název:* `Python`
   - *Autor:* `Microsoft` (součástí je i jazykový server `Pylance`)

2. ⚠️ **CircuitPython v2 Cursor AI** *(VELMI DŮLEŽITÉ!)*
   - Rozšíření zajišťující práci s CircuitPythonem na desce Pico:ed a přístup ke knihovnám.
   - *Název:* `CircuitPython v2 Cursor AI`
   - *Autor:* `wmerkens` (vyžadována verze **0.3.3**)
   - > [!CAUTION]
     > **Pozor na záměnu rozšíření!**  
     > Ujistěte se, že instalujete přesně rozšíření **`CircuitPython v2 Cursor AI`** od autora `wmerkens`.  
     > **NEINSTALUJTE** obecné rozšíření „CircuitPython v2“ (od joedevivo ani jiné s vyšším číslem verze) – s naším prostředím a deskou Pico:ed **nefunguje**! Pokud ho již máte nainstalované, odinstalujte ho.

3. **Run on Save**
   - Automaticky spouští skript při každém stisku `Ctrl+S` (uložení souboru). Slouží k bleskovému zkopírování změněného souboru do Pico:edu.
   - *Název:* `Run on Save`
   - *Autor:* `EmeraldWalk`

4. **PlantUML**
   - Umožňuje přímo v editoru prohlížet a generovat UML diagramy tříd, které budeme v kurzu kreslit pro návrh architektury robota.
   - *Název:* `PlantUML`
   - *Autor:* `jebbs`

---

### Doporučená rozšíření (usnadní vám práci):

1. **GitLens – Git supercharged**
   - Zobrazuje historii změn řádek po řádku přímo v editoru, porovnává commity a větve.
   - *Autor:* `GitKraken` (bezplatná edice *Community* plně postačuje).

2. **GitHub Pull Requests**
   - Umožňuje kontrolovat a spravovat Pull Requesty přímo z postranního panelu VS Code.
   - *Autor:* `GitHub`

3. **Output Colorizer**
   - Barevně zvýrazňuje text v okně OUTPUT a v terminálu, což pomáhá v rychlé orientaci při ladění chyb.
   - *Autor:* `IBM`

4. **MagicPython**
   - Pokročilé gramatické zvýrazňování syntaxe Pythonu.
   - *Autor:* `MagicStack Inc.`

---

## 3. Získání výchozí struktury projektu

Celá připravená výchozí struktura projektu je součástí repozitáře kurzu na GitHubu. Nemusíte nic ručně konfigurovat – projekt už přímo obsahuje:
- **`.vscode/`** – připravená konfigurace editoru, doporučená rozšíření (`extensions.json`), pravidla ignorování souborů (`.ignoreCopy`) a nahrávací skripty:
  - `copy.ps1` (autorský skript mentora kurzu Jana Chaloupka pro Windows)
  - `copy.sh` (skript studenta Robina Bortlíka upravený Janem Chaloupkem pro macOS a Linux)
- **`_stubs/`** – interní složka s typovými definicemi a fake moduly CircuitPythonu (`board`, `busio`, `digitalio`, `picoed`, `neopixel`...). Podtržítko v názvu značí, že jde o interní knihovny pro editor a offline unit testy na PC, které se nekopírují do robota. Plně nahrazuje dřívější složku `lib_vsc_only/`.
- **`lib/`** – složka pro ovladače a knihovny hardware JoyCaru.
- **`pyrightconfig.json`** – konfigurace analyzátoru Pylance/Pyright pro přesné našeptávání a typovou kontrolu bez falešných chybových hlášení.
- **`code.py`** – hlavní vstupní soubor programu běžící přímo v procesoru robota.
- **`.gitignore`** – pravidla verzování zamezující nahrávání mezipaměti a dočasných souborů do Gitu.

---

### Jak projekt získat do počítače:

Máte k dispozici dvě cesty podle toho, zda již ovládáte Git, nebo chcete začít rychle bez něj:

#### Varianta A: Přes Git (doporučený a profesionální postup)
Pokud již pracujete s Git a GitHubem (podrobný návod pro odevzdávání přes Pull Requesty najdete v [Kapitole 4](4-prace-s-gitem.md)):
1. Otevřete terminál (PowerShell / Bash) a přejděte do složky pro projekty (např. `cd C:\Projekty`).
2. Naklonujte repozitář kurzu:
   ```bash
   git clone https://github.com/Global-Classes-CZE/robotprogramming.git joyCarProjekt
   ```
   *(Pokud již máte vytvořený svůj vlastní fork podle [Kapitoly 4](4-prace-s-gitem.md), naklonujte URL svého forku).*
3. Klonovat lze také přímo z prostředí VS Code: stiskněte zkratku `Ctrl+Shift+P`, vyberte **Git: Clone**, vložte adresu repozitáře a vyberte složku na disku.

#### Varianta B: Ruční stažení ZIP archivu z GitHubu (pro úplné začátečníky)
Pokud zatím Git neovládáte a chcete si nejprve osahat hardware a psaní kódu:
1. Otevřete v prohlížeči oficiální repozitář kurzu na GitHubu (např. [github.com/Global-Classes-CZE/robotprogramming](https://github.com/Global-Classes-CZE/robotprogramming)).
2. V pravé horní části klikněte na zelené tlačítko **`<> Code`**.
3. V rozbalené nabídce zvolte položku **`Download ZIP`**.
4. Stažený soubor ZIP rozbalte na svůj disk (např. do složky `joyCarProjekt`).
5. K nastavení Gitu a odevzdávání úkolů přes Pull Requesty se můžete vrátit kdykoliv později podle [4. Práce s Git a GitHubem](4-prace-s-gitem.md).

---

## 4. Otevření projektu ve VS Code

1. Spusťte VS Code.
2. V horním menu zvolte **File** → **Open Folder...** (nebo stiskněte zkratku `Ctrl+K Ctrl+O`).
3. Vyberte složku projektu (např. `joyCarProjekt`).
4. VS Code automaticky detekuje soubor `.vscode/extensions.json`. Pokud se v pravém dolním rohu zobrazí výzva *„Do you want to install the recommended extensions?“*, potvrďte kliknutím na **Install**.
5. Zkontrolujte, zda v levém panelu Průzkumníka vidíte složky `.vscode`, `_stubs`, `lib` a soubory `pyrightconfig.json` i `code.py`.

Nyní máte připravený editor i kompletní strukturu projektu. V dalším kroku připojíme desku Pico:ed a nastavíme automatické nahrávání:  
👉 **Pokračujte na: [2. Práce s Pico:ed a CircuitPythonem](2-nastaveni-picoed.md)**
