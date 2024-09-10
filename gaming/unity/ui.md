## UI

Původní systém pro vytváření uživatelského rozhraní v Unity.

### Tlačítko (Button)

#### Rozsah detekce kliknutí (dle průhlednosti obrázku)

 `alphaHitTestMinimumThreshold` je používána u komponenty `Image`
 
Určuje minimální prahovou hodnotu alfa (průhlednosti), při které bude kliknutí na tento obrázek zaregistrováno. 

Nabývá rozsah hodnoty (0 až 1)

- Hodnota `0` znamená, že kliknutí bude zaregistrováno i na úplně průhledných částech obrázku.

-  Hodnota `1` znamená, že kliknutí bude zaregistrováno pouze na zcela neprůhledných částech obrázku.

 Například, pokud nastavíme `alphaHitTestMinimumThreshold` na `0.5`, kliknutí bude zaregistrováno pouze na částech obrázku, které mají alfa hodnotu alespoň 0.5 (tedy nejsou příliš průhledné).

Příklad použití: 

```c#
using UnityEngine;
using System.Collections;
using UnityEngine.UI; // Required when Using UI elements.

public class ExampleClass : MonoBehaviour
{
    public Image theButton;

    // Use this for initialization
    void Start()
    {
        theButton.alphaHitTestMinimumThreshold = 0.5f;
    }
}
```

> [!TIP]
> Lze použít například při tvorbě kruhového tlačítka.