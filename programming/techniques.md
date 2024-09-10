## Vývojové metodiky

Techniky vývoje softwaru jsou postupy, které určují, jakým způsobem se vyvíjí software.

### Agilní metodika (Scrum)

- Zaměřuje se na spolupráci, zákaznickou spokojenost a schopnost reagovat na změny.

- V praxi tým pracuje v krátkých iteracích zvaných `sprinty`, které trvají obvykle **2-4 týdny**. 

    > [!NOTE]
    > Na konci každého sprintu tým prezentuje hotové funkce zákazníkovi a získává zpětnou vazbu.

> [!WARNING]
> Není vhodná pro projekty, které vyžadují pevný plán a jasně definované výstupy.
    
<ol>
<li>
      
Plánování sprintu (Sprint Planning)

Týmová schůzka na začátku sprintu, která se koná jednou.

Výběr úkolů (z backlogu) pro daný sprint k provedení.

Diskutování o tom, jak budou tyto úkoly provedeny.
</li>
<li>
      
Vývoj

Každodenní práce na úkolech, které byly vybrány během plánování sprintu.

Každodenní týmová schůzka zvaná: `Daily Scrum`, kde se diskutuje o pokroku a případných překážkách na úkolech.

Testování je součástí této sekce vývoje. 

> [!NOTE]
> Jakmile je úkol nebo funkce vyvinuta, je ihned testována, aby se zajistilo, že funguje správně a splňuje požadavky.

> [!TIP]
> Toto průběžné testování umožňuje rychlé odhalení a opravu chyb.
</li>
<li>
      
Revize sprintu (Sprint Review)

Týmová schůzka na konci sprintu, která se koná jednou.

Prezentuje se práce zákazníkovi a získává se zpětná vazba.

> [!TIP]
> Tato schůzka je také příležitostí k diskusi o tom, co se v sprintu povedlo a co ne.
</li>
<li> 
      
Retrospektiva sprintu (Sprint Retrospective)

Týmová schůzka obvykle hned po revizi sprintu.

Diskutuje se o tom, co se v průběhu sprintu povedlo, co se nepovedlo a jak se mohou věci zlepšit v dalším sprintu.
</li>
</ol>

### Vodopádová metodika

Každá fáze musí být dokončena, než může začít další.

> [!WARNING]
> Délka každé fáze závisí na velikosti a složitosti projektu, počtu lidí v týmu a mnoha dalších faktorech.

<ol>
<li>
Analýza požadavků

Na začátku projektu se shromažďují a analyzují požadavky.

> [!NOTE]
> Toto zahrnuje porozumění potřebám zákazníka a definování, co bude systém dělat.
</li>
<li>
    
Návrh

Vytváří se podrobný plán toho, jak bude systém fungovat a jak bude vypadat.
</li>
<li>

Implementace

Návrh se převede na zdrojový kód. 

Programátoři píší kód, který realizuje návrh systému.
</li>
<li> 

Testování

Kontroluje se, zda systém splňuje požadavky definované v první fázi a zda neobsahuje chyby.
</li>
<li> 
    
Nasazení

Jakmile je systém otestován a schválen, je nasazen do produkčního prostředí.
</li>
<li>
    
Údržba

Sleduje se výkon systému, opravují se chyby a přidávají se nové funkce podle potřeb zákazníka.
</li>
</ol>

### Kanban

Vizuální systém řízení práce, který se zaměřuje na dokončení úkolů.

> [!NOTE]
> Zaměřuje se na průběžnou dodávku a minimalizaci času stráveného na úkolech.

> [!WARNING]
> Není vhodný pro projekty, které vyžadují pevné plány a termíny

<ol start="1">
<li>Definování úkolů

Na začátku se vytvoří seznam úkolů, které je třeba dokončit. 

> [!TIP]
> Tyto úkoly se zapisují na karty, které se umístí na Kanban tabuli.
</li>
<li>Vizualizace práce

Kanban tabule je rozdělena na několik sloupců, které reprezentují různé stavy úkolu. 

> [!TIP]
> Například: `Backlog`, `Todo` , `Done`, atd...

Karty s úkoly se přesouvají mezi těmito sloupci podle toho, v jakém stavu se nacházejí.
</li>
<li> Práce na úkolech

Tým začne pracovat na úkolech, začínajíc u těch, které jsou nejvíce prioritní. 

> [!NOTE]
> Jakmile je úkol dokončen, karta se přesune do dalšího sloupce.
> 
> Například sloupec: `Done`
</li>
<li>Omezení práce v průběhu (Work in Progress, WIP)

Kanban klade důraz na omezení množství práce, která se může dělat současně. 

> [!NOTE]
> Zvyšuje se efektivita a snižuje se doba, kterou úkol stráví v systému.
</li>
<li>Průběžné zlepšování

Tým pravidelně hodnotí svůj proces a hledá způsoby, jak ho zlepšit. 

> [!TIP]
> To může zahrnovat změnu počtu úkolů, prioratizaci úkolů atd...
</li>
</ol>

## Rychlé prototypování

Proces pro vytvoření funkčního modelu projektu co nejrychleji, aby bylo možné testovat a iterovat nápady.

