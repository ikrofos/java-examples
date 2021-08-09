Тестирование JUnit
---

Источники
---
- [JUnit 5 tutorial - Learn how to write unit tests](https://www.vogella.com/tutorials/JUnit/article.html)
- [JUnit 5 User Guide](https://junit.org/junit5/docs/current/user-guide/)
- [Create tests (www.jetbrains.com)](https://www.jetbrains.com/help/idea/create-tests.html#naming-pattern-for-tests)
- [JUnit 5 (www.jetbrains.com)](https://www.jetbrains.com/help/idea/junit.html)
- [Writing Tests with JUnit 5](https://blog.jetbrains.com/idea/2020/09/writing-tests-with-junit-5/)
- [JUnit 5 Display Names](https://mkyong.com/junit5/junit-5-display-names/)


https://www.jetbrains.com/help/idea/tdd-with-intellij-idea.html
https://www.jetbrains.com/help/idea/performing-tests.html#RedebugFailedTests
- [Параметризированные тесты в JUnit 5](https://urvanov.ru/2020/11/27/%D0%BF%D0%B0%D1%80%D0%B0%D0%BC%D0%B5%D1%82%D1%80%D0%B8%D0%B7%D0%B8%D1%80%D0%BE%D0%B2%D0%B0%D0%BD%D0%BD%D1%8B%D0%B5-%D1%82%D0%B5%D1%81%D1%82%D1%8B-%D0%B2-junit-5/)

Различия между аннотациями
---
![alt text](https://raw.githubusercontent.com/ikrofos/java-examples/main/src/%D0%A0%D0%B0%D0%B7%D0%BB%D0%B8%D1%87%D0%B8%D1%8F%20%D0%BC%D0%B5%D0%B6%D0%B4%D1%83%20%D0%B0%D0%BD%D0%BD%D0%BE%D1%82%D0%B0%D1%86%D0%B8%D1%8F%D0%BC%D0%B8.PNG)

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
