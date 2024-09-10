### `fixup!` 

= Nepoužije zprávu z commitu do opravy

```bash
git commit --fixup <hashId>
```

nebo

```bash
git commit -m "fixup! <hashId> notUsedMessage"
```

### `squash!`

= Sloučí zprávu z commitu do opravy

```bash
git commit -m "squash! <hashId> optionalCustomMessage"
```
    
### Příklad

<ol>    
<li>
    
Vytvořit nový commit:

```bash
git commit --fixup <hashId>
```

> [!NOTE]
> `<hashId>` = id commitu na který chcete aplikovat opravu
</li>

<li>

```bash
git rebase -i --autosquash head~<n>
```

> [!NOTE]
> `--autosquash` = setřídí commity pro opravu s označením `fixup!` či `squash!`
>
> `<n>` = počet posledních commitů
</li>
<li>

Otevře se textový editor

Pokud jsme zde provedli změny, tak musíme uložit soubor.

Nakonec zavřít soubor

> [!NOTE]
> Po zavření souboru se začne vykonávat rebase.
</li>
</ol>

Pokud proběhl rebase dokonce, veškeré opravy budou aplikovány.