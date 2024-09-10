## Klávesové zkratky

### Parametry metody

- Informace o parametrech metody

`Ctrl` + `Shift` + `Space`
  
Procházení seznamu:

- Vpřed

  `Ctrl` + `Shift` + `Space`

- Zpět

  `Ctrl` + `Shift` + `P`

## XML komentáře

### Zalomit řádek

- Použijte:
  
	**`<para>&#160;</para>`**

    > [!WARNING]
    > `<para></para>` a `<br/>` nefungují pro zalomení řádku

    Příklad použití:
    
    ```c#
    /// <summary>
    ///     This sentence shows up when the type is hovered
    ///     <para>&#160;</para>
    ///     <para>int PrimaryKey</para>
    ///     <para>&#160;</para>
    ///     <para>virtual Relation Relation</para>
    /// </summary>
    ```

    Pro více informací: [XML zalomení komentáře](https://stackoverflow.com/questions/7279108/how-to-add-a-line-break-in-c-sharp-net-documentation)