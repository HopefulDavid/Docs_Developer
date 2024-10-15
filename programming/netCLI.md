## .NET CLI (Command Line Interface)

> [!IMPORTAND]
> Je zapotřebí mít nainstalovaný `.NET SDK (Software Development Kit) a .NET Runtime (Framework)`

Po instalaci se vyskytuje zde:

- Windows

  `C:\Program Files\dotnet\`

  > [!TIP]
  > Použijte tento příkaz:
  >
  > ```bash
  > where dotnet
  > ```

- macOS

  `/usr/local/share/dotnet/`

  > [!TIP]
  > Použijte tento příkaz:
  >
  > ```bash
  > which dotnet
  > ```

- Linux

  `/usr/share/dotnet/` nebo `/usr/local/share/dotnet/`

### Záloha globálních nástrojů

1. Zjištění nainstalovaných globálních nástrojů

   ```bash
   dotnet tool list -g
   ```

   > [!IMPORTANT]
   > Zaznamenejte názvy a verze nainstalovaných nástrojů, což usnadní jejich opětovnou instalaci.
   
2. Umístění nástrojů

    Zálohujte celý adresář `tools`.

   - Windows

     `C:\Users\<uživatelské\_jméno>\.dotnet\tools`

   - macOS/Linux
  
     `~/.dotnet/tools`
  
### Obnova globálních nástrojů

1. Obnovení ze zálohy

   Pokud máte zálohovaný adresář `tools`, jednoduše zkopírujte jeho obsah zpět do původního umístění.

   > [!NOTE]
   > Restartovat příkazový řádek nebo terminál, aby se projevily změny.

2. Kontrola instalace

   Po obnovení zkontrolujte, zda jsou nástroje správně nainstalovány:

   ```bash
   dotnet tool list -g
   ```
