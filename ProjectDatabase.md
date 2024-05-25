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

        //SQL INSERT QUERY
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
        String insertSQL = "INSERT INTO Auto (mpg, cylinders, displacement, horsepower, weight, acceleration, modelYear, origin, carName) VALUES (?, ?, ?, ?, ?, ?, ?, ?, ?)";

        try (
                // Create a prepared statement
                PreparedStatement preparedStatement = connection.prepareStatement(insertSQL)
        ) {
            // Set values for the parameters
            //preparedStatement.setString(1, "value1");
            //preparedStatement.setString(2, "value2");
            //Read file & insert Data

            try {
                File myObj = new File("AutoMPG.txt");
                Scanner myReader = new Scanner(myObj);
                while (myReader.hasNextLine()) {
                    String data = myReader.nextLine();
                    System.out.println(data);
                    if(i==1)
                    {
                        mpg = Float.parseFloat(myReader.next());
                        preparedStatement.setFloat(i, mpg);
                        i++;
                    }
                    if(i==2)
                    {
                        cylinders = Integer.parseInt(myReader.next());
                        preparedStatement.setInt(i, cylinders);
                        i++;
                    }
                    if(i==3)
                    {
                        displacement = Float.parseFloat(myReader.next());
                        preparedStatement.setFloat(i, displacement);
                        i++;
                    }
                    if(i==4)
                    {
                        horsepower = Float.parseFloat(myReader.next());
                        preparedStatement.setFloat(i, horsepower);
                        i++;
                    }
                    if(i==5)
                    {
                        weight = Float.parseFloat(myReader.next());
                        preparedStatement.setFloat(i, weight);
                        i++;
                    }
                    if(i==6)
                    {
                        acceleration = Float.parseFloat(myReader.next());
                        preparedStatement.setFloat(i, acceleration);
                        i++;
                    }
                    if(i==7)
                    {
                        modelYear = Integer.parseInt(myReader.next());
                        preparedStatement.setInt(i, modelYear);
                        i++;
                    }
                    if(i==8)
                    {
                        origin = Integer.parseInt(myReader.next());
                        preparedStatement.setInt(i, origin);
                        i++;
                    }
                    if(i==9)
                    {
                        carName = myReader.next();
                        preparedStatement.setString(i, carName);
                        i=1;
                    }
                }
                myReader.close();
            } catch (FileNotFoundException e) {
                System.out.println("An error occurred.");
                e.printStackTrace();
            }

            // Execute the SQL INSERT statement
            int rowsAffected = preparedStatement.executeUpdate();
            System.out.println(rowsAffected + " row(s) affected.");
        } catch (SQLException e) {
            e.printStackTrace();
        }

        // Execute a statement
        JFrame mainFrame;
        JTextField inputField;
        mainFrame = new JFrame("Auto Database");
        mainFrame.setLayout(new FlowLayout());
        mainFrame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);

        JLabel inputLabel = new JLabel("Enter text to show result:");
        inputField = new JTextField(20);

        JButton submitButton = new JButton("Submit");

        submitButton.addActionListener(new SubmitButtonListener());

        mainFrame.add(inputLabel);
        mainFrame.add(inputField);
        mainFrame.add(submitButton);
        mainFrame.setVisible(true);
        ResultSet resultSet = statement.executeQuery
                ("select * from Auto;");
        SubmitButtonListener a = new SubmitButtonListener();
        a.displayResult(resultSet);
        new Slider();
        ResultSet resultSet1 = statement.executeQuery
                ("SELECT mpg, horsePower, ...\n" +
                        "FROM autoMPG\n" +
                        "WHERE condition" );
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
```
import javax.swing.*;
import java.awt.*;
import javax.swing.event.*;

public class Slider extends JFrame {

    private JSlider mpgSlider;
    private JSlider horsepowerSlider;
    private JLabel mpgLabel;
    private JLabel horsepowerLabel;
    private JFrame mainFrame;
    private JTextField inputField;

    public void Slider() {
        setTitle("Auto Database");
        setSize(400, 200);
        setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);

        // Create MPG slider
        mpgSlider = new JSlider(JSlider.HORIZONTAL, 0, 50, 25);
        mpgSlider.setMajorTickSpacing(10);
        mpgSlider.setMinorTickSpacing(1);
        mpgSlider.setPaintTicks(true);
        mpgSlider.setPaintLabels(true);
        mpgSlider.addChangeListener(new SliderChangeListener());

        // Create Horsepower slider
        horsepowerSlider = new JSlider(JSlider.HORIZONTAL, 0, 500, 250);
        horsepowerSlider.setMajorTickSpacing(100);
        horsepowerSlider.setMinorTickSpacing(10);
        horsepowerSlider.setPaintTicks(true);
        horsepowerSlider.setPaintLabels(true);
        horsepowerSlider.addChangeListener(new SliderChangeListener());

        // Create labels for sliders
        mpgLabel = new JLabel("MPG: 25");
        horsepowerLabel = new JLabel("Horsepower: 250");

        // Add sliders and labels to the frame
        JPanel panel = new JPanel(new GridLayout(4, 1));
        panel.add(mpgLabel);
        panel.add(mpgSlider);
        panel.add(horsepowerLabel);
        panel.add(horsepowerSlider);
        add(panel);

        setVisible(true);
    }

    public class SliderChangeListener implements ChangeListener {
        public void stateChanged(ChangeEvent e) {
            JSlider source = (JSlider) e.getSource();
            if (!source.getValueIsAdjusting()) {
                if (source == mpgSlider) {
                    int value = mpgSlider.getValue();
                    mpgLabel.setText("MPG: " + value);
                } else if (source == horsepowerSlider) {
                    int value = horsepowerSlider.getValue();
                    horsepowerLabel.setText("Horsepower: " + value);
                }
            }
        }
    }

    public static void main(String[] args) {
        new Slider();
    }
}
```
```
import javax.swing.*;
import java.awt.event.*;
import java.sql.ResultSet;

public class SubmitButtonListener implements ActionListener
    {
        public void actionPerformed(ActionEvent e) {
            JTextField inputField = new JTextField(20);
            String userInput = inputField.getText();
        }
        public void displayResult(ResultSet result) {
            JFrame resultFrame = new JFrame("Result");
            JLabel resultLabel = new JLabel("You entered: " + result);
            resultFrame.getContentPane().add(resultLabel);
            resultFrame.setSize(300, 100);
            resultFrame.setVisible(true);
        }

        public static void main(String[] args) {
            new SubmitButtonListener();
        }
    }
```

