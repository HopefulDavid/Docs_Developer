## Flutter

Používá se pro vývoj mobilních aplikací pro Android a iOS.

Využívá **Dart** jako programovací jazyk.

<details>
<summary><span style="color:#1E90FF;">Instalace</span></summary>

> [!IMPORTANT]
> Flutter používá `Git` pro správu závislostí, takže je potřeba mít nainstalovaný `Git`.

> [!IMPORTANT]
> Flutter vyžaduje nainstalovaný `Android Studio` pro vývoj aplikací pro Android.

<details>
<summary><span style="color:#E95A84;">Windows</span></summary>

1. Stáhnout Flutter SDK z [oficiálních stránek](https://flutter.dev/docs/get-started/install/windows)
2. Rozbalit ZIP soubor do složky, například: `C:\src\flutter`
   > [!IMPORTANT]
   > Cesta nesmí obsahovat mezery nebo speciální znaky
3. Přidat cestu k adresáři `flutter\bin` do proměnného prostředí `PATH`

4. Spuště nyní kontrolu zda je vše správně nastaveno:

    ```bash
    flutter doctor
    ```

5. Příkaz pro vypnutí analyzování:

    ```bash
    flutter config --no-analytics
    ```

> [!TIP]
> Pro kontrolu veškerého nastavení:
>
> ```bash
> flutter config
> ```

<details>
<summary><span style="color:#E95A84;">Android toolchain - develop for Android devices</span></summary>

1. Ujistěte se, že je nainstalován `Android Studio`
2. <img src="../../images/77fb408804c94851a06078aae17e694f.png">
3. <img src="../../images/5d7ee05eacb549d5ada6e1edef7a2e59.png">

</details>

<details>
<summary><span style="color:#E95A84;">Prohlížeč pro vývoj webových aplikací</span></summary>

Pokud chcete používat jiný prohlížeč než **Google Chrome**:

```bash
flutter config --no-web-browser
```

1. Použijte

```bash
flutter run -d web-server
```

2. Otevřete ve vlastním prohlížeči a zadejte adresu `http://localhost:PORT/`

</details>

</details>
</details>

<details>
<summary><span style="color:#1E90FF;">Vytvoření nového projektu</span></summary>

```bash
flutter create project_name
```

Nyní můžete spustit aplikaci:

```bash
cd project_name
flutter run
```

</details>