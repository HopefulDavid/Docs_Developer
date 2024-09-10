Atributy obsahujá **Metadata**

## Datové anotace
= System.ComponentModel.Annotations (namespace)

Nejvíce používané anotace:

- `[Required]`

  Hodnota je povinná
  
- `[Range]`

  Hodnota v číselném rozsahu

- `[MaxLength]`

  Hodnota s maximální délkou

- `[MinLength]`

  Hodnota s minimální délkou

- `[StringLength]`

  Hodnota s maximální a volitelnou minimální délkou

- `[RegularExpression]`

  Ověření hodnoty z regulárního výrazu

- `[DataType]`

  Specifikuje datový typ pro hodnotu

- `[Display]`

  Název a pořadí hodnoty

### Příklad

- Definice

    ```c#
    public class Author
    {
        [Required(ErrorMessage = "{0} is required")]
        [StringLength(50, MinimumLength = 3,
        ErrorMessage = "First Name should be minimum 3 characters and a maximum of 50 characters")]
        [DataType(DataType.Text)]
        public string FirstName { get; set; }
        
        [Required(ErrorMessage = "{0} is required")]
        [StringLength(50, MinimumLength = 3,
        ErrorMessage = "Last Name should be minimum 3 characters and a maximum of 50 characters")]
        [DataType(DataType.Text)]
        public string LastName { get; set; }
        
        [DataType(DataType.PhoneNumber)]
        [Phone]
        public string PhoneNumber { get; set; }
        
        [DataType(DataType.EmailAddress)]
        [EmailAddress]
        public string Email { get; set; }
    }
    ```

- Použití

    ```c#
    Author author = new Author();
    author.FirstName = "Joydip";
    author.LastName = "";
    author.PhoneNumber = "1234567890";
    author.Email = "joydipkanjilal@yahoo.com";
    
    // Provedení kontroly dat
    ValidationContext context = new ValidationContext(author, null, null);
    List<ValidationResult> validationResults = new List<ValidationResult>();
    bool valid = Validator.TryValidateObject(author, context, validationResults, true);
    if (!valid)
    {
      foreach (ValidationResult validationResult in validationResults)
      {
           Console.WriteLine("{0}", validationResult.ErrorMessage);
      }
    }
    ```

### Vlastní datová anotace
<ol>
<li>
    
Vytvořit třídu a rozšířit ji o třídu `ValidationAttribute`
</li>
<li>
    
Přepsat metodu `IsValid`
</li>
</ol>

- Definice
  
    ```c#
    [AttributeUsage(AttributeTargets.Property, AllowMultiple = false, Inherited = false)]
    public class IsEmptyAttribute : ValidationAttribute
    {
       public override bool IsValid(object value)
       {
       		var inputValue = value as string;
            return !string.IsNullOrEmpty(inputValue);
       }
    }
    ```

- Použití

    ```c#
    [IsEmpty(ErrorMessage = "Should not be null or empty.")]
    public string FirstName { get; set; }
    
    [IsEmpty(ErrorMessage = "Should not be null or empty.")]
    public string LastName { get; set; }
    ```

Použité odkazy [^1]

## FileHelpers
= FileHelpers (namespace)

> [!IMPORTANT]
> Nepodporuje:
> 
> - Záznamy s proměnnou délkou
>   
>   = každý záznam musí mít stejný počet polí
> - Změnu formátu za běhu
>   
>   = každý záznam musí mít stejný formát po celou dobu.

Nejvíce používané atributy:

- Pro třídu:

    - `[DelimitedRecord]`
 
      Záznamy s oddělovači.
      
      Argument: řetězec reprezentující oddělovač pro záznamy.

    - `[FixedLengthRecord]`
      
      Záznamy s pevnou délkou.
 
- Pro pole
 
   - `[FieldTrim]`
      
     Odstranění bílých znaků z hodnoty.
 
     Argument: `TrimMode.Both`, `TrimMode.Left`, `TrimMode.Right`.
 
    - `[FieldOptional]`

      Volitelný sloupec.

      Pokud sloupec v souboru chybí, nebude to považováno za chybu.

    - `[FieldIgnore]`
   
       Ignoruje sloupec při čtení nebo zápisu souboru.
   
    - `[FieldConverter]`
   
      Přiřazení konvertoru.
   
      Konvertor = třída, převádí hodnoty mezi textovou reprezentací v souboru a hodnotou v datech.
   
    - `[FieldOrder]`
   
      Určuje pořadí sloupců pro čtení nebo zápis souboru.

    - `[FieldQuoted]`
   
      Pokud je hodnota v souboru uvedena v uvozovkách.

### Příklad
<ol>
<li> Definice třídy pro záznamy

- CSV soubory
  
	[DelimitedRecord(",")]

- Soubory s pevnou délkou záznamu

  [FixedLengthRecord]
</li>
<li> Přečíst nebo zapsat soubor
    
- Čtení ze souboru

    ```c#
    var engine = new FileHelperEngine<Order>();
    Order[] result = engine.ReadFile("Input.txt");	
    ```
    
- Zápis do souboru

    ```c#
    var engine = new FileHelperEngine<Order>();
    engine.WriteFile("Output.txt", result);
    ```
</li>
</ol>

### Vlastní konvertor
<ol>
<li>Vytvořit třídu a rozšířit ji o třídu `ConverterBase`</li>
<li>Přepsat metody `StringToField` a `FieldToString.`</li>
</ol>

- Definice
  
    ```c#
    public class MyCustomConverter : ConverterBase
    {
        public override object StringToField(string from)
        {
            // Převeďte řetězec na objekt
        }
    
        public override string FieldToString(object fieldValue)
        {
            // Převeďte objekt na řetězec
        }
    }
    ```

- Použití

    ```c#
    [DelimitedRecord(",")]
    public class Order
    {
        [FieldConverter(typeof(MyCustomConverter))]
        public int OrderID;
        // ...
    }
    ```

[^1]: [How to use data annotations in C# | InfoWorld](https://www.infoworld.com/article/3543302/how-to-use-data-annotations-in-c-sharp.html)