# Java Collections

![Image result for java collections](https://www.sitesbay.com/collection-framework/images/collection-framework-hierarchy.png)

![Image result for java collections map](https://www.mainjava.com/wp-content/uploads/2016/08/map-interface.png)

Collection interface:

| boolean                                                                                                              | [add](https://docs.oracle.com/javase/8/docs/api/java/util/Collection.html#add-E-)                                                           |
| -------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------- |
| boolean                                                                                                              | [addAll](https://docs.oracle.com/javase/8/docs/api/java/util/Collection.html#addAll-java.util.Collection-)                                  |
| void                                                                                                                 | [clear](https://docs.oracle.com/javase/8/docs/api/java/util/Collection.html#clear--)                                                        |
| boolean                                                                                                              | Returns true if this collection contains the specified element.                                                                             |
| [contains](https://docs.oracle.com/javase/8/docs/api/java/util/Collection.html#contains-java.lang.Object-)           |                                                                                                                                             |
| boolean                                                                                                              | Returns true if this collection contains all of the elements  in the specified collection.                                                  |
| [containsAll](https://docs.oracle.com/javase/8/docs/api/java/util/Collection.html#containsAll-java.util.Collection-) |                                                                                                                                             |
| boolean                                                                                                              | [isEmpty](https://docs.oracle.com/javase/8/docs/api/java/util/Collection.html#isEmpty--)                                                    |
| [Iterator](https://docs.oracle.com/javase/8/docs/api/java/util/Iterator.html)                                        | [iterator](https://docs.oracle.com/javase/8/docs/api/java/util/Collection.html#iterator--)                                                  |
| default                                                                                                              | [parallelStream](https://docs.oracle.com/javase/8/docs/api/java/util/Collection.html#parallelStream--)                                      |
| boolean                                                                                                              | [remove](https://docs.oracle.com/javase/8/docs/api/java/util/Collection.html#remove-java.lang.Object-)                                      |
| boolean                                                                                                              | [removeAll](https://docs.oracle.com/javase/8/docs/api/java/util/Collection.html#removeAll-java.util.Collection-)                            |
| default boolean                                                                                                      | [removeIf](https://docs.oracle.com/javase/8/docs/api/java/util/Collection.html#removeIf-java.util.function.Predicate-)                      |
| boolean                                                                                                              | [retainAll](https://docs.oracle.com/javase/8/docs/api/java/util/Collection.html#retainAll-java.util.Collection-)                            |
| int                                                                                                                  | [size](https://docs.oracle.com/javase/8/docs/api/java/util/Collection.html#size--)                                                          |
| default                                                                                                              | [spliterator](https://docs.oracle.com/javase/8/docs/api/java/util/Collection.html#spliterator--)                                            |
| default                                                                                                              | [stream](https://docs.oracle.com/javase/8/docs/api/java/util/Collection.html#stream--)                                                      |
| [Object](https://docs.oracle.com/javase/8/docs/api/java/lang/Object.html)                                            | Returns an array containing all of the elements in this collection.                                                                         |
| [toArray](https://docs.oracle.com/javase/8/docs/api/java/util/Collection.html#toArray--)                             |                                                                                                                                             |
| \<T> T\[]                                                                                                            | Returns an array containing all of the elements in this collection;  the runtime type of the returned array is that of the specified array. |
| [toArray](https://docs.oracle.com/javase/8/docs/api/java/util/Collection.html#toArray-T:A-)                          |                                                                                                                                             |

* HashTable - хэш-таблица, не позволяет null в качестве ключа, все методы synchronized (низкая производительность)
* [HashMap](https://www.evernote.com/shard/s696/nl/1/69e6f898-b0dd-441e-b501-6dd915345a5c?title=HashMap)
* LinkedHashMap - упорядоченная мапа, основанная на двухсвязном списке
* TreeMap - упорядоченная мапа основанная на красно-черном дереве
* WeakHashMap - мапа с слабыми ссылками, gc удалит объекты если на них не будет других ссылок.
* HashSet - внутри объект hashMap для хранения, элементы хранятся на месте ключа, а на место значения ложится new Object()
* LinkedHashSet - использует LinkedHashMap для хранения, гарантирует порядок для вставки.
* TreeSet - использует NavigableMap, поддерживает порядок при помощи Comparator

LinkedHashMap ![ninja1000rr inserted](http://www.thejavageek.com/wp-content/uploads/2016/06/FourthObjectInserted.png)

TreeMap ![Fourth Object Inserted](http://www.thejavageek.com/wp-content/uploads/2016/06/FourthObjecctInserted.png)
