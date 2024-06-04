Here are some common data structures used in C# programming:

1. **Arrays**: An array stores a fixed-size sequential collection of elements of the same type. 

```csharp
int[] array = new int[5] {1, 2, 3, 4, 5};
```

2. **ArrayList**: The ArrayList is a non-generic type of collection in C#. It can contain elements of any data types.

```csharp
ArrayList arrayList = new ArrayList();
arrayList.Add(1);
arrayList.Add("Two");
```

3. **List**: A List is a generic version of ArrayList. It is the same as an ArrayList except that List is a generic type, so you can have a list of any type.

```csharp
List<int> list = new List<int>();
list.Add(1);
list.Add(2);
```

4. **LinkedList**: LinkedList is a doubly-linked list. Each node in the list holds a reference to the next as well as the previous node.

```csharp
LinkedList<int> linkedList = new LinkedList<int>();
linkedList.AddLast(1);
linkedList.AddLast(2);
```

5. **Stack**: A Stack is a data structure for storing a list of elements in a LIFO (last in, first out) fashion.

```csharp
Stack<int> stack = new Stack<int>();
stack.Push(1);
stack.Push(2);
```

6. **Queue**: A Queue is a data structure for storing a list of elements in a FIFO (first in, first out) fashion.

```csharp
Queue<int> queue = new Queue<int>();
queue.Enqueue(1);
queue.Enqueue(2);
```

7. **HashSet**: A HashSet is a collection of the unique elements. It is based on a hash table data structure.

```csharp
HashSet<int> hashSet = new HashSet<int>();
hashSet.Add(1);
hashSet.Add(2);
```

8. **Dictionary**: A Dictionary is a collection of keys and values.

```csharp
Dictionary<int, string> dictionary = new Dictionary<int, string>();
dictionary.Add(1, "One");
dictionary.Add(2, "Two");
```

9. **SortedList**: A SortedList is a collection of key/value pairs that are sorted by the keys and are accessible by key and by index.

```csharp
SortedList<int, string> sortedList = new SortedList<int, string>();
sortedList.Add(1, "One");
sortedList.Add(2, "Two");
```

10. **BitArray**: A BitArray is a collection of bits.

```csharp
BitArray bitArray = new BitArray(8);
bitArray.Set(0, true);
bitArray.Set(1, false);
```

Each of these data structures has its own strengths and weaknesses, and is best suited to specific types of tasks and data.