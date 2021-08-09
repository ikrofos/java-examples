Тестирование JUnit
---

Источники
---
- [JUnit 5 tutorial - Learn how to write unit tests](https://www.vogella.com/tutorials/JUnit/article.html)
- [JUnit 5 User Guide](https://junit.org/junit5/docs/current/user-guide/)



Различия между аннотациями
---


Последовательность выполнения

![alt text](https://images4.russianblogs.com/967/61/6136acedd5c7f2313175b1d37336781f.png)

характеристика Junit 4	Junit 5
Выполнять перед всеми тестовыми методами текущего класса.
Аннотации к статическим методам.
Этот метод может содержать некоторый код инициализации.
@BeforeClass	@BeforeAll
Выполнить после всех тестовых методов в текущем классе.
Аннотации к статическим методам.
Этот метод может содержать некоторый код очистки.
@AfterClass	@AfterAll
Выполняйте перед каждым методом тестирования.
Аннотации относятся к нестатическим методам.
Вы можете повторно инициализировать некоторые свойства класса, которые требуются для метода тестирования.
@Before	@BeforeEach
Выполняйте после каждого метода тестирования.
Аннотации относятся к нестатическим методам.
Модификацию базы данных, вызванную тестовым методом, можно откатить.
@After	
@AfterEach

https://russianblogs.com/article/72191273138/