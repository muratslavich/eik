# qt

Qt нуждается в компиляторе

* MSVS
* MinGW
* g++(gcc) - linux

Шаблон

```
template <class T>
void swap (T& a, T& b)
{
    T tmp = a;
    a = b;
    b = tmp;
}
```

Текущее дата и время

```
QDateTime now = QDateTime::currentDateTime();
```

Правила именования

* имена классов с большой буквы, верблюд
* функции, члены класса со строчной
* переменные-члены класса m\_
* функции qt из глобального пр имен qDebug()
* метод чтения без get
* метод записи set
* is has для bool
