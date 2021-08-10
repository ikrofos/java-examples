Содержание:
- > Источники
- > Руководство
- >> Репозитории
- >> Зависимости
- > Установка 
- > Решение проблем

Источники
---
- [Введение (java-course.ru)](https://www.youtube.com/watch?v=c2sBG5emv1o)
- [На русском (https://proselyte.net/)](https://proselyte.net/tutorials/maven/introduction/)
- [Использование Maven для построения Java проектов. Часть 1](https://www.youtube.com/watch?v=IAbZVA4tK6M)
- [Использование Maven для построения Java проектов. Часть 2](https://www.youtube.com/watch?v=Grl1GhklwDQ)
- [https://maven.apache.org/pom.html](POM Reference) [Описание тегов, теги компании, разработчиков]



Руководство
---
Ниже указаны значения по умолчанию для исходного кода проекта и других модулей.

| - | - | - |
| --- | --- | --- |
Исходный код | /src/main/java |
Ресурсы | /src/main/resources |
Тесты | /src/test | файлы юнит тестов |
Дистрибутив JAR | /target | 
Скомпилированный байт-код | /target/classes | Файлы после компиляции |


POM (Project Object Model) является базовым модулем Maven. Это специальный XML-файл, который всегда хранится в базовой директории проекта и называется pom.xml.

Файл POM содержит информацию о проекте и различных деталях конфигурации, которые используются Maven для создания проекта.

```xml
<project xmlns="http://maven.apache.org/POM/4.0.0"
   xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
   xsi:schemaLocation="http://maven.apache.org/POM/4.0.0
   http://maven.apache.org/xsd/maven-4.0.0.xsd">
   <modelVersion>4.0.0</modelVersion>

   <groupId>com.companyname.project-group</groupId>
   <artifactId>project</artifactId>
   <version>1.0</version>
 
</project>
```

– `groupID` - Это ID группы проекта. Зачастую, это уникальная организация или проект. Например, если мы хотим создать   группу, которая отвечает за видео, то groupId будет выглядеть, примерно так: net.proselyte.video. В этой группе будут все проекты, которые относятся к видео. 
Проект в рамках одного большого проекта 

– `artifactId` Это идентификатор самого проекта. Чаще всего – его имя. Например, maven-video. artifactId также помогает найти проект в репозитории.

– `version` Версия проекта. Определяет конкретную версию продукта. [Семантическое Версионирование 2.0.0](https://semver.org/lang/ru/).
Например:
```console
net.proselyte.video:maven-video:1.0
net.proselyte.video:maven-video:1.1
```

Существует три встроенных жизненных цикла сборки:
- Жизненный цикл (default) обрабатывает развертывания проекта.
- Жизненный цикл (clean) обрабатывает очистку проекта.
- Жизненный цикл (site) обрабатывает создание документации проекта.

Этапы (фазы) жизненного цикла Default (Build):
- `validate` – проверяет насколько `pom.xml` файл верный.
- `compile` – комплирует исходный код проекта.
- `test` - запуск Unit тестов
- `package` - создание конечного продукта. По умолчанию `JAR` файл 
- `install` - устанавливает пакет (jar) в локальный репозиторий, который может быть использован как зависимость в других локальных проектах.
- `deploy` - копирует финальный пакет (архив) в удалённый репозиторий для, того, чтобы сделать его доступным другим разработчикам и проектам.

[Выходная папка сохранения архива](http://maven.apache.org/plugins/maven-jar-plugin/jar-mojo.html#outputDirectory)
[Все короткие ссылки (${project.build.directory})](https://cwiki.apache.org/confluence/display/MAVEN/Maven+Properties+Guide)


Этапы (фазы) жизненного цикла Clean:
- `pre-clean` - выполнять процессы, необходимые до фактической очистки проекта.
- `clean` - очистка директории сборки (папка target). Удалить все файлы, созданные предыдущей сборкой.
- `post-clean` - выполнить процессы, необходимые для завершения очистки проекта.

`Задача (goal)` – это специальная задача, которая относится к сборке проекта и его управлению. Она может привязываться как к нескольким фазам, так и ни к одной. Задача, которая не привязана ни к одной фазе, может быть запущена вне фаз сборки с помощью прямого вызова.

Порядок выполнения зависит от порядка вызова целей и фаз.

Например, рассмотрим команду ниже. Аргументы `clean` и `package` являются фазами сборки до тех пор, пока `dependency: copy-dependencies` является задачей.

`mvn clean dependency:copy-dependencies package`

В этом случае, сначала будет выполнена фаза `clean`, после этого будет выполнена задача `dependency: copy-dependencies`. После чего будет выполнена фаза `package`.


Репозитории
---
1. Локальный (`Local`) - [каталог на локальном компьютере](https://www.baeldung.com/maven-local-repository) путь к которому прописан в `d:\apache-maven-3.8.1\conf\settings.xml` строка `localRepository`. При первом создании (build) проекта Maven скачивает все зависимости в локальный репозиторий. Обычно этот каталог называется .m2.
2. Центральный (`Central`) - сайт с библиотеками.
3. Корпоративный, Удаленный (`Remote`) - пользовательский репозиторий, принадлежащий организации




Зависимости 
---
```xml
    <dependencies>
        <!-- https://mvnrepository.com/artifact/org.junit.jupiter/junit-jupiter-engine -->
        <dependency>
            <groupId>org.junit.jupiter</groupId>
            <artifactId>junit-jupiter-engine</artifactId>
            <version>5.8.0-M1</version>
            <scope>test</scope>
        </dependency>
    </dependencies>
```

Область зависимости (Dependency Scope)
---
- [Dependency Scope (maven.apache.org)](https://maven.apache.org/guides/introduction/introduction-to-dependency-mechanism.html#Dependency_Scope)
- [What is `scope` under `dependency` in pom.xml for? (stackoverflow.com)](https://stackoverflow.com/a/47121804)


Элемент \<`scope`\> может принимать 6 значений: компиляция (compile), предоставление (provided), время выполнения (runtime), проверка (test), система (system) и импорт (import).

- `compile`: область по умолчанию, путь к классам доступен как для `src/main`, так и для `src/test`. Будет работать в момент компиляции и будет включён в пакет. 
- `<scope>test</scope>` -  зависимость не требуется для нормального использования приложения и доступна только на этапах `компиляции` и `выполнения теста`. Обычно эта область используется для тестовых библиотек, таких как JUnit и Mockito. Для `src/test`.
- `provided`: что это очень похоже `compile`, JDK или контейнер предоставят эту зависимость во время выполнения. Только для компиляции, но не для создания пакета.
- `runtime`: не требуется для компиляции требуется только во время выполнения
- `system` - похоже на `provided`, но библиотека подключается из вне. Не в одном репозитории, а на стороне.
- `import`: может импортировать только другие POM в <dependencyManagement/>, доступный только в Maven 2.0.9 или новее. Смена родительского объекта не всегда практична, во многих проектах уже указан родительский проект для управления стандартами своей организации. dependencyManagement позволяет нам добавлять родительский проект, не создавая родительский, это похоже на множественное наследование.


Установка 
---
- [Использование JAVA_HOME для JDK](https://roufid.com/no-compiler-is-provided-in-this-environment/)
- [Source option 5 is no longer supported. Use 6 or later](https://github.com/jflex-de/jflex/issues/400)

Решение проблем
---
- [dependency not found.](https://ru.stackoverflow.com/questions/867006/maven-dependencies-%D0%BF%D0%BE%D0%B4%D0%BA%D0%BB%D1%8E%D1%87%D0%B8%D1%82%D1%8C-%D0%B7%D0%B0%D0%B2%D0%B8%D1%81%D0%B8%D0%BC%D0%BE%D1%81%D1%82%D0%B8-%D0%B2-web-project)
- [Перезагрузка проекта после добавления зависимости в pom.xml](https://stackoverflow.com/questions/65277972/intellij-idea-often-doesnt-resolve-maven-dependency)


