# Список всех коллекций

| Интерфейс   | Класс/Реализация           | Описание      |
| ----------- | -------------------------- | ------------- |
| List        |  ArrayList                 |  Список       |
|  LinkedList |  Список                    |               |
|  Vector     |  Вектор                    |               |
|  Stack      |  Стек                      |               |
|  Set        |  HashSet                   |  Множество    |
|  TreeSet    |  Множество                 |               |
|  SortedSet  |  Отсортированное множество |               |
| Map         |  HashMap                   | Карта/Словарь |
|  TreeMap    |  Карта/Словарь             |               |
|  SortedMap  |  Отсортированный слова     |               |
|  Hashtable  |  Хеш-таблица               |               |

Вывод на экран элементов Set / List

&#x20;`public static void main(String[] args)`{

&#x20;   Set set = new HashSet(); // вместо set можно подставить list `set.add("Mama");     set.add("Mila");     set.add("Ramu");     //получение итератора для множества     Iterator iterator = set.iterator();     while (iterator.hasNext())        //проверка, есть ли ещё элементы        {         //получение текущего элемента и переход на следующий         String text = iterator.next();         System.out.println(text);     }`}

Через for-each

```
public static void main(String[] args){
    Set set = new HashSet();
    set.add("Mama");
    set.add("Mila");
    set.add("Ramu");

    for (String text : set)   
    {
        System.out.println(text);
    }}
```

Вывод на экран элементов Map

`public static void main(String[] args){     //все элементы хранятся в парах     Map<String, String> map = new HashMap<String, String>();     map.put("first", "Mama");     map.put("second", "Mila");     map.put("third", "Ramu");     Iterator<Map.Entry<String, String>> iterator = map.entrySet().iterator();     while (iterator.hasNext())     {         //получение «пары» элементов         Map.Entry<String, String> pair = iterator.next();         String key = pair.getKey();            //ключ         String value = pair.getValue();        //значение         System.out.println(key + ":" + value);`    }

&#x20;   &#x20;

***

&#x20;    for (Map.Entry\<String, String> pair : map.entrySet() {

&#x20;       String key = pair.getKey();                      //ключ

&#x20;       String value = pair.getValue();                  //значение

&#x20;       System.out.println(key + ":" + value);

&#x20;   }

&#x20;       ``       &#x20;

&#x20;   &#x20;

`}`
