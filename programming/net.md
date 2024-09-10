## Modifikátory přístupu

Určuje přistup k danému prvku.

| Caller's location                      | public | protected internal | protected | internal | private protected | private | file |
|----------------------------------------|--------|--------------------|-----------|----------|-------------------|---------|------|
| Within the file                        | ✔️     | ✔️                 | ✔️        | ✔️       | ✔️                | ✔️      | ✔️   |
| Within the class                       | ✔️     | ✔️                 | ✔️        | ✔️       | ✔️                | ✔️      | ❌    |
| Derived class (same assembly)          | ✔️     | ✔️                 | ✔️        | ✔️       | ✔️                | ❌       | ❌    |
| Non-derived class (same assembly)      | ✔️     | ✔️                 | ❌         | ✔️       | ❌                 | ❌       | ❌    |
| Derived class (different assembly)     | ✔️     | ✔️                 | ✔️        | ❌        | ❌                 | ❌       | ❌    |
| Non-derived class (different assembly) | ✔️     | ❌                  | ❌         | ❌        | ❌                 | ❌       | ❌    |

Více podrobností <a href="https://learn.microsoft.com/en-us/dotnet/csharp/programming-guide/classes-and-structs/access-modifiers#summary-table">zde</a>.
  
## Uvolnění zdrojů

- **Řízené zdroje**

    = Objekty, které jsou spravovány garbage collectorem.
    
    Zahrnuje všechny objekty vytvořené pomocí klíčového slova `new`.
    
    Garbage collector automaticky sleduje tyto objekty a uvolňuje jejich paměť, když již nejsou potřebné.
    
    > [!TIP]
    > Programátoři nemusí explicitně uvolňovat paměť pro tyto objekty.
 
- **Neřízené zdroje**

    = Objekty, které nejsou spravovány garbage collectorem.
    
    Zahrnuje soubory, databázové připojení, síťové zdroje, atd...

    > [!NOTE]
    > Programátoři musí explicitně uvolnit tyto zdroje, aby zabránili úniku paměti.
    > 
    > Uvolnění zdrojů je důležité pro správné fungování aplikace.

### Destruktor
	
- Automaticky volán, když je objekt zničen garbage collectorem. 

- Definuje se pomocí syntaxe **`~ClassName()`**. 
 
- Uvolňuje neřízené zdroje, které třída drží.

- Destruktory nejsou deterministické.

    > [!TIP]
    > Znamená, že nevíme přesně, kdy budou volány. 

- **Jsou volány, když garbage collector rozhodne**, že je objekt vhodný ke zničení. 

    > [!NOTE]
    > Může to být kdykoliv po tom, co objekt přestane být používán.

### Dispose

- Součástí rozhraní `IDisposable` a je určen pro explicitní uvolnění zdrojů. 

- Metoda **`Dispose` je volána programátorem**, když je známo, že objekt již nebude potřebný. 

  > [!NOTE]
  > To umožňuje okamžité uvolnění zdrojů a zajišťuje, že nebudou drženy déle, než je nutné. 

- Metoda `Dispose` je určena pro uvolnění jak řízených, tak neřízených zdrojů.
	
## Volání funkcí z externích DLL

> [!NOTE]
> **Platform Invocation Services (PInvoke)** se používá pro volání knihoven z nativního kódu.

- Nativní kód = Kód kompilován do strojového kódu pro konkrétní platformu.

- Strojový kód = Kód přímo spustitelný na hardware dané platformy.

Postup:

<ol>
<li>

**Importování funkce z DLL**

Atribut **`DllImport`** z `System.Runtime.InteropServices` k importování funkce z DLL. 

Například:
```c#
using System.Runtime.InteropServices;

public class MyProgram
{
    [DllImport("User32.dll")]
    public static extern int MessageBox(IntPtr h, string m, string c, int type);
}
```

>[!NOTE]
> `MessageBox` je funkce definovaná v knihovně: `User32.dll`.
> 
> Tato funkce je nyní dostupná v rámci tohoto .NET kódu.

### Příklad knihovny v c++

Knihovna v c++ by mohla vypadat takto:

```c++
#include <windows.h>

extern "C" __declspec(dllexport) int MessageBox(HWND h, LPCSTR m, LPCSTR c, int type)
{
    return MessageBoxA(h, m, c, type);
}
```

