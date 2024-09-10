## Queue

= Fronta

Funguje na principu FIFO (First In First Out) = První prvek, který je vložen do fronty, je první, který je vyjmut.

> [!NOTE]
> Představte si frontu jako řadu lidí čekajících na autobus.
>
> První člověk, který přišel (`enqueue`), je první, kdo nastoupí do autobusu (`dequeue`).   

Příklad:
```c#
Queue<int> queue = new Queue<int>();
queue.Enqueue(1); // Enqueue() vloží prvek do fronty
queue.Enqueue(2);
queue.Enqueue(3);

Console.WriteLine(queue.Dequeue()); // Dequeue() vyjme první prvek z fronty: 1
Console.WriteLine(queue.Dequeue()); // 2
Console.WriteLine(queue.Dequeue()); // 3
```
	
### PriorityQueue

Každý prvek ve frontě má přiřazenou prioritu. 
  
Prvek s nejvyšší prioritou je vždy vyjmut první.

Příklad:
```c#
PriorityQueue<int> queue = new PriorityQueue<int>();
queue.Enqueue(1, 2); // Enqueue() vloží prvek do fronty s prioritou 2
queue.Enqueue(2, 1); // Prvek s prioritou 1 bude vyjmut první
queue.Enqueue(3, 3);

Console.WriteLine(queue.Dequeue()); // 2
Console.WriteLine(queue.Dequeue()); // 1
Console.WriteLine(queue.Dequeue()); // 3
```

## Stack

= Zásobník

Funguje na principu LIFO (Last In First Out) = Poslední prvek, který je vložen do zásobníku, je první, který je vyjmut.

> [!NOTE]
> Představte si zásobník jako hromadu talířů.
>
> Poslední talíř, který je položen na hromadu (`push`), je první, který je vyjmut (`pop`).

Příklad:
```c#
Stack<int> stack = new Stack<int>();
stack.Push(1); // Push() vloží prvek na zásobník
stack.Push(2);
stack.Push(3);

Console.WriteLine(stack.Pop()); // Pop() vyjme poslední prvek ze zásobníku: 3
Console.WriteLine(stack.Pop()); // 2
Console.WriteLine(stack.Pop()); // 1
```

## List

- `List`

  Seznam prvků, který lze indexovat.

  Příklad:
    ```c#
    List<int> list = new List<int>();
    list.Add(1); // Add() přidá prvek na konec seznamu
    list.Add(2);
    list.Add(3);
  
    Console.WriteLine(list[1]); // Vrátí prvek na indexu 1: 2
    list.RemoveAt(1); // RemoveAt() odebere prvek na indexu 1
    Console.WriteLine(list[1]); // 3
    ```
	
### LinkedList

- `LinkedList`

  Seznam prvků, který lze efektivně upravovat.

  Příklad:
    ```c#
    LinkedList<int> linkedList = new LinkedList<int>();
    linkedList.AddLast(1); // AddLast() přidá prvek na konec seznamu
    linkedList.AddLast(2);
    linkedList.AddLast(3);
  
    Console.WriteLine(linkedList.First.Value); // Vrátí první prvek seznamu: 1
    linkedList.RemoveFirst(); // RemoveFirst() odebere první prvek ze seznamu
    Console.WriteLine(linkedList.First.Value); // 2
    ```
  > [!NOTE]
  > Rozdíl proti `Dictionary` je, že `LinkedList` je efektivnější pro úpravy, ale méně efektivní pro vyhledávání.

### SortedLinkedList

- `SortedLinkedList`

  Seznam prvků, který je automaticky seřazený.

  Příklad:
    ```c#
    SortedLinkedList<int> sortedLinkedList = new SortedLinkedList<int>();
    sortedLinkedList.Add(3); // Add() přidá prvek do seznamu
    sortedLinkedList.Add(1);
    sortedLinkedList.Add(2);
  
    Console.WriteLine(sortedLinkedList.First.Value); // Vrátí první prvek seznamu: 1
    sortedLinkedList.RemoveFirst(); // RemoveFirst() odebere první prvek ze seznamu
    Console.WriteLine(sortedLinkedList.First.Value); // 2
    ```
	
  > [!NOTE]
  > Rozdíl proti `LinkedList` je, že `SortedLinkedList` je automaticky seřazený.

## Dictionary

- `Dictionary`

  Kolekce klíč-hodnota, která je efektivní pro vyhledávání.

  Příklad:
    ```c#
    Map<string, int> map = new Map<string, int>();
    map.Put("key1", 1); // Put() přidá klíč a hodnotu do mapy
    map.Put("key2", 2);
    map.Put("key3", 3);
  
    Console.WriteLine(map.Get("key2")); // Get() vrátí hodnotu pod klíčem "key2": 2
    map.Remove("key2"); // Remove() odebere klíč a hodnotu z mapy
    Console.WriteLine(map.ContainsKey("key2")); // false
    ```

  > [!NOTE]
  > Je efektivní pro vyhledávání, ale méně efektivní pro úpravy.

### SortedDictionary

- `SortedDictionary`

  Kolekce klíč-hodnota, která je automaticky seřazena podle klíčů.

  Příklad:
    ```c#
    SortedDictionary<string, int> sortedDictionary = new SortedDictionary<string, int>();
    sortedDictionary.Add("key3", 3); // Add() přidá klíč a hodnotu do tabulky
    sortedDictionary.Add("key1", 1);
    sortedDictionary.Add("key2", 2);
  
    Console.WriteLine(sortedDictionary.First().Key); // Vrátí klíč prvního prvku: "key1"
    sortedDictionary.Remove("key1"); // Remove() odebere klíč a hodnotu z tabulky
    Console.WriteLine(sortedDictionary.First().Key); // "key2"
    ```

  > [!NOTE]
  > Rozdíl proti `Dictionary` je, že `SortedDictionary` je automaticky seřazený podle klíčů.

## HashSet

Množina unikátních prvků.

> [!WARNING]
> Není zaručeno, že prvky budou v množině ve stejném pořadí, jak byly přidány.

Příklad:
```c#
HashSet<int> hashSet = new HashSet<int>();
hashSet.Add(1); // Add() přidá prvek do množiny
hashSet.Add(2);
hashSet.Add(3);

Console.WriteLine(hashSet.Contains(2)); // Contains() zjistí, zda množina obsahuje prvek: true
hashSet.Remove(2); // Remove() odebere prvek z množiny
Console.WriteLine(hashSet.Contains(2)); // false
```

> [!NOTE]
> `HashSet` je optimalizovaný pro rychlé vyhledávání.

## Hashtable

Kolekce klíč-hodnota.

Příklad:
```c#
Hashtable hashtable = new Hashtable();
hashtable.Add("key1", 1); // Add() přidá klíč a hodnotu do tabulky
hashtable.Add("key2", 2);
hashtable.Add("key3", 3);

Console.WriteLine(hashtable["key2"]); // Vrátí hodnotu pod klíčem "key2": 2
hashtable.Remove("key2"); // Remove() odebere klíč a hodnotu z tabulky
Console.WriteLine(hashtable.Contains("key2")); // false
```

> [!WARNING]
> `Hashtable` je starší třída a je obecně doporučováno používat `Dictionary`

## Tuple

Kolekce prvků různých typů.

Příklad:
```c#
Tuple<int, string> tuple = new Tuple<int, string>(1, "Hello");
Console.WriteLine(tuple.Item1); // Vrátí první prvek: 1
Console.WriteLine(tuple.Item2); // Vrátí druhý prvek: "Hello"
```

> [!NOTE]
> `Tuple` je obecný typ, který lze použít pro vytvoření kolekce prvků různých typů.

### ValueTuple

Kolekce prvků různých typů, která je optimalizovaná pro rychlé vytváření.

> Kolekce znamená, že prvek může obsahovat více prvků.

Příklad:
```c#
(int, string) valueTuple = (1, "Hello");
Console.WriteLine(valueTuple.Item1); // Vrátí první prvek: 1
Console.WriteLine(valueTuple.Item2); // Vrátí druhý prvek: "Hello"
```

> [!NOTE]
> `ValueTuple` je optimalizovaný typ, který lze použít pro rychlé vytváření kolekce prvků různých typů.

> Vlastní názvy prvků:
> ```c#
> var tuple = (Shield: 1, Sword: "Hello");
> Console.WriteLine(tuple.Shield); // Vrátí první prvek: 1
> Console.WriteLine(tuple.Sword); // Vrátí druhý prvek: "Hello"
> ``` 

## ObservableCollection

Kolekce, která upozorní na změnu prvků.

Příklad:
```c#
    ObservableCollection<int> observableCollection = new ObservableCollection<int>();
    observableCollection.CollectionChanged += (sender, e) => {
        Console.WriteLine("Collection changed");
    };
    observableCollection.Add(1); // Přidá prvek do kolekce
```

> [!NOTE]
> `ObservableCollection` je užitečná pro sledování změn v kolekci.

## WeakReference

Slabá reference na objekt, která nezabraňuje garbage collectoru v uvolnění paměti.

Příklad:
```c#
    WeakReference<int> weakReference = new WeakReference<int>(1);
    Console.WriteLine(weakReference.TryGetTarget(out int value)); // TryGetTarget() vrátí hodnotu: true
```

