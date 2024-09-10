## Balíčky

### Umístění

- Globální balíčky:

    - Windows: 

      `C:\Users\<user>\AppData\Roaming\npm\node_modules`

### Záloha

<ol>
<li> 
    
Vytvořit soubor s informacemi o nainstalovaných balíčcích.

- Záloha globálních balíčků

	  ```bash
	  npm list -g --depth=0 > npm_global_packages.txt
	  ```

  - Záloha lokálních balíčků

	  ```bash
	  npm list --depth=0 > npm_local_packages.txt
	  ```
</li>
<li> 
    
Vytvořit .tgz soubory pro balíčky.

- Automaticky

    ```bash
    # Read the file content
    $content = Get-Content -Path 'npm_global_packages.txt'
    
    # Skip the first line
    $content = $content | Select-Object -Skip 1
    
    # For each line in the content
    foreach ($line in $content)
    {
        # Remove unwanted symbols
        $line = $line -replace '[+`-]', ''
    
        # Split the line by '@' to separate the package name and version
        $parts = $line -split '@'
    
        # The first part is the package name
        $packageName = $parts[0].Trim()
    
        # Ignore lines that don't contain a package name or are the names of your text files
        if ($packageName -ne "" -and $packageName -ne "globalpackages.txt" -and $packageName -ne "npm_global_packages.txt")
        {
            # Run npm pack for the package
            npm pack $packageName
        }
    }
    ```
  
    > `'path-to-your-file.txt'`
    >
    > Cesta k souboru s informacemi o balíčcích. 

- Manuálně

    Pro každý balíček vytvoříme zálohu.
    
    ```bash
    
    npm pack <package_name>
    ```

    > `<package_name>`
    >
    > Název balíčku, který chceme zazálohovat.
    >
    > Například: `npm pack sass@1.76.0`
</li>
</ol>

### Obnova

> [!IMPORTANT]
> Při instalaci balíčku z `.tgz` je tento soubor následně automaticky odstraněn.

<ol>
<li>
    
Instalace balíčků z .tgz souborů.

- Automaticky

    ```bash
    # Get all .tgz files in the current directory
    $files = Get-ChildItem -Path .\ -Filter *.tgz
    
    # For each .tgz file
    foreach ($file in $files)
    {
        # Run npm install for the file
        Invoke-Expression -Command "npm install $($file.FullName)"
    }
    ```
  
    > Spustit ve složce s .tgz soubory.

- Manuálně

    ```bash
    npm install <package_path>
    ```

  > Ceta k balíčku, který chceme obnovit.
  >
  > Například: `npm install sass-1.76.0.tgz`
</li>
</ol>