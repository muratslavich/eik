# Java способы перебора коллекции Map

Map\<String, String> map = new HashMap<>();

&#x20;   map.put("1", "Понедельник");

&#x20;   map.put("2", "Вторник");

&#x20;   map.put("3", "Среда");

&#x20;   // Map.Entry - описываем пару (ключ - значение) "3=Среда" и т.п.

&#x20;   // entrySet - возращает множество со значениями карты, т.е. \[3=Среда, 2=Вторник, 1=Понедельник]

&#x20;   **for (Map.Entry\<String, String> entry : map.entrySet()) {**

\*\*        System.out.println("ID =  " + entry.getKey() + " День недели = " + entry.getValue());\*\*

&#x20;   }

&#x20;   System.out.println();

&#x20;   // Iterator - интерфейс, для организации цикла для перебора коллекций

&#x20;   // hasNext - true, если есть еще элементы

&#x20;   // next - возвращает слудующий элемент

&#x20;   **Iterator\<Map.Entry\<String, String>> entries = map.entrySet().iterator();**

\*\*    while (entries.hasNext()) {\*\*

\*\*        Map.Entry\<String, String> entry = entries.next();\*\*

\*\*        System.out.println("ID = " + entry.getKey() + " День недели = " + entry.getValue());\*\*

\*\*    }\*\*

&#x20;   System.out.println();

&#x20;   // keySet - возвращает множество ключей

&#x20;   **for (String key : map.keySet()) {**

\*\*        System.out.println("ID = " + key + ", День недели = " +  map.get(key));\*\*

\*\*    }\*\*

&#x20;   System.out.println();

В Java8 все гораздо проще и без всяких циклов:

Map\<String, Integer> fruits = new HashMap<>();

fruits.put("pineapple", 100);

fruits.put("banana", 15);

fruits.put("mango", 60);

fruits.put("papaya", 20);

fruits.put("orange", 25);

fruits.put("lemon", 7);

fruits.forEach((key, value) -> {

&#x20;       System.out.println(key + " == " + value);

});
