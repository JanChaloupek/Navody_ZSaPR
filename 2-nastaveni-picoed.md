# 2. Nastavení Visual Studio Code pro použití s Pico:ed

Tento návod popisuje připojení desky **Pico:ed**, kontrolu a aktualizaci verze **CircuitPythonu**, nastavení automatického nahrávání kódu při uložení (`Run on Save`) a řešení běžných problémů.

---

## 1. Zlaté pravidlo kurzu: Python na PC nespouštíme!

> [!IMPORTANT]
> **Kód běží v hardware, nikoliv na vašem počítači.**  
> Kromě offline testů (které slouží pro ověřování čisté logiky bez robota, viz [JakSeTestuje.md](https://github.com/JanChaloupek/robot-programming3/blob/main/JakSeTestuje.md)) v tomto kurzu **nespouštíte žádný `python.exe` na svém PC**.  
> Veškerý kód se automaticky odesílá do desky Pico:ed a spouští se přímo v jejím procesoru RP2040 pod systémem CircuitPython.

---

## 2. Kontrola a aktualizace firmware CircuitPythonu

Připojte desku Pico:ed k počítači pomocí microUSB kabelu. V Průzkumníku souborů se musí objevit vyměnitelný disk s názvem **`CIRCUITPY`**.

### Jak zjistit verzi CircuitPythonu:
1. Otevřete disk `CIRCUITPY`.
2. Otevřete textový soubor **`boot_out.txt`**.
3. Na prvním řádku uvidíte nainstalovanou verzi, například:
   ```text
   Adafruit CircuitPython 9.2.1 on 2024-10-15; ELECFREAKS Pico:ed with rp2040
   ```
4. **Požadavek:** Pro správné fungování všech knihoven podvozku JoyCar a senzorů potřebujete **minimálně verzi 9** (aktuální stabilní verze je 10.x). Pokud máte starší verzi (např. CircuitPython 7.x nebo 8.x), musíte firmware aktualizovat!

---

### Jak aktualizovat firmware na verzi 9+ (krok za krokem):

1. **Odpojte USB kabel** Pico:edu od počítače.
2. Na zadní straně desky Pico:ed najděte malé bílé tlačítko označené **BOOTSEL**.
3. **Držte tlačítko BOOTSEL stisknuté** a zároveň zasuňte USB kabel do počítače. Po 2 sekundách tlačítko uvolněte.
4. Místo disku `CIRCUITPY` se v počítači objeví disk s názvem **`RPI-RP2`**.
5. Stáhněte si aktuální firmware CircuitPythonu (soubor s příponou `.uf2`) pro desku Pico:ed:
   - 🔗 [Oficiální stažení pro ELECFREAKS Pico:ed](https://circuitpython.org/board/elecfreaks_picoed/) (zvolte verzi 9.x nebo 10.x).
6. Stažený soubor `.uf2` jednoduše **přetáhněte myší (nakopírujte) na disk `RPI-RP2`**.
7. Deska po dokončení zápisu okamžitě sama restartuje a v systému se znovu přihlásí jako disk **`CIRCUITPY`**.
8. Znovu otevřete `boot_out.txt` a ověřte, že je verze 9+.

---

## 3. Konfigurace rozšíření CircuitPython ve VS Code

1. Spusťte VS Code a otevřete váš pracovní adresář (např. `joyCarProjekt`).
2. Vytvořte v kořenu složky soubor `code.py` (obsah může být zatím prázdný).
3. Otevřením `code.py` se aktivuje rozšíření **CircuitPython v2 Cursor AI** (verze 0.3.3).
4. Podívejte se do **dolní modré stavové lišty** (Status Bar). Měli byste vidět položku `<Choose a board>`.
5. Klikněte na ni, do vyhledávacího políčka v horní části napište **`picoed`** a vyberte:  
   `ELECFREAKS:Pico:ed`
6. Tím se stáhnou typové definice specifické pro Pico:ed a editor začne správně napovídat piny a moduly.

### Kontrola cest ke knihovnám v `settings.json`:
Otevřete soubor `.vscode/settings.json` a ujistěte se, že sekce `python.analysis.extraPaths` obsahuje cesty k lokálním knihovnám `./lib` a `./lib_vsc_only`:
```jsonc
"python.analysis.extraPaths": [
    "./lib",
    "./lib_vsc_only"
]
```

---

## 4. Automatické nahrávání kódu při uložení (`Run on Save`)

Při každém stisku `Ctrl+S` ve VS Code rozšíření **Run on Save** automaticky spustí skript `copy.ps1` (pro Windows) nebo `copy.sh` (pro macOS/Linux). Skript zkontroluje soubor `.vscode/.ignoreCopy` a pokud soubor není ignorován, ihned jej nakopíruje na disk `CIRCUITPY`.

### Nastavení konfigurace v `.vscode/settings.json`:

Otevřete `.vscode/settings.json` ve svém projektu a doplňte následující blok podle vašeho operačního systému:

#### Pro Windows:
```json
"emeraldwalk.runonsave": {
    "commands": [
        {
            "match": ".*\\.py",
            "isAsync": true,
            "cmd": "powershell -ExecutionPolicy Bypass -NoProfile -File \"${workspaceFolder}\\.vscode\\copy.ps1\" \"${workspaceFolder}\" \"${relativeFile}\" \".vscode\\.ignoreCopy\""
        }
    ]
}
```

#### Pro macOS / Linux:
```json
"emeraldwalk.runonsave": {
    "commands": [
        {
            "match": ".*\\.py",
            "isAsync": true,
            "cmd": "bash \"${workspaceFolder}/.vscode/copy.sh\" \"${workspaceFolder}\" \"${relativeFile}\" \".vscode/.ignoreCopy\""
        }
    ]
}
```

> [!NOTE]
> Skript `copy.ps1` pro Windows je autorský skript kurzu a je průběžně laděn. Skript `copy.sh` pro Linux a macOS naleznete také v [oficiálním repozitáři šablony](https://github.com/JanChaloupek/vsc_init_circuitPythonProject/blob/main/.vscode/copy.sh).

---

## 5. 💡 Co dělat, když se soubory neukládají na Pico:ed

Pokud po uložení (`Ctrl+S`) kód na robotovi nereaguje, postupujte podle této diagnostiky:

### Krok 1: Kontrola chyb v okně OUTPUT
1. Ve VS Code otevřete okno **OUTPUT** pomocí zkratky `Ctrl+Shift+U` (nebo přes horní menu: *View → Output*).
2. V pravé části okna OUTPUT přepněte rozbalovací filtr na **`Run On Save`**.
3. Přepněte se zpět do `code.py` a stiskněte **`Ctrl+S`**.
4. V okně OUTPUT se okamžitě zobrazí výpis skriptu:
   - Zda našel disk `CIRCUITPY`.
   - Který soubor kopíruje a kam.
   - Případné červené chybové hlášení.

### Krok 2: Zamčený disk (Read-only ve Windows)
Velmi častou příčinou je, že operační systém Windows disk `CIRCUITPY` zamkne proti zápisu kvůli náhlému odpojení nebo přepětí:
- **První pomoc:** Odpojte USB kabel od počítače a po 3 sekundách jej znovu zapojte – disk se ve Windows znovu načte.
- **Pokud to nepomůže – ÚPLNÝ RESTART ROBOTA (Power-Cycle):**
  1. Odpojte USB kabel od počítače.
  2. Vypněte hlavní napájecí přepínač na základní desce JoyCaru.
  3. Znovu zapněte napájení JoyCaru.
  4. Zapojte USB kabel zpět do počítače.

---

## 6. Sériová konzole (REPL)

REPL (Read-Eval-Print Loop) umožňuje sledovat textové výstupy `print()`, zprávy z `log` i chybové výjimky přímo z jedoucího robota:

1. Klikněte v dolní liště VS Code na ikonu **zástrčky sériového portu** (CircuitPython).
2. Vyberte COM port odpovídající vašemu Pico:ed.
3. V terminálu se otevře interaktivní okno CircuitPythonu.
4. **Ovládání:**
   - `Ctrl+C` : Zastaví právě běžící program v robotovi a přejde do příkazového řádku REPL.
   - `Ctrl+D` : Soft reset – znovu spustí program `code.py` od začátku.

---

## 7. 🛠️ Tip: Práce ve VS Code Workspace (více složek najednou)

Pokud chcete mít v levém průzkumníku VS Code zobrazený jak svůj pracovní projekt z disku počítače, tak přímo obsah disku `CIRCUITPY` v robotovi:

1. Otevřete svůj pracovní projekt jako obvykle (`File → Open Folder...`).
2. V horním menu zvolte **File** → **Add Folder to Workspace...**
3. Vyberte připojený disk `CIRCUITPY`.
4. V levém panelu nyní uvidíte obě složky pod sebou.
5. Aby se toto nastavení uchovalo i po restartu VS Code, uložte si ho:  
   **File** → **Save Workspace As...** (např. pod názvem `joyCar.code-workspace`).  
   Příště pak otevíráte přímo tento soubor workspace.

---

👉 **Další kapitola: [3. Úvodní práce s Micro:bitem a Mu Editorem](3-microbit-mu-editor.md)**  
👉 **Návod pro odevzdávání úkolů: [4. Práce s Git a GitHubem](4-prace-s-gitem.md)**
