### Odstranění souborů z verzování

Příkaz aktualizuje změny a všechny dříve sledované soubory, které jsou nyní v `.gitignore`, přestanou být sledovány.

```powershell
git rm -r --cached .
git add .
git commit -m "Refresh .gitignore rules"
```

> [!NOTE]
> Soubor je odstraněn z verzování, ale je ponechání na disku

### Nahrazení Vzdálené Branch z Lokální Branch

<ol>

<li>

Přepnout se na novou branch

```bash
git checkout --orphan latest_branch
```

> [!NOTE]
> `--orphan` znamená, že vytvoří branch bez historie commitů
    
</li>
<li>

Přidat všechny soubory.

```bash
git add -A
```
</li>
<li>

Provedení commitu.

```bash
git commit -am "commit message"
```

> [!TIP]
> `-am` je zkrácený zápis
>
> Je to stejné jako zápis: `--all` `--message "commit message"`
</li>
<li>

Smazat hlavní branch.

> [!WARNING]
> Zjistěte název hlavní větve. (Většinou se jmenuje `master` nebo `main`)

```bash
git branch -D master
```
</li>
<li>

Přejmenovat aktivní branch na branch z předchozího kroku.

> [!WARNING]
> Zjistěte název hlavní větve. (Většinou se jmenuje `master` nebo `main`)

```bash
git branch -m master
```
</li>
<li>

Odeslat změny z pracovního adresáře do centrálního úložiště

```bash
git push -f origin master
```

> [!TIP]
> `-f` (force) = Historie commitů v centrálním úložišti je nahrazena historií z pracovního adresáře
</li>
</ol>