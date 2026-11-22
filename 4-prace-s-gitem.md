# 4. Práce s Git a GitHubem – Odevzdávání úkolů přes Pull Requesty

V tomto kurzu se naučíte pracovat s verzovacím systémem **Git** a platformou **GitHub** způsobem, který se běžně používá v profesionálních softwarových týmech.

Všechny úkoly kurzu se budou odevzdávat formou **Pull Requestu (PR)** do oficiálního repozitáře kurzu (podobně jako v [minulých ročnících kurzu](https://github.com/Global-Classes-CZE/robotprogramming/pulls?q=is%3Apr+state%3Aclosed)).

Tento návod vám ukáže, jak vše nastavit a jak se vyhnout nejčastější chybě studentů: **míchání starých úkolů do nových odevzdání**.

---

## 1. Jak funguje model dvou repozitářů (Upstream vs. Origin)

Do oficiálního školního repozitáře **nemáte přímé právo zápisu** (nemůžete tam dělat `git push`). Proto se používá model **Fork & Pull Request**:

```
Centrální repozitář kurzu (UPSTREAM)
        │
        │ 1. Fork na webu GitHubu
        ▼
Váš osobní repozitář na GitHubu (ORIGIN)
        ▲                                │
        │ 4. git push origin ukol-1      │ 2. git clone
        │                                ▼
    Váš počítač (Lokální pracovní složka v VS Code)
```

1. **`upstream`** = Oficiální repozitář kurzu. Odtud si stahujete nová zadání, opravy a knihovny.
2. **`origin`** = Váš osobní repozitář na GitHubu (váš **Fork**). Zde máte plná práva a sem posíláte své vypracované úkoly.

---

## 2. Úvodní nastavení (dělá se jen jednou na začátku kurzu)

### Krok 1: Vytvoření forku na GitHubu
1. Přihlaste se na [github.com](https://github.com).
2. Otevřete odkaz na oficiální repozitář kurzu zadaný vyučujícím.
3. V pravém horním rohu klikněte na tlačítko **Fork**.
4. Ponechte výchozí nastavení a klikněte na **Create fork**.
5. Na vašem profilu vznikne vaše vlastní kopie repozitáře.

### Krok 2: Naklonování vašeho forku do počítače
1. Na stránce vašeho forku klikněte na zelené tlačítko **<> Code** a zkopírujte URL adresu (např. `https://github.com/vase-jmeno/robotprogramming.git`).
2. Otevřete terminál (nebo VS Code: `Ctrl+Shift+P` → *Git: Clone*).
3. Spusťte příkaz pro naklonování:
   ```bash
   git clone https://github.com/vase-jmeno/robotprogramming.git
   cd robotprogramming
   ```

### Krok 3: Nastavení propojení na oficiální repozitář (`upstream`)
Ve složce projektu nastavíme odkaz na původní školní repozitář, abychom z něj mohli stahovat aktualizace:
```bash
git remote add upstream https://github.com/Global-Classes-CZE/robotprogramming.git
```
Ověřte nastavení příkazem:
```bash
git remote -v
```
Měli byste vidět:
- `origin` ukazuje na vaše osobní URL.
- `upstream` ukazuje na oficiální školní URL.

---

## 3. Zlaté pravidlo: Jeden úkol = Jedna samostatná větev

> [!CAUTION]
> **Nejčastější chyba studentů z minulých let:**  
> Pokud student pracuje stále na větvi `main`, nebo větev pro *Úkol 2* založí z větve *Úkol 1*, stane se, že **nový Pull Request obsahuje všechny staré úkoly z minulých týdnů**! Vyučující pak nemůže úkol přehledně zhodnotit.

Řešení je velmi jednoduché a má přesná pravidla:
1. **Na větvi `main` se kód nikdy přímo neupravuje.** Větev `main` slouží jen jako čisté zrcadlo školního repozitáře.
2. **Před každým novým úkolem se `main` zaktualizuje z `upstreamu`.**
3. **Každý úkol se vypracovává v nové vlastní větvi** (např. `ukol-1`, `ukol-2`).

```mermaid
gitGraph
   commit id: "Zadání z upstreamu"
   branch ukol-1
   checkout ukol-1
   commit id: "Kód úkolu 1"
   commit id: "Dokončení úkolu 1"
   checkout main
   merge ukol-1 tag: "PR #1 (obsahuje jen Úkol 1)"
   commit id: "Nové zadání z upstreamu"
   branch ukol-2
   checkout ukol-2
   commit id: "Kód úkolu 2"
   checkout main
   merge ukol-2 tag: "PR #2 (čisté odevzdání jen Úkolu 2!)"
```

---

## 4. Pracovní postup krok za krokem (při každém úkolu)

### Fáze 1: Synchronizace větve `main` (před začátkem práce)
Před zahájením nového úkolu si stáhněte nejnovější stav z oficiálního repozitáře kurzu:

```bash
# 1. Přepněte se do větve main
git checkout main

# 2. Stáhněte nejnovější změny z oficiálního repozitáře
git pull upstream main

# 3. Zaktualizujte také svůj GitHub fork
git push origin main
```

---

### Fáze 2: Založení nové větve pro daný úkol
Nyní vytvořte novou větev. Větev pojmenujte jasně podle čísla úkolu (např. `ukol-1`):

```bash
git checkout -b ukol-1
```
*(Tento příkaz vytvoří větev `ukol-1` a rovnou vás do ní přepne).*

Ve VS Code můžete větev vytvořit také kliknutím na název aktuální větve v levém dolním rohu stavového řádku a volbou *Create new branch...*.

---

### Fáze 3: Vypracování úkolu a uložení (commit)
Nyní pracujete na svém kódu v Pico:ed. Jakmile máte úkol hotový a otestovaný:

```bash
# Zkontrolujte změněné soubory
git status

# Přidejte změněné soubory do commitu
git add .

# Vytvořte commit s výstižnou zprávou
git commit -m "Vypracování úkolu 1: line-following robot"
```

---

### Fáze 4: Odeslání větve na váš GitHub
Odešlete svou novou větev do svého osobního forku na GitHubu:

```bash
git push origin ukol-1
```

---

### Fáze 5: Vytvoření Pull Requestu pro vyučujícího

1. Otevřete v prohlížeči stránku svého forku na GitHubu (`https://github.com/vase-jmeno/robotprogramming`).
2. Nahoře se automaticky objeví žlutý proužek:  
   **`ukol-1 had recent pushes less than a minute ago`** s tlačítkem **Compare & pull request**. Klikněte na něj.
3. **Velmi důležitá kontrola záhlaví (směr PR):**
   - **Base repository:** `Global-Classes-CZE/robotprogramming` | **base:** `main` *(cílový školní repozitář)*
   - **Head repository:** `vase-jmeno/robotprogramming` | **compare:** `ukol-1` *(vaše větev)*
4. **Název Pull Requestu:** Zadejte přesný formát:  
   `[Úkol 1] Jméno Příjmení`
5. Do textového pole popisu můžete uvést případné poznámky k řešení.
6. **Klíčová sebekontrola:** Klikněte dole na záložku **Files changed** (Změněné soubory).
   - > [!TIP]
     > Pokud jste postupovali správně, uvidíte zde **POUZE a JEDINĚ soubory patřící k Úkolu 1**! Žádné staré soubory ani konflikty.
7. Klikněte na zelené tlačítko **Create pull request**. Úkol je úspěšně odevzdán!

---

## 5. Co dělat, když vyučující napíše připomínky k PR?

Pokud vám vyučující v Pull Requestu napíše komentář, že je potřeba něco opravit:
1. **Nezakládejte nový Pull Request!**
2. Zůstaňte v téže větvi na svém počítači:
   ```bash
   git checkout ukol-1
   ```
3. Proveďte požadované opravy v kódu.
4. Změny commitněte a odešlete:
   ```bash
   git add .
   git commit -m "Oprava připomínek vyučujícího"
   git push origin ukol-1
   ```
5. Váš stávající Pull Request na GitHubu se **automaticky sám aktualizuje** o nový commit.

---

## 6. Jak začít další úkol (Úkol 2)?

Až bude zadán další úkol (např. *Úkol 2*), zopakujete celý cyklus:
1. `git checkout main`
2. `git pull upstream main`
3. `git push origin main`
4. `git checkout -b ukol-2`
5. Programujete, commitujete a posíláte PR z větve `ukol-2`.

Díky tomuto postupu budete mít každé odevzdání naprosto čisté, přehledné a bez zbytečných chyb!
