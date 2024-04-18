# Activity 11.2: GUI input and formatted text fields

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

public class MilesConversion extends JFrame implements ActionListener {
    private JLabel milesLabel;     // Label for # miles
    private JLabel kLabel;              //Label for conversion to km
    private JLabel mLabel;      // Label for conversion to m
    private JLabel fLabel;      // Label for conversion to feet
    private JTextField milesField; // Displays # miles
    private JTextField kmField; // Displays conversion to km
    private JTextField mField;  // Displays conversion to m
    private JTextField fField;    //Displays conversion to feet
    private JButton calcButton;   //

    /* Constructor creates GUI components and adds GUI components
       using a GridBagLayout. */
    MilesConversion() {
        // Used to specify GUI component layout
        GridBagConstraints positionConst = null;

        // Set frame's title
        setTitle("Salary");

        // Set hourly and yearly salary labels
        milesLabel = new JLabel("Miles: ");
        kLabel = new JLabel("Kilometers: ");
        mLabel = new JLabel("Meters: ");
        fLabel = new JLabel("Feet: ");

        milesField = new JTextField(15);
        milesField.setEditable(true);
        milesField.setText("0");

        kmField = new JTextField(15);
        kmField.setEditable(false);
        kmField.setText("0");

        mField = new JTextField(15);
        mField.setEditable(false);
        mField.setText("0");

        fField = new JTextField(15);
        fField.setEditable(false);
        fField.setText("0");

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

        //Miles: [ ]
        add(milesLabel, positionConst);

        positionConst.gridx = 1;
        positionConst.gridy = 0;
        positionConst.insets = new Insets(10, 10, 10, 10);
        add(milesField, positionConst);

        //Kilometers: [ ]
        positionConst.gridx = 0;
        positionConst.gridy = 1;
        positionConst.insets = new Insets(10, 10, 10, 10);
        add(kLabel, positionConst);

        positionConst.gridx = 1;
        positionConst.gridy = 1;
        positionConst.insets = new Insets(10, 10, 10, 10);
        add(kmField, positionConst);

        //Meters: [ ]
        positionConst.gridx = 0;
        positionConst.gridy = 2;
        positionConst.insets = new Insets(10, 10, 10, 10);
        add(mLabel, positionConst);

        positionConst.gridx = 1;
        positionConst.gridy = 2;
        positionConst.insets = new Insets(10, 10, 10, 10);
        add(mField, positionConst);

        //Feet: [ ]
        positionConst.gridx = 0;
        positionConst.gridy = 3;
        positionConst.insets = new Insets(10, 10, 10, 10);
        add(fLabel, positionConst);

        positionConst.gridx = 1;
        positionConst.gridy = 3;
        positionConst.insets = new Insets(10, 10, 10, 10);
        add(fField, positionConst);

        //Calculate Button
        positionConst.gridx = 0;
        positionConst.gridy = 4;
        positionConst.insets = new Insets(10, 10, 10, 10);
        add(calcButton, positionConst);
    }

    /* Method is automatically called when an event
       occurs (e.g, button is pressed) */
    @Override
    public void actionPerformed(ActionEvent event) {
        String input1;
        String input2;
        String input3;
        String input4;
        int miles;
        int km;
        int m;
        int ft;

        // Get user's wage input
        input1 = milesField.getText();
        input2 = kmField.getText();
        input3 = mField.getText();
        input4 = fField.getText();

        // Convert from String to an integer
        miles = Integer.parseInt(input1);
        km = Integer.parseInt(input2);
        m = Integer.parseInt(input3);
        ft = Integer.parseInt(input4);

        // Display calculated salary
        kmField.setText(Double.toString((double) miles * 1.6));
        mField.setText(Double.toString((double) miles * 1609.344));
        fField.setText(Double.toString((double) miles * 5280));
    }

    /* Creates a SalaryCalculatorFrame and makes it visible */
    public static void main(String[] args) {
        // Creates SalaryLabelFrame and its components
        MilesConversion myFrame = new MilesConversion();

        myFrame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        myFrame.pack();
        myFrame.setVisible(true);
    }
}
```

## Challenges:
Since we've progressed through the unit, I think I have become more confident in using GUIs to execute tasks.
I ended up reusing my code from the last assignment and just readjusting it to fit this assignment. As a result, I did not have many difficulties because of it.
The most difficult part was that there are a lot of different variables to keep track of, so I had to be extra thorough to make sure they all line up.