> [!NOTE]
> V kontextu Unity, to znamená vytvoření základní verzi hry nebo aplikace, která zahrnuje pouze klíčové mechaniky a funkce.

> [!NOTE]
> Rychlá iterace 
> 
> - Rychle testovat a provádět nápady. 
> 
> - Pokud vytvoříte prototyp, zkuste ho co nejdříve otestovat a získat zpětnou vazbu. 
> 
> 	Poté můžete na základě této zpětné vazby upravit a vylepšit svůj prototyp.
 
> [!IMPORTANT]
> **Cílem je vytvořit funkční model** vašeho projektu, **ne dokonalý produkt**. 
> 
> Nebojte se udělat kompromisy v kvalitě, pokud to znamená, že můžete rychleji testovat a iterovat své nápady.

### Postup

<ol start="1">
<li>Definice svého konceptu

Než se začne s prototypováním, měli byste mít jasnou představu o tom, co chcete vytvořit. 

> [!TIP]
> To může zahrnovat definování klíčových mechanik, funkcí a cílů vašeho projektu.
</li>
<li>Vytvořit základní scénu v Unity

> [!TIP]
> Tato scéna bude sloužit jako základ pro váš prototyp.
</li>
<li> Přidat základní objekty

Přidejte do scény základní objekty, jako jsou krychle, koule a válce, které můžete použít k reprezentaci různých prvků ve vaší hře.
</li>
<li>Přidejte mechaniky a funkce

Použijte skriptování a vestavěné nástroje Unity k přidání mechanik a funkcí do vašeho prototypu.
</li>
<li>Testujte a iterujte

Jakmile máte základní prototyp, začněte ho testovat. 

> [!NOTE]
> Získejte zpětnou vazbu od ostatních a na základě této zpětné vazby upravte a vylepšujte svůj prototyp.
</li>
<li>Opakujte proces

Po provedení změn na svém prototypu ho znovu otestujte a pokračujte v tomto cyklu, dokud nejste spokojeni s výsledkem.

> [!TIP]
> Rychlé prototypování je iterativní proces.
</li>
</ol>

## Pojmenování BEM

BEM = "Block Element Modifier"

Metodika pro pojmenování tříd v `HTML` a `CSS`. 

> [!NOTE]
> Pomáhá udržet váš kód organizovaný a snadno pochopitelný, a to i pro ostatní vývojáře, kteří se na váš kód podívají.

Příklad:

```html
<div class="block"> <!-- Block -->
  <div class="block__element"> <!-- Element -->
  </div>
  <div class="block__element--modifier"> <!-- Element with modifier -->
  </div>
</div>
```

```css
.block { ... }
.block__element { ... }
.block__element--modifier { ... }
```

### Block
    
Jedná se o samostatnou entitu, která má smysl sama o sobě. 

Například: `header`, `container`, `menu`, `checkbox`, atd.

### Element

Část bloku, která nemá samostatný význam.

Je semanticky vázána na svůj blok. 

Například: `menu item`, `list item`, `checkbox caption`, atd.

### Modifier

Varianta bloku nebo prvku, která mění vzhled nebo chování. 

Například: `disabled`, `highlighted`, `checked`, atd.

Syntax BEM je poté následující:

- Názvy bloků a elementů jsou odděleny dvěma podtržítky: `__`

- Názvy modifikátorů jsou odděleny dvěma pomlčkami: `--`

## Základy pojmenování při vývoji

### Jasné a popisné názvy
 
  Názvy proměnných, funkcí, tříd atd. by měly být dostatečně popisné, aby bylo jasné, co dělají nebo co reprezentují. 

  Například: 
 
  Místo: `p` 

  **použijte:** `product` 

  místo: `calc` 
 
  **použijte:** `calculateAverage`.

  > [!TIP]
  > Vyhněte se používání zkratek a akronymů.

### Boolovské proměnné

  Boolovské proměnné by měly začínat předponou jako: `is`, `has`, `can` atd., které naznačují, že hodnota může být pravdivá nebo nepravdivá. 

  Například: 
 
  `isAvailable`, `hasPermission`, `canExecute`.

- Názvy funkcí

  Funkce by měly začínat slovesem, které popisuje, co funkce dělá. 

  Například: 
 
  `getUserName()`, `calculateTotalPrice()`, `printReport()`.

- Konzistentní názvosloví

  Pokud se rozhodnete pro určitý styl názvosloví, buďte konzistentní v jeho používání po celém kódu. 

  Například: 
 
  Pokud používáte `camelCase` pro názvy proměnných, používejte je všude.

### Jednotné názvy pro stejné typy proměnných
 
  Pokud máte více polí.

  Například:

  `firstArray`, `secondArray`.

### Množné čísla (plurál) pro kolekce

  Pokud proměnná reprezentuje kolekci objektů, použijte množné číslo. 

  Například: 
 
  `users`, `products`, `items`.

### Konstanty pro "magické" hodnoty

  Pokud kód obsahuje "magické" hodnoty, které nejsou okamžitě zřejmé, zvažte jejich nahrazení pojmenovanými konstantami. 
 
  Například: 

  místo: `if (status == 1)` 

  **použijte:** `if (status == STATUS_ACTIVE)`.