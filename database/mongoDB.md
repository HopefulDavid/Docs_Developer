## Co je MongoDB
= Dokumentová databáze

- NoSQL (typ databáze)

    > [!NOTE]	
    > Nevyužívá tabulkový formát, který je běžný u SQL databází.

- Data ukládá ve formátu zvaném **`BSON`**. (Binární verze formátu `JSON`)
    
    > [!TIP]	
    > Formát `BSON` podporuje více datových typů.
    >
    > Efektivnější při encoding a decoding než `JSON`.
  
## Collections 
  
- Data jsou organizována do **`collections`** 

    > [!NOTE]
    > Jsou ekvivalentem tabulek v SQL.

- Každá tato kolekce obsahuje **`documents`**, což jsou jednotlivé záznamy dat.

    > [!NOTE]
    > Na rozdíl od řádků v tabulce SQL nemusí mít dokumenty v MongoDB stejnou strukturu.
    >
    > To znamená, že různé dokumenty ve stejné kolekci mohou mít různé sady polí.
    >
    > Příklad:
    >
    >```Javascript
    > var document1 = { name: "Peter", age: 30, residence: "Prague" };
    > db.myPeople.insert(document1);
    >
    > var document2 = { name: "Anna", age: 25, occupation: "Engineer" };
    > db.myPeople.insert(document2);
    >```

## Klíčové pojmy

### Dokumenty

Záznamy v MongoDB. 

> [!NOTE]
> Každý dokument je struktura dat podobná JSON.

### Kolekce 

Skupiny dokumentů. 

> [!NOTE]
> Jsou to ekvivalenty tabulek v SQL.

### BSON 

Formát ve kterém jsou data uložena. 

> [!NOTE]
> Je to binární verze JSON.

## Kód

### Vytvořit

- Databázi

    ```Javascript
    use mydb
    ```

- Kolekci

    ```Javascript
    mydb.createCollection('mycollection')
    ```

- Vložit dokument do kolekce

    ```Javascript
    mydb.mycollection.insert({name: 'test'})
    ```

- Vložit více dokumentů do kolekce

    ```Javascript
    mydb.mycollection.insertMany([{name: 'test1'}, {name: 'test2'}])
    ```

- Vytvořit index

  ```Javascript
  mydb.mycollection.createIndex({name: 1})
  ```

    > [!TIP]
    > Index je vytvořen na pole `name`
    >
    > Vzestupný = 1
    >
    > Sestupný = -1
    >
    > Vzestupné a sestupné indexy určují pořadí, ve kterém jsou data v indexu uložena, což může ovlivnit výkon a rychlost dotazů, které vyžadují řazení

- Vytvoření více indexů

  ```Javascript
  mydb.mycollection.createIndexes([{ key: { name: 1 } }, { key: { age: -1 } }])
  ```

### Hledat

- Výpis databází

    ```Javascript
    show dbs
    ```
- Výpis dokumentů

    ```Javascript
    mydb.mycollection.find()
    ```

- Výpis kolekcí

    ```Javascript
    show collections
    ```

- Hledání dokumentu

    ```Javascript
    mydb.mycollection.find({name: 'test'})
    ```

- Hledání dokumentu s určitými poli

    ```Javascript
    mydb.mycollection.find({name: 'test'}, {name: 1})
    ```

- Hledání dokumentu s regulárním výrazem

    ```Javascript
    mydb.mycollection.find({name: {$regex: 'te.*'}})
    ```
### Aktualizovat	

- Aktualizace dokumentu

    ```Javascript
    mydb.mycollection.update({name: 'test'}, {$set: {name: 'newTest'}})
    ```

- Aktualizace více dokumentů

    ```Javascript
    mydb.mycollection.updateMany({}, {$set: {name: 'newTest'}})
    ```

- Aktualizace dokumentu s upsert

    ```Javascript
    mydb.mycollection.update({name: 'test'}, {$set: {name: 'newTest'}}, {upsert: true})
    ```
	
    > [!NOTE]  
    > "upsert" **je kombinací "update" a "insert"**
    > 
    > Aktualizuje existující dokument, nebo pokud dokument neexistuje, vloží nový dokument.

### Smazat

- Smazání databáze

    ```Javascript
    db.dropDatabase()
    ```

- Smazání kolekce

    ```Javascript
    mydb.mycollection.drop()
    ```

- Smazání dokumentu

    ```Javascript
    mydb.mycollection.remove({name: 'test'})
    ```

- Smazání všech dokumentů

    ```Javascript
    mydb.mycollection.remove({})
    ```

### Počet

- Počet dokumentů v kolekci

    ```Javascript
    mydb.mycollection.count()
    ```

- Počet dokumentů odpovídajících určitému dotazu

    ```Javascript
    mydb.mycollection.count({name: 'test'})
    ```

- Počet unikátních hodnot v určitém poli

    ```Javascript
    mydb.mycollection.distinct('name').length
    ```

- Počet dokumentů odpovídajících regulárnímu výrazu

    ```Javascript
    mydb.mycollection.count({name: {$regex: 'te.*'}})
    ```

### Setřídit

- Seřazení dokumentů podle pole

    ```Javascript
    mydb.mycollection.find().sort({name: 1})
    ```

- Seřazení dokumentů podle více polí

    ```Javascript
    mydb.mycollection.find().sort({name: 1, age: -1})
    ```

- Seřazení a omezení počtu dokumentů

    ```Javascript
    mydb.mycollection.find().sort({name: 1}).limit(5)
    ```

- Seřazení a přeskočení dokumentů

    ```Javascript
    mydb.mycollection.find().sort({name: 1}).skip(5)
    ```

## Rady a Tipy

### Povolení autorizace

- MongoDB má vestavěný systém pro správu uživatelů a rolí.

  Pro povolení autorizace upravte konfigurační soubor MongoDB a nastavte `security.authorization` na `enabled`.

    ```bash
    security:
      authorization: "enabled"
    ```

### Využití indexů

- Indexy v MongoDB vytváříte pomocí metody `createIndex()`.

  Například pro vytvoření vzestupného indexu na pole `name` v kolekci `mycollection` použijete následující příkaz:

    ```Javascript
    db.mycollection.createIndex({name: 1})
    ```

### Optimalizace dotazů

- MongoDB poskytuje operátor `explain()`, který vám umožní zjistit, jak databáze vykonává váš dotaz.

  Tímto způsobem můžete identifikovat, které části dotazu je třeba optimalizovat.

    ```Javascript
    db.mycollection.find({name: 'test'}).explain()
    ```

### Správné modelování dat

- MongoDB je dokumentová databáze, která umožňuje velmi flexibilní modelování dat.

  Při návrhu vašeho datového modelu zvažte, jak budou data dotazována a jaké budou pracovní zátěže.

### Škálování

- MongoDB podporuje horizontální škálování pomocí replikačních sad a sharding.

  Pro větší aplikace zvažte použití těchto funkcí pro zlepšení výkonu a dostupnosti.

### Paměť

- MongoDB využívá paměť pro ukládání pracovní sady, což zlepšuje výkon dotazů.

  Ujistěte se, že váš server má dostatek RAM pro vaše pracovní zátěže.

### Šetření prostředky

- Pokud máte dotazy, které se často opakují, zvažte ukládání výsledků těchto dotazů pro pozdější použití.

  To může šetřit výpočetní prostředky a zlepšit výkon vaší aplikace.