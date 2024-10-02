## Nuget Packages

- **packages.config**

  Ukládá seznam všech balíčků používaných projektem, **včetně jejich závislostí**.

  Každý balíček je nainstalován do specifické složky projektu (typicky `packages` složka uvnitř řešení).

  > [!NOTE]
  > Zde jsou balíčky uloženy v projektu a zkopírovány z globální složky, což může zpomalovat buildy a zvětšuje velikost repozitářů.
  >
  > Používané před rokem 2017. V každém projektu je samostatná složka s balíčky a soubor `.csproj` obsahuje pouze cesty k těmto balíčkům.

- **PackageReference**

  Spravuje pouze balíčky, které jste **přímo nainstalovali**.

  Závislosti se spravují automaticky a nejsou explicitně uvedeny v souboru `.csproj`.

  Balíčky se nestahují do složky projektu, ale do **globální složky balíčků**.

  > [!NOTE]
  > Používá balíčky přímo z globální složky `global-packages`, což zrychluje build a snižuje nároky na prostor v projektu.
  >
  > Od roku 2017 je výchozí formát ve Visual Studiu. Všechny balíčky jsou spravovány na jednom centrálním místě a projekt využívá jejich globální umístění, což vede k lepší přehlednosti a výkonu.

**Globální složka balíčků**

- Balíčky jsou při použití **PackageReference** vždy načítány přímo ze složky **global-packages** (není nutné je kopírovat do projektu, jak to je u packages.config).
- Umístění složky:
  
  Windows: `%userprofile%\\.nuget\packages`
  
  Mac/Linux: `~/.nuget/packages`
  
  > [!NOTE]
  > Toto výchozí umístění lze upravit přes proměnné prostředí `NUGET_PACKAGES`
