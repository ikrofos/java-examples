[Класс Statement](http://java-online.ru/jdbc-statement.xhtml)

1. Создаём соединение
2. Создаём выражение
3. Выполняем запрос

Statement используется для выполнения SQL-запросов. Существует три типа класса Statement, которые являются как бы контейнерами для выполнения SQL-выражений через установленное соединение:
- Statement, базовый;
- PreparedStatement, наследующий от Statement;
- CallableStatement, наследующий от PreparedStatement.

Все классы специализируются для выполнения различных типов запросов:
- `Statement` предназначен для выполнения простых SQL-запросов без параметров; содержит базовые методы для выполнения запросов и извлечения результатов.
- `PreparedStatement` используется для выполнения SQL-запросов с или без входных параметров; добавляет методы управления входными параметрами.
- `CallableStatement` используется для вызовов хранимых процедур; добавляет методы для манипуляции выходными параметрами.


```java
import java.sql.*;

public class Application {
    public static void main(String[] args) {
        String url = "jdbc:postgresql://localhost:5432/db_name";
        String login = "postgres";
        String password = "postgres";
        try (Connection connection = DriverManager.getConnection(url, login, password)) {
            Statement statement = connection.createStatement();
            ResultSet resultSet = statement.executeQuery("SELECT * FROM jc_street WHERE street_code > 2");

            while (resultSet.next()) {
                System.out.println(resultSet.getInt(1) + " - " + resultSet.getString(2));

            }
        } catch (SQLException e) {
            System.out.println(e.getMessage());
        }
    }
}
```
[Работа с БД с помощью JDBC](https://www.examclouds.com/ru/java/java-core-russian/jdbc-work)
