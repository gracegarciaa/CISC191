# Activity 13-14.1: Manipulating Databases Using Java

## My Code:
```
import java.sql.*;

import static java.time.chrono.JapaneseEra.values;

public class Miramar {
    public static void main(String[] args)
            throws SQLException, ClassNotFoundException {
        // Load the JDBC driver
        Class.forName("com.mysql.cj.jdbc.Driver");
        System.out.println("Driver loaded");

        // Establish a connection
        // Assuming the database name is 'miramar', user is 'testuser'
        // and password is 'Pa$$word'
        Connection connection = DriverManager.getConnection
                ("jdbc:mysql://localhost/miramar","testuser","Pa$$word");
        System.out.println("Database connected");

        // Create a statement
        Statement statement = connection.createStatement();

        // Execute a statement
        ResultSet resultSet = statement.executeQuery
                ("select * from Student;");
        // Iterate through the result and print the student names
        while (resultSet.next())
            System.out.println(resultSet.getString(1) + "\t" +
                    resultSet.getString(2) + "\t" + resultSet.getString(3) + "\t" +
                    resultSet.getString(4) + "\t" + resultSet.getString(5));

        // Close the connection
        connection.close();
    }
}
```

## Challenges:
I think my biggest challenge is figuring out how to use sql through java. I'm not even sure if I did this correctly but we'll see!