> [!NOTE]
> `WeakReference` je užitečná pro sledování objektů, které mohou být uvolněny garbage collectorem.

## Memory

Ukazatel na paměť, který umožňuje bezpečný přístup k paměti.

Příklad:

```c#
Memory<int> memory = new Memory<int>(new int[] { 1, 2, 3 });
Console.WriteLine(memory.Span[1]); // Span[] vrátí prvek na indexu 1: 2
```

> [!NOTE]
> `Memory` je užitečná pro bezpečný přístup k paměti.

## Span

Ukazatel na paměť, který umožňuje bezpečný přístup k paměti.
    
Příklad:
```c#
        Span<int> span = new Span<int>(new int[] { 1, 2, 3 });
        Console.WriteLine(span[1]); // Vrátí prvek na indexu 1: 2
```
    
> [!NOTE]
> `Span` je užitečná pro bezpečný přístup k paměti.

## Immutable kolekce

### ImmutableArray

Pole, které nelze měnit.

 Příklad:
 ```c#
    ImmutableArray<int> immutableArray = ImmutableArray.Create(1, 2, 3);
    Console.WriteLine(immutableArray[1]); // Vrátí prvek na indexu 1: 2
 ```
> [!NOTE]
> `ImmutableArray` je pole, které nelze měnit.
 
### Immutable List

Seznam, který nelze měnit.

Příklad:
    ```c#
    ImmutableList<int> immutableList = ImmutableList.Create(1, 2, 3);
    Console.WriteLine(immutableList[1]); // Vrátí prvek na indexu 1: 2
    ```
> [!NOTE]
> `ImmutableList` je seznam, který nelze měnit.

### Immutable Dictionary

Kolekce klíč-hodnota, která nelze měnit.

Příklad:
```c#
    ImmutableDictionary<string, int> immutableDictionary = ImmutableDictionary.Create<string, int>();
    immutableDictionary = immutableDictionary.Add("key1", 1); // Add() přidá klíč a hodnotu do tabulky
    immutableDictionary = immutableDictionary.Add("key2", 2);
    immutableDictionary = immutableDictionary.Add("key3", 3);
  
    Console.WriteLine(immutableDictionary["key2"]); // Vrátí hodnotu pod klíčem "key2": 2
    immutableDictionary = immutableDictionary.Remove("key2"); // Remove() odebere klíč a hodnotu z tabulky
    Console.WriteLine(immutableDictionary.ContainsKey("key2")); // false
```

> [!NOTE]
> `ImmutableDictionary` je kolekce klíč-hodnota, která nelze měnit.

### Immutable HashSet

Množina prvků, kterou nelze měnit.

Příklad:
```c#
    ImmutableHashSet<int> immutableHashSet = ImmutableHashSet.Create(1, 2, 3);
    Console.WriteLine(immutableHashSet.Contains(2)); // Contains() zjistí, zda množina obsahuje prvek: true
```

> [!NOTE]
> `ImmutableHashSet` je množina prvků, kterou nelze měnit.
  
### Immutable SortedSet

Seřazená množina prvků, kterou nelze měnit.

Příklad:
```c#
    ImmutableSortedSet<int> immutableSortedSet = ImmutableSortedSet.Create(3, 1, 2);
    Console.WriteLine(immutableSortedSet.Min); // Min vrátí nejmenší prvek: 1
```

> [!NOTE]
> `ImmutableSortedSet` je seřazená množina prvků, kterou nelze měnit.

### Immutable Stack

Zásobník prvků, který nelze měnit.

Příklad:
```c#
    ImmutableStack<int> immutableStack = ImmutableStack.Create(1, 2, 3);
    Console.WriteLine(immutableStack.Peek()); // Peek() vrátí poslední prvek: 3
```

> [!NOTE]
> `ImmutableStack` je zásobník prvků, který nelze měnit.

### Immutable Queue

Fronta prvků, kterou nelze měnit.

Příklad:
```c#
    ImmutableQueue<int> immutableQueue = ImmutableQueue.Create(1, 2, 3);
    Console.WriteLine(immutableQueue.Peek()); // Peek() vrátí první prvek: 1
```

> [!NOTE]
> `ImmutableQueue` je fronta prvků, kterou nelze měnit. 

## Readonly kolekce

### ReadOnlyCollection

Kolekce, kterou nelze měnit.

Příklad:
```c#
    List<int> list = new List<int> { 1, 2, 3 };
    ReadOnlyCollection<int> readOnlyCollection = new ReadOnlyCollection<int>(list);
    Console.WriteLine(readOnlyCollection[1]); // Vrátí prvek na indexu 1: 2
```

> [!NOTE]
> `ReadOnlyCollection` je kolekce, kterou nelze měnit.
 
### ReadOnlyDictionary

Kolekce klíč-hodnota, kterou nelze měnit.

Příklad:
```c#
    Dictionary<string, int> dictionary = new Dictionary<string, int> {
        { "key1", 1 },
        { "key2", 2 },
        { "key3", 3 }
    };
    ReadOnlyDictionary<string, int> readOnlyDictionary = new ReadOnlyDictionary<string, int>(dictionary);
    Console.WriteLine(readOnlyDictionary["key2"]); // Vrátí hodnotu pod klíčem "key2": 2
```

> [!NOTE]
> `ReadOnlyDictionary` je kolekce klíč-hodnota, kterou nelze měnit.
  
### ReadOnlyList

Seznam prvků, který nelze měnit.

Příklad:
```c#
    List<int> list = new List<int> { 1, 2, 3 };
    ReadOnlyList<int> readOnlyList = new ReadOnlyList<int>(list);
    Console.WriteLine(readOnlyList[1]); // Vrátí prvek na indexu 1: 2
```

> [!NOTE]
> `ReadOnlyList` je seznam prvků, který nelze měnit.

## Asynchronní struktury dat

### ConcurrentQueue

Fronta, která je bezpečná pro použití ve více vláknech.

Příklad:
```c#
    ConcurrentQueue<int> concurrentQueue = new ConcurrentQueue<int>();
    concurrentQueue.Enqueue(1); // Enqueue() vloží prvek do fronty
    concurrentQueue.Enqueue(2);
    concurrentQueue.Enqueue(3);
  
    Console.WriteLine(concurrentQueue.TryDequeue(out int value)); // TryDequeue() vyjme první prvek z fronty: true
    Console.WriteLine(value); // 1
```

> [!NOTE]
> `ConcurrentQueue` je bezpečná pro použití ve více vláknech.
  
### ConcurrentStack

Zásobník, který je bezpečný pro použití ve více vláknech.

Příklad:
```c#
    ConcurrentStack<int> concurrentStack = new ConcurrentStack<int>();
    concurrentStack.Push(1); // Push() vloží prvek na zásobník
    concurrentStack.Push(2);
    concurrentStack.Push(3);
  
    Console.WriteLine(concurrentStack.TryPop(out int value)); // TryPop() vyjme poslední prvek ze zásobníku: true
    Console.WriteLine(value); // 3
```

> [!NOTE]
> `ConcurrentStack` je bezpečný pro použití ve více vláknech.
  
### ConcurrentDictionary

Kolekce klíč-hodnota, která je bezpečná pro použití ve více vláknech.

Příklad:
```c#
    ConcurrentDictionary<string, int> concurrentDictionary = new ConcurrentDictionary<string, int>();
    concurrentDictionary.TryAdd("key1", 1); // TryAdd() přidá klíč a hodnotu do tabulky
    concurrentDictionary.TryAdd("key2", 2);
    concurrentDictionary.TryAdd("key3", 3);
  
    Console.WriteLine(concurrentDictionary["key2"]); // Vrátí hodnotu pod klíčem "key2": 2
    concurrentDictionary.TryRemove("key2", out _); // TryRemove() odebere klíč a hodnotu z tabulky
    Console.WriteLine(concurrentDictionary.ContainsKey("key2")); // false
```

> [!NOTE]
> `ConcurrentDictionary` je bezpečná pro použití ve více vláknech.
  
### ConcurrentBag

Kolekce prvků, která je bezpečná pro použití ve více vláknech.

Příklad:
```c#
    ConcurrentBag<int> concurrentBag = new ConcurrentBag<int>();
    concurrentBag.Add(1); // Add() přidá prvek do kolekce
    concurrentBag.Add(2);
    concurrentBag.Add(3);
  
    Console.WriteLine(concurrentBag.TryTake(out int value)); // TryTake() vyjme prvek z kolekce: true
    Console.WriteLine(value); // 1
```

> [!NOTE]
> `ConcurrentBag` je bezpečná pro použití ve více vláknech.

### BlockingCollection

Kolekce prvků, která blokuje vlákno, pokud je prázdná nebo plná.

Příklad:
```c#
    BlockingCollection<int> blockingCollection = new BlockingCollection<int>();
    Task.Run(() => {
        blockingCollection.Add(1); // Add() přidá prvek do kolekce
    });
    Console.WriteLine(blockingCollection.Take()); // Take() vyjme prvek z kolekce
```

> [!NOTE]
> `BlockingCollection` je užitečná pro synchronizaci mezi vlákny.