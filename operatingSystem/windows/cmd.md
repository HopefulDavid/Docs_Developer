## Příkazový řádek

Batch skript obvykle obsahuje příponu `.bat` nebo `.cmd`.

### SQL

<details>
<summary><span style="color:#1E90FF;">Spuštění všech sql skriptů ze složky</span></summary>

```bash
for %%G in (*.sql) do sqlcmd /S serverTest /d CT46 -U userName -P password123 -i"%%G"

pause
```

> [!NOTE]
> `for %%G`
>
> Používá se k iteraci přes všechny soubory v adresáři, které odpovídají vzoru v závorce.
>
> `in (*.sql)`
>
> Označuje, že smyčka projde všechny soubory s příponou `.sql` v aktuálním adresáři.
>
> `do sqlcmd`
>
> Při každém průchodu smyčkou se provede příkaz `sqlcmd`, což je příkazový nástroj pro spouštění SQL příkazů na serveru
> Microsoft SQL Server.
>
> `/S serverTest`
>
> Tento parametr určuje název nebo IP adresu SQL serveru, ke kterému se připojuješ.
>
> (V tomto případě je to `serverTest`.)
>
> `/d CT46`
>
> Určuje databázi, ke které se chcete připojit.
>
> (Zde je to `CT46`.)
>
> `-U userName`
>
> Určuje uživatelské jméno pro připojení k SQL serveru.
>
> (Zde je to `userName`.)
>
> `-P password123`
>
> Určuje heslo pro uživatele `userName`.
>
> (Zde je to `password123`.)
>
> `-i "%%G"`
>
> Označuje, že soubor SQL (který je uložen v proměnné `%%G` – každý `.sql` soubor) bude použit jako vstup pro `sqlcmd`.
>
> Tento příkaz tedy vykoná SQL skript v daném souboru.
>
> `pause`, zastaví provedení skriptu a čeká na stisknutí libovolné klávesy.
>
> (To umožňuje uživateli vidět výsledky před tím, než se okno zavře.)

</details>