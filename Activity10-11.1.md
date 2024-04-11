# Activity 10-11.1: GUI

## My Code:
```
import java.awt.GridBagConstraints;
import java.awt.GridBagLayout;
import java.awt.Insets;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;
import javax.swing.JButton;
import javax.swing.JFrame;
import javax.swing.JLabel;
import javax.swing.JTextField;

public class SalaryCalcButtonFrame extends JFrame implements ActionListener {
    private JLabel wageLabel;     // Label for hourly salary
    private JLabel hoursLabel;              //Label for number of hours worked
    private JLabel salLabel;      // Label for yearly salary
    private JTextField wageField; // Displays yearly salary
    private JTextField hoursField; // Displays # weekly hours
    private JTextField salField;  // Displays hourly salary
    private JButton calcButton;   // Triggers salary calculation

    /* Constructor creates GUI components and adds GUI components
       using a GridBagLayout. */
    SalaryCalcButtonFrame() {
        // Used to specify GUI component layout
        GridBagConstraints positionConst = null;

        // Set frame's title
        setTitle("Salary");

        // Set hourly and yearly salary labels
        wageLabel = new JLabel("Hourly wage:");
        hoursLabel = new JLabel("Weekly hours: ");
        salLabel = new JLabel("Yearly salary:");

        wageField = new JTextField(15);
        wageField.setEditable(true);
        wageField.setText("0");

        hoursField = new JTextField(15);
        hoursField.setEditable(true);
        hoursField.setText("0");

        salField = new JTextField(15);
        salField.setEditable(false);

        // Create a "Calculate" button
        calcButton = new JButton("Calculate");

        // Use "this" class to handle button presses
        calcButton.addActionListener(this);

        // Use a GridBagLayout
        setLayout(new GridBagLayout());
        positionConst = new GridBagConstraints();

        // Specify component's grid location
        positionConst.gridx = 0;
        positionConst.gridy = 0;

        // 10 pixels of padding around component
        positionConst.insets = new Insets(10, 10, 10, 10);

        // Add component using the specified constraints

        //Hourly: [#]
        add(wageLabel, positionConst);

        positionConst.gridx = 1;
        positionConst.gridy = 0;
        positionConst.insets = new Insets(10, 10, 10, 10);
        add(wageField, positionConst);

        //Weekly hours: [#]
        positionConst.gridx = 0;
        positionConst.gridy = 1;
        positionConst.insets = new Insets(10, 10, 10, 10);
        add(hoursLabel, positionConst);

        positionConst.gridx = 1;
        positionConst.gridy = 1;
        positionConst.insets = new Insets(10, 10, 10, 10);
        add(hoursField, positionConst);

        //Yearly Salary: [#]
        positionConst.gridx = 0;
        positionConst.gridy = 2;
        positionConst.insets = new Insets(10, 10, 10, 10);
        add(salLabel, positionConst);

        positionConst.gridx = 1;
        positionConst.gridy = 2;
        positionConst.insets = new Insets(10, 10, 10, 10);
        add(salField, positionConst);

        //Calculate Button
        positionConst.gridx = 0;
        positionConst.gridy = 3;
        positionConst.insets = new Insets(10, 10, 10, 10);
        add(calcButton, positionConst);
    }

    /* Method is automatically called when an event
       occurs (e.g, button is pressed) */
    @Override
    public void actionPerformed(ActionEvent event) {
        String userInput;      // User specified hourly wage
        String input2;         // User specified # weekly hours
        int hourlyWage;        // Hourly wage
        int weeklyHrs;         // # weekly hours

        // Get user's wage input
        userInput = wageField.getText();

        input2 = hoursField.getText();

        // Convert from String to an integer
        hourlyWage = Integer.parseInt(userInput);
        weeklyHrs = Integer.parseInt(input2);

        // Display calculated salary
        salField.setText(Integer.toString(hourlyWage * weeklyHrs * 52));
    }

    /* Creates a SalaryCalculatorFrame and makes it visible */
    public static void main(String[] args) {
        // Creates SalaryLabelFrame and its components
        SalaryCalcButtonFrame myFrame = new SalaryCalcButtonFrame();

        myFrame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        myFrame.pack();
        myFrame.setVisible(true);
    }
}
```

## Challenges:
I think this lab was a little bit more challenging for me because I am trying to learn about GUIs ahead of class. The most difficult part for me was taking user input and using it to execute my code. However, after rereading the GUI lecture a couple times, I was finally able to figure it out. It's mainly just trial and error for me.
