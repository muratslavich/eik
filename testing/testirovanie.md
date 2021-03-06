# Тестирование

**Тестирование бывает:**

* Блочное (
* Интеграционное (
* Системное (
* Функциональное тестирование
* Тестирование производительности
* Тестирование удобства использования
* Тестирование безопасности
* Тестирование «черного ящика»
* Тестирование «белого ящика»&#x20;

**TDD - test driven development** - техника разработки ПО, при которой сначала пишется тест на определенный функционал, а затем пишется реализация этого функционала.

**JUnit - фреймворк для тестирования**&#x20;

&#x20;    [Unit тестирование с JUnit�](http://devcolibri.com/864)�

&#x20;    [Getting started JUnit4](https://github.com/junit-team/junit4/wiki/Getting-started)

**Инфраструктуры для написания и запуска тестов**

* JUnit,
* TestNG

**Библиотеки проверок**

* FEST Assert,
* Hamcrest,
* XMLUnit,
* HttpUnit

**Библиотеки для создания тестовых дублеров**

* Mockito,
* JMock,
* EasyMock&#x20;

pom.xml

```
< dependency > 
     < groupId > junit </ groupId > 
     < artifactId > junit </ artifactId > 
     < version > 4.11 </ version > 
     < scope > test </ scope > 
</ dependency > 
```

mvn test

```
package ru . csc . java2014 . testing ; 

import org . junit . Test ; 
import static org . junit . Assert .*; 

public class StringTest { 
     @Test 
     public void substring () { 
          assertEquals (" llo ", " Hello ". substring (3)); 
     } 
}
```

**org.junit.Assert**

* assertTrue
* assertFalse
* assertEquals
* assertArrayEquals
* assertNotEquals
* assertSame
* assertNotSame
* fail
* Варианты с текстом ошибки и без

**assert**&#x20;

* поддерживает только булевские условия
* в исключении нет описания проблемы
* Надо включать флагом JVM -ea

**Структура теста**

* Подготовка тестового окружения (Given)
* Выполнение тестового сценария (When)
* Проверки (Then)

**Жизненный цикл теста**

* @BeforeClass
* создание экземпляра тестового класса@Before@Test@After Для каждого @Test - метода
* @AfterClass

**TestDrivenDevelopment**

* Пишем простейший тест, ломающий программу
* Пишем простейшую реализацию, достаточную для прохождения теста
* Улучшаем написанный код, не ломая тесты
* Возвращаемся в п.1

Если писать тесты после кода, необходимо следить, чтобы были покрыты все возможные пути.

Если использовать TDD, то сразу становится понятно когда теста не хватает.

&#x20;        // ... arrange

&#x20;        // ... act

&#x20;        // ... assert

Чтобы протестировать надо разорвать внешние зависимости. Иногда код нетестопригоден. Нужно либо рефакторить, либо подменять его(заглушки).

Заглушка - управляемая замена существующей зависимости.

mocks - подставки

stubs - заглушки

fakes

**Выделение интерфейса с целью подмены истинной реализации**

**Внедрение реализации заглушки в тестируемый класс через КОНСТРУКТО�**�

**Внедрение подделки через установку свойства**

**Внедрение подделки перед вызовом метода**