### Metody a argumenty v c++

 - **`extern "C"`** 
	
	>[!WARNING]
    > Zajistí, že funkce jsou kompatibilní s C jazykem. (To je důležité pro interoperabilitu mezi C++ a jinými jazyky, jako je C#.)

	>[!TIP]
    > Když kompilátor narazí na funkci, změní její název na něco, co jednoznačně identifikuje nejen název funkce, ale také typy jejích parametrů.
    >
    > To znamená, že název funkce, jak je viděn v DLL, nebude stejný jako název funkce v původním kódu.
    >
    > Když použijete `extern "C"`, říkáte kompilátoru, aby tuto funkci nezměnil a zachoval její název tak, jak je. To umožňuje jiným jazykům, jako je C#, najít a volat tuto funkci správným názvem.

-   **`__declspec(dllexport)`**

    Říka kompilátoru C++, že tato funkce nebo proměnná bude exportována z DLL, takže ji může volat jiný kód, který tuto DLL používá.
 
	>[!WARNING]
    > Důležité k viditelnosti a dostupnosti pro `PInvoke`

- **`HWND`**

	"handle to a window" (rukojeť okna)
 
 - **`LPCTSTR`**

	"Long Pointer Constant String"

     > | Item           | 8-bitů (Ansi) | 16-bitů (Wide) | Různé   |
     > |----------------|---------------|----------------|---------|
     > | character      | CHAR          | WCHAR          | TCHAR   |
     > | string         | LPSTR         | LPWSTR         | LPTSTR  |
     > | string (const) | LPCSTR        | LPCWSTR        | LPCTSTR |
     >
     > Odkaz <a href="https://stackoverflow.com/questions/321413/lpcstr-lpctstr-and-lptstr"> zde</a>
</li>
<li>

**Volání importované funkce**

```c#
public class MyProgram
{
    public static void Main()
    {
        MessageBox(IntPtr.Zero, "Hello, World!", "Test MessageBox", 0);
    }
}
```

> `IntPtr.Zero`
>
> Konstanta, která reprezentuje nulový ukazatel.
>
> Je to ekvivalent NULL v C++.
</li>
</ol>

### `__Internal`

Pokud se používá **`__Internal` jako název DLL v atributu `DllImport`**, znamená to, že funkce se hledá přímo v hlavním spustitelném souboru.

> [!TIP]
> Hledá tedy v samotné aplikaci, pokud je to nativní kód, nebo v jedné z knihoven, na které aplikace odkazuje.
>
>   - Příklad použití v C#:
> 
>       ```c++
>       public class MyProgram
>       {
>           [DllImport("__Internal")]
>           public static extern int MyFunction();
>       
>           public static void Main()
>           {
>               MyFunction();
>           }
>       }
>       ```
>
>   - Příklad definice v C++
>
>       ```c++
>       extern "C" __declspec(dllexport) int MyFunction()
>       {
>           // Implementace vaší funkce
>           return 0;
>       }
>       ```
> 
>       V tomto příkladu `MyFunction` je funkce definovaná v nativním kódu.
> 
>       Je tedy součástí aplikace nebo jedné z jejích závislostí.

### Tipy

- `PInvoke`

    = **Platform Invocation Services**, což je technika v `.NET`, která umožňuje volání funkcí, které jsou implementovány v neřízeném kódu.

    > [!TIP]
    > To je obvykle používáno pro volání C API funkcí, které jsou definovány v DLL.
    >
    > Příklad:
    > 
    >```c#
    >       private static class PInvoke
    >       {
    >       #if UNITY_IOS || UNITY_TVOS
    >            private const string DllName = "__Internal";
    >       #elif UNITY_STANDALONE_OSX
    >            private const string DllName = "MacOSAppleAuthManager";
    >       #endif
    >       
    >           public delegate void NativeMessageHandlerCallbackDelegate(uint requestId, string payload);
    >       
    >           [AOT.MonoPInvokeCallback(typeof(NativeMessageHandlerCallbackDelegate))]
    >           public static void NativeMessageHandlerCallback(uint requestId, string payload)
    >           {   
    >               try
    >               {
    >                   CallbackHandler.ScheduleCallback(requestId, payload);
    >               }
    >               catch (Exception exception)
    >               {
    >                   Console.WriteLine("Received exception while scheduling a callback for request ID " + requestId);
    >                   Console.WriteLine("Detailed payload:\n" + payload);
    >                   Console.WriteLine("Exception: " + exception);
    >               }
    >           }
    >       
    >           [System.Runtime.InteropServices.DllImport(DllName)]
    >           public static extern bool AppleAuth_IsCurrentPlatformSupported();
    >       
    >           [System.Runtime.InteropServices.DllImport(DllName)]
    >           public static extern void AppleAuth_SetupNativeMessageHandlerCallback(NativeMessageHandlerCallbackDelegate callback);
    >                   
    >           [System.Runtime.InteropServices.DllImport(DllName)]
    >           public static extern void AppleAuth_GetCredentialState(uint requestId, string userId);
    >       
    >           [System.Runtime.InteropServices.DllImport(DllName)]
    >           public static extern void AppleAuth_LoginWithAppleId(uint requestId, int loginOptions, string nonceCStr, string stateCStr);
    >                   
    >           [System.Runtime.InteropServices.DllImport(DllName)]
    >           public static extern void AppleAuth_QuickLogin(uint requestId, string nonceCStr, string stateCStr);
    >                   
    >           [System.Runtime.InteropServices.DllImport(DllName)]
    >           public static extern void AppleAuth_RegisterCredentialsRevokedCallbackId(uint callbackId);
    >       
    >           [System.Runtime.InteropServices.DllImport(DllName)]
    >           public static extern void AppleAuth_LogMessage(string messageCStr);
    >       }
    >```
    
    Více info <a href="https://github.com/lupidan/apple-signin-unity/blob/master/AppleAuth/AppleAuthManager.cs">zde</a>.