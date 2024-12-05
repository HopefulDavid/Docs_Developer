## Balíčky

<details>
<summary><span style="color:#1E90FF;">Globální balíčky</span></summary>

- Umístění windows: C:\Users\<user>\AppData\Roaming\npm\node_modules

  ```bash
  npm root -g
  ```

</details>

<details>
<summary><span style="color:#1E90FF;">Záloha</span></summary>

1. Vytvořit soubor s informacemi o nainstalovaných balíčcích.

    - Záloha globálních balíčků

      ```bash
      npm list -g --depth=0 > npm_global_packages.txt
      ```

    - Záloha lokálních balíčků

      ```bash
      npm list --depth=0 > npm_local_packages.txt
      ```


2. Vytvořit .tgz soubory pro balíčky.

- Možnosti:

    <details>
    <summary><span style="color:#E95A84;">Automaticky</span></summary>

     ```bash
     # Cesta k souboru se seznamem balíčků v aktuální pracovní složce
     $packageListFilePath = Join-Path -Path $PWD.Path -ChildPath 'npm_global_packages.txt'
    
     # Cesta k složce, kde se mají balíčky uložit
     $outputFolder = Join-Path -Path $PWD.Path -ChildPath 'offline_packages'
    
     # Kontrola, zda soubor existuje
     if (!(Test-Path -Path $packageListFilePath)) {
         Write-Error "Soubor npm_global_packages.txt nebyl nalezen v aktuálním adresáři."
         exit
     }
    
     # Vytvoření složky pro offline balíčky, pokud neexistuje
     if (!(Test-Path -Path $outputFolder)) {
         New-Item -ItemType Directory -Path $outputFolder
     }
    
     # Načtení obsahu souboru
     $content = Get-Content -Path $packageListFilePath
    
     # Přeskočení první řádky (pokud je soubor ve formátu, který obsahuje hlavičku)
     $content = $content | Select-Object -Skip 1
    
     # Zpracování každé řádky v souboru
     foreach ($line in $content) {
         # Odstranění nepotřebných symbolů
         $line = $line -replace '[+`-]', ''
    
         # Rozdělení řádky pomocí '@' na jméno balíčku a verzi
         $parts = $line -split '@'
    
         # Jméno balíčku je první část
         $packageName = $parts[0].Trim()
    
         # Získání verze (pokud je specifikována)
         $version = if ($parts.Length -gt 1) { $parts[1].Trim() } else { '' }
    
         # Ignorování prázdných řádků a případně jiných záznamů
         if ($packageName -ne "" -and $packageName -ne "globalpackages.txt" -and $packageName -ne "npm_global_packages.txt") {
    
             # Připravit cestu k balíčku
             $packageDir = Join-Path -Path $outputFolder -ChildPath $packageName
             if (!(Test-Path -Path $packageDir)) {
                 New-Item -ItemType Directory -Path $packageDir
             }
    
             # Pokud je specifikována verze, stáhnout balíček s verzí
             if ($version -ne '') {
                 Write-Output "Stahuji balíček: $packageName@$version"
                 npm pack "$packageName@$version" --pack-destination $packageDir
             } else {
                 Write-Output "Stahuji balíček: $packageName"
                 npm pack $packageName --pack-destination $packageDir
             }
    
             # Pokud balíček obsahuje package.json, stáhnout závislosti
             $packageJsonPath = Join-Path -Path $packageDir -ChildPath 'package.json'
             if (Test-Path -Path $packageJsonPath) {
                 Write-Output "Stahuji závislosti pro balíček: $packageName"
              
                 # Pro každý závislý balíček stáhnout jeho tarball
                 $dependencies = (Get-Content -Path $packageJsonPath | ConvertFrom-Json).dependencies
                 foreach ($dependency in $dependencies.Keys) {
                     Write-Output "Stahuji závislost: $dependency"
                     npm pack $dependency --pack-destination $packageDir
                 }
             }
         }
     }
    
     Write-Output "Všechny balíčky a závislosti byly úspěšně staženy pro offline instalaci."
     ```

    </details>

    <details>
    <summary><span style="color:#E95A84;">Manuálně</span></summary>

  Pro každý balíček vytvoříme zálohu.

      ```bash
    
      npm pack <package_name>
      ```

  > `<package_name>`
  >
  >    Název balíčku, který chceme zazálohovat.
  >
  >    Například: `npm pack sass@1.76.0`

    </details>

</details>

<details>
<summary><span style="color:#1E90FF;">Obnova</span></summary>

> [!IMPORTANT]
> Při instalaci balíčku z `.tgz` je tento soubor následně automaticky odstraněn.

1. Instalace balíčků z .tgz souborů.

- Možnosti:

  <details>
  <summary><span style="color:#E95A84;">Automaticky</span></summary>

    ```bash
    # Cesta k složce s offline balíčky
    $packageFolder = Join-Path -Path $PWD.Path -ChildPath 'offline_packages'
    
    # Kontrola, zda složka existuje
    if (!(Test-Path -Path $packageFolder)) {
        Write-Error "Složka s offline balíčky nebyla nalezena: $packageFolder"
        exit
    }
    
    # Získání všech .tgz souborů v dané složce
    $tgzFiles = Get-ChildItem -Path $packageFolder -Filter *.tgz
    
    if ($tgzFiles.Count -eq 0) {
        Write-Error "Nebyl nalezen žádný .tgz soubor v složce $packageFolder. Zkontrolujte, že máte offline balíčky připravené."
        exit
    }
    
    # Instalace každého .tgz souboru
    foreach ($tgzFile in $tgzFiles) {
        Write-Output "Instaluji balíček: $($tgzFile.Name)"
        
        # Extrahování názvu balíčku z názvu souboru .tgz
        $packageName = [System.IO.Path]::GetFileNameWithoutExtension($tgzFile.Name)
        
        # Vytvoření složky pro instalaci, pokud ještě neexistuje
        $installDir = Join-Path -Path $PWD.Path -ChildPath $packageName
        if (!(Test-Path -Path $installDir)) {
            Write-Output "Vytvářím složku pro instalaci: $installDir"
            New-Item -ItemType Directory -Path $installDir
        }
    
        # Instalace balíčku pomocí .tgz souboru
        try {
            Write-Output "Instaluji balíček z $($tgzFile.FullName)..."
            npm install --prefix $installDir $tgzFile.FullName
            Write-Output "Balíček $packageName byl úspěšně nainstalován."
        }
        catch {
            Write-Error "Chyba při instalaci balíčku $packageName z $($tgzFile.FullName): $_"
            continue
        }
    
        # Pokud balíček obsahuje závislosti (package.json), pokusíme se stáhnout a nainstalovat je offline
        $packageJsonPath = Join-Path -Path $installDir -ChildPath 'node_modules' -ChildPath $packageName -ChildPath 'package.json'
    
        if (Test-Path -Path $packageJsonPath) {
            Write-Output "Balíček $packageName obsahuje závislosti. Stahuji je..."
            
            # Načteme závislosti z package.json
            $dependencies = (Get-Content -Path $packageJsonPath | ConvertFrom-Json).dependencies
            if ($dependencies) {
                foreach ($dependency in $dependencies.Keys) {
                    $dependencyPackagePath = Join-Path -Path $packageFolder -ChildPath "$dependency-*.tgz"
                    
                    if (Test-Path -Path $dependencyPackagePath) {
                        Write-Output "Instaluji závislost: $dependency"
                        npm install --prefix $installDir $dependencyPackagePath
                    } else {
                        Write-Error "Závislost $dependency není k dispozici pro offline instalaci!"
                    }
                }
            }
        }
    }
    
    Write-Output "Všechny balíčky byly úspěšně nainstalovány z offline záloh."
    ```
  </details>

  <details>
  <summary><span style="color:#E95A84;">Manuálně</span></summary>

    - Pro každý balíček obnovíme zálohu.

      ```bash
      npm install <package_path>
      ```

  > Ceta k balíčku, který chceme obnovit.
  >
  > Například: `npm install sass-1.76.0.tgz`

  </details>
  </details>

## Aplikační balíčky

<details>
<summary><span style="color:#1E90FF;">conventional-changelog-cli</span></summary>

Slouží k automatickému generování changelogu na základě commit zpráv.

1. Instalace balíčku.

    ```bash
    npm install -g conventional-changelog-cli
    ```

2. Generování changelogu.

    ```bash
    conventional-changelog -p angular -i CHANGELOG.md -o CHANGELOG.md -s
    ```
   
   | Parameter         | Popis                                                                                   |
   |-------------------|-----------------------------------------------------------------------------------------|
   | `-p` / `--preset` | Přednastavený styl changelogu, např. `angular`, `eslint`, `conventionalcommits`.        |
   | `-i` / `--infile` | Vstupní soubor pro generování changelogu (např. `CHANGELOG.md`).                        |
   | `-o` / `--outfile`| Výstupní soubor pro generování changelogu.                                              |
   | `-r` / `--release-count` | Počet posledních verzí, pro které bude changelog generován.                      |
   | `--context`       | JSON nebo JS soubor obsahující vlastní kontext pro šablonu changelogu.                  |
   | `--pkg`           | Cesta k `package.json`, může být použita pro čtení verzí a dalších údajů.               |
   | `--append`        | Přidá změny na konec souboru místo přepsání celého obsahu.                              |
   | `--same-file`     | Přepíše stejný soubor bez použití dočasného souboru.                                    |
   | `--tag-prefix`    | Přidá prefix k tagům verzí (např. `v`).                                                 |
   | `-n` / `--config` | Vlastní konfigurační soubor, který přizpůsobí generování changelogu.                    |

   > [!TIP]
   > Použití vlastní šablony pro generování changelogu.
   >
   > ```bash
   > conventional-changelog -i index.md -s --config ./changelog-config.js
   > ```
   >
   > [Příklad konfigurace s emoji](../images/changelog-config.js)
   >
   > [Příklad konfigurace bez emoji](../images/changelog-config-noEmojis.js) 

</details>