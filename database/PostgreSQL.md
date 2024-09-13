## PostgreSQL

Podporuje programovací jazyky:

- Python
- Java
- C/C++
- C#
- Node.js
- Go
- Ruby
- Perl
- Tcl

PostgreSQL podporuje v podstatě všechny funkce, které podporují jiné systémy pro správu databází.

### Instalace

#### Výběr verze produktu

<a href="https://www.enterprisedb.com/downloads/postgres-postgresql-downloads"><img src="../images/postgreSQL_Install.png"></a>

#### Spustit instalaci

Po dokončení stahování dvakrát klikněte na stažený soubor a spusťte instalaci:

<img src="../images/postgreSQL_Install_2.png"/>

#### Složka pro instalaci

Můžete zadat umístění PostgreSQL,  vybereme prozatím výchozí volbu:

<img src="../images/postgreSQL_Install_3.png"/>

#### Výběr komponent

<img src="../images/wqiRRNNKOT.png"/>

> [!NOTE]
> Chcete-li používat PostgreSQL, budete muset nainstalovat PostgreSQL Server.
>
> Doporučuji `pgAdmin 4`, který poskytuje uživatelské rozhraní a `Comand Line Tools` pro příkazový řádek.

#### Složka pro uložení dat databáze

Vyberte kam uložit data databáze, použijeme výchozí volbu:

<img src="../images/postgreSQL_Install_4.png"/>

#### Nastavit heslo

Pro přístup do databáze budete muset zvolit heslo. 

<img src="../images/postgreSQL_Install_5.png"/>

#### Port k naslouchání

Můžete nastavit port, na kterém má server naslouchat, použijeme výchozí volbu:

<img src="../images/postgreSQL_Install_6.png"/>


#### Geografické umístění serveru

Vyberte geografické umístění databázového serveru:

<img src="../images/postgreSQL_Install_7.png"/>

#### Kontrola před provedením

<img src="../images/postgreSQL_Install_8.png"/>

Následně stačí dokončit instalaci

### Příkazový řádek

#### Otestovat zda PostgreSQL naslouchá

Otevřít:

<img src="../images/zGRvsmYA6A.png"/>

Připojení:

<img src="../images/t0Vjh1fqzy.png"/>


Nyní byste měli dostat výsledek podobný níže:

<img src="../images/oY0QJRKkL1.png"/>

> [!WARNING]
> **Pokud nevidíte konzoli v angličtině**, musíte udělat tyto změny:
> 
> - Nastavit v `C:\Program Files\PostgreSQL\16\data\postgresql.conf`
>
> 	<img src="../images/G0Loa7KgVA.png"/>
>
> - Nastavit v proměnném prostředí
>
> 	<img src="../images/0qjIRo5xxb.png"/>
>
> Nyní stačí vypnout a zapnout konzoli a změny by se měli projevit


Pro odzkoušení zda jsme se správně připojili stačí zavolat kód níže:

```sql
SELECT version();
```

### Uživatelské rozhraní

Otevřete aplikaci:

<img src="../images/t0m7kk76Jm.png"/>