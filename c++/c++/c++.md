# c++

\=

\+

\-

/          - если оба операнда целые то результат округляется до целого

%          - остаток от деления

\++

\--

\>

\>=

<

<=

\==

!=

!

&&     - логическое и

||       - логическое или

&#x20;         **Унарные операции**

sizeof     - размер

\~          - поразрядное отрицание

&          - взятие адресса

\* разадресация

new          -выделение памяти

delete        - освобождение памяти

(type)        - явное приведение типов

\++

\--

!

\-     унарный минус, арифметическое отрицание

\+    унарный плюс

&#x20;         **Бинарные операции**

\*

/

%

\+

\-

<<           сдвиг влево

\>>          сдвиг вправо

<

<=

\>

\>=

\==

!=

&          поразрядная И конъюнкция

^          поразрядное исключающее ИЛИ

\|           поразрядная дизъюнкция ИЛИ

&&

||

?:          условная операция

\=

\*=

/=

%=

\+=

\-=

<<=     сдвиг влево с присваиванием

\>>=

&=         поразрядное И с присваиванием

|=

^=

,           последовательное вычитание

**Ввод вывод**

**библиотека      \<stdio>**

printf()

scanf()

int printf(const char \*format \[, argument]... );

int scanf( const char \*format \[,argument]... );

(\*format) – форматная спецификация определяет вид строки и может содержать спецификаторы. Затем, следует список необязательных аргументов.

%<флаги><ширина><.точность><модификатор>тип

printf("Выводимый текст");

Функция возвращает либо число

отображенных символов, либо отрицательное число в случае неправильной работы.

int i =5;

float f = 10.5;

printf("i = %d, f = %f", i, f);

printf("i = %d,\n f = %f", i, f);

управляющие последовательности

Все управляющие символы, при использовании, обрамляются двойными кавычками,

но если необходимо вывести какое-то сообщение, то управляющие символы можно

записывать сразу в сообщении, в любом его месте.

Функция scanf( ) может работать сразу с несколькими переменными. Предположим, что

необходимо ввести два целых числа с клавиатуры. Вообще, можно дважды вызвать функцию

scanf( ), однако лучше воспользоваться такой конструкцией:

scanf(" %d, %d ", \&n, \&m);

Функция scanf( ) возвращает число успешно считанных элементов. Если операции

считывания не происходило, что бывает в том случае, когда вместо ожидаемого цифрового

значения вводится какая-то буква, то возвращаемое значение будет равно 0.

Обратите внимание на то, что в списке параметров функции scanf( ) перед каждой

переменной стоит знак &, он означает, что данные будут переданы из функции в программу

по ссылке.

**Потоковый ввод вывод       \<iostream>**

\>> извлечение из потока

<< вставка в поток

в namespace std - потоки определены с клавиатуры и экран

cin.get() - задержка до нажатия клавиши

\<conio.h>

getch() - задержка до нажатия клавиши

**Операторы ветвления**

if (условие\_истинно)

{ оператор; }

else // если условие не выполняется

{ альтернативный\_оператор; }

Пример:

if (i==5)

&#x20;    cout << "i=" << I << endl;

int i; // выражение

switch (i)

{      case 0: оператор\_1; break;

&#x20;      case 1: оператор\_2; break;

&#x20;      case 2: оператор\_3; break;

&#x20;      case 3: оператор\_4; break;

&#x20;      default: оператор\_по\_умолчанию;

}

int i=0;

while (i<=10) // пока условие истинно

{      cout << i ; // оператор

&#x20;      i++; // для выхода из цикла

}

int i;

do // цикл с постусловием

{      cout<\<i; // оператор

&#x20;      i++;

} // для выхода из цикла

while (i<=10); // условие

for (int i=0; i<10; i++)

{ cout<\<i; }

goto метка;

...

метка: оператор

**Указатели**

&#x20;    Указатель - переменная, содержащая адрес объекта

&#x20;    Адрес - целое число

тип\_данных \* имя\_переменной\_указателя; // типизированный указатель

void \* имя\_переменной\_указателя; // нетипизированный указатель

& - взять адрес переменной

\*  - взять значение переменной, расположенной по этому адресу - разадресация

int x =101;

int \*y; - указатель на переменную целого типа

y = \&x; - присвоить переменной указателю y адрес переменной x

int z = \*y;

Прежде чем использовать нетипизированный указатель его нужно привести к определенному типу

Типизированный указатель можно использовать только для указания на ячейку памяти определенного типа.

Над указателями можно выполнять унарные операции ++ --. При этом значение указателя изменяется на 1ячейку того типа на который он указывает&#x20;

printf() - %p позволяет вывести на экран адрес памяти в 16системе

int x= 101;

void \*v= \&x; // нетипизированному указателю v присвоен адрес переменной х

printf(" x= %d, v= %p \n", x, v);

int \*pw= (int\*)v; // явное преобразование типа void\* к типу int\*

printf(" x= %d, v= %p, pw= %p\n", x, v, pw);

pw++;

printf(" v= %p, pw= %p\n", v, pw);

**Динамическое распределение памяти**

статически - распределение памяти во время компиляции

динамически - во время выполнения программы

статические объекты - именованные переменные - действия над ними напрямую, через их имена - выделение и освобождение памяти автоматически

динамические - не имеют собственных имен - действия над ними пр-ся косвенно с помощью указателей - полностью вручную выделять и освобождать память

new

delete

int \*pint = new int(1024);

new int(1024) - выделить память под безымянный объект типа int, и инициализировать его значением 1024, и вернуть адрес созданного объекта.

int \*pint - объявление указателя типа int

выделение памяти под массив

int \*pia = new int\[4];&#x20;

не забываем удалять отведенную для них память

delete pint;

delete\[] pia;

Динамические объекты хранятся в куче

библиотеки для динамического распределения памяти&#x20;

**\<alloc.h>**

**\<stdlib.h>**

calloc

malloc

realoc

free

void \*calloc(size\_t nitems, size\_t size);     \\\выделяет память под nitems элементов по size байт и инициализирует ее нулями

void \*malloc(size\_t size);                    \\\выделяет память объемом size байт

void \*realloc (void \*block, size\_t size);     \\\пытается переразместить ранее выделенный блок памяти, изменив его размер на size

void free(void \*block);                       \\\пытается освободить блок, полученный посредством функции calloc, malloc или realloc

calloc malloc возвращают нетипизированный указатель - необходимо выполнять преобразование в указатель объявленного типа

**Функции, методы, подпрограммы**

Описать прототип функции.

Прототип используется для того, чтобы к ней можно было обращаться из других мест.

При вызове ф-ии тип парам сверяется с ожидаемым типом - гарантия стабильности.

При обращении к функции может быть неявно выполнено восходящее преобразование типов.

тип\_возвр\_знач имя(список\_форм\_параметров);

имена формальных параметров не важны, можно их не указывать

return - выходит из тела функции и возвращает значение

**Передача параметров в тело функции**

1. по значению
2. по ссылке
3. по указателю

void F1(int p, int q); // передача параметров по значению

void F2(int \&p, int \&q) // передача параметров по ссылке

void F3(int \*p, int \*q) // передача параметров по указателю

1. По значению

Область видимости локальных переменных p q - тело функции F()

После завершение функции память выделенная под локальные переменные освобождается

1. По ссылке

Ячейки памяти для ссылочных переменных p и q не создаются. Для работы используются ячейки памяти вызывающей программы, чьи адреса передаются в функцию S().

Переменные p q в теле функции S() не существуют как отдельные ячейки памяти, а служат лишь для обозначения ячеек x и y.

1. По указателю

в памяти выделяется 3 ячейки под переменные p,q,t

sizeof(int\*) - p, q

sizeof(int) - t

p, q - указатели в них копируются не значения, а адреса. При вызове это необходимо указать - S(\&x, \&y)

**Перегрузка функций**

int pow(int, int);

double pow(double, double);

**Массивы -** набор данных одного типа

Элементы массива хранятся в памяти последовательно.(учитывая размер каждого элемента например int - 4 байта(4 ячейки))

Двумерный массив располагается в памяти построчно.

Доступ к членам массива можно получить через индекс и через указатель.

Имя массива само является указателем на первый элемент массива.

Нельзя присвоить один массив другому оператором присваивания. Массивы копируются поэлементно, потому что имя массива - адрес в памяти на первый элемент массива.

При передачи массива, как параметра в функцию, передается значение имени массива - указатель на первый элемент массива. В локальном пространстве создается локальные переменные.

**Структуры**

**Переименование типов typedef**

Для того чтобы сделать программу более ясной, можно задать типу новое имя с

помощью ключевого слова typedef. Введенное таким образом имя можно использовать таким

же образом, как и имена стандартных типов.

Пример:

typedef unsigned int UINT;

typedef char Msg\[100];

UINT i, j ; // две переменных типа unsigned int

Msg str\[10]; // массив из 10 строк по 100 символов

**Перечисления enum**

enum name {list};

Имя типа задается если необходимо определять переменные этого типа

Эти переменные будут принимать значения только из списка

Константы инициализируют обычным образом, иначе первая = 0, а каждая след ++

enum Err {ERR\_\_READ, ERR\_\_WRITE, ERR\_CONVERT}; // задан тип

Err error; // определена переменная типа Err

switch (error)

{    case ERR\_READ: /\* операторы \*/ break;

&#x20;    case ERR\_WRITE: /\* операторы \*/ break;

&#x20;    case ERR\_CONVERT: /\* операторы \*/ break;

}

// Константам ERR\_READ, ERR\_WRITE, ERR\_CONVERT присваиваются

// значения 0, 1 и 2 соответственно

enum {two = 2, three, four, ten = 10, eleven, fifty = ten + 40};

// Константам three и four присваиваются значения 3 и 4, константе eleven — 11

**Структуры struct**

В отличии от массива может содержать разные типы

Элементы структуры - поля

Элементы могут иметь любой тип, кроме типа этой же структуры, но могут быть указателями на него

struct имя\_типа

{    тип\_1 элемент\_1:

&#x20;    тип\_2 элемент\_2;

&#x20;    ...

&#x20;    тип\_n элемент\_n;

} список\_описателей;

Имя структуры не обязательно, но тогда обязательно нужно указать список описателей

struct // безымянная структура

{

&#x20;    char f1o\[30]; // поля структуры

&#x20;    int date, code;

&#x20;    double salary;

} staff\[100], \*ps; // определен массив структур и указатель на структуру

Если список описателей отсутствует, то структура определяет новый тип

struct Worker// описание нового типа Worker

{

&#x20;    char fio\[30];

&#x20;    int date, code;

&#x20;    double salary;

}; // описание заканчивается точкой с запятой

Worker staff\[100], \*ps; // определение массива типа Worker и указателя на Worker

Для инициализации структуры значения ее элементов перечисляют в фигурных скобках в порядке их описания

struct

{

&#x20;    char fio\[30];

&#x20;    int date, code;

&#x20;    double salary;

} worker = {"Путинович В. В.", 31, 215, 3400.55 };

**union**

частный случай структуры

все поля распологаются по одному адресу

длина union равна длине наибольшей из длин его полей

В каждый момент времени в переменной типа union хранится только одно значение

Применяются для экономии памяти, если известно, что больше одного поля одновременно не требуется
