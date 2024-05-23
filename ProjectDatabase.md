# Project Database

## My Code:
```
import javax.swing.*;
import java.awt.*;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;
import java.io.File;
import java.io.FileInputStream;
import java.io.FileNotFoundException;
import java.sql.*;
import java.util.Scanner;

import static java.time.chrono.JapaneseEra.values;

public class SimpleJdbc {
    public static void main(String[] args)
            throws SQLException, ClassNotFoundException, FileNotFoundException {
        // Load the JDBC driver
        Class.forName("com.mysql.cj.jdbc.Driver");
        System.out.println("Driver loaded");

        // Establish a connection
        // Assuming the database name is 'Auto', user is 'root'
        // and password is 'Pa$$word'
        Connection connection = DriverManager.getConnection
                ("jdbc:mysql://localhost/Auto","testuser","Pa$$word");
        System.out.println("Database connected");

        // Create a statement
        Statement statement = connection.createStatement();

        FileInputStream inputData;
        try {
            inputData = new FileInputStream("~/Desktop/CISC191/Project Database/AutoMPG.txt");
        }catch(FileNotFoundException e)
            {
                throw new RuntimeException(e);
            }

        Scanner input = new Scanner(inputData);
        int i = 1;
        float mpg = 0;
        int cylinders = 0;
        float displacement = 0;
        float horsepower = 0;
        float weight = 0;
        float acceleration = 0;
        int modelYear = 0;
        int origin = 0;
        String carName = "";

        while(input.hasNextLine() == true)
        {
            if(i == 1)
            {
                mpg = input.nextFloat();
                i++;
                System.out.println(mpg);
            }
        }

        // Execute a statement
        ResultSet resultSet = statement.executeQuery
                ("select * from Auto;");
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

