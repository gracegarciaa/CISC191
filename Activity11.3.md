# Activity 11.3: GUI input and formatted text fields

## My Code:
```
import java.awt.GridBagConstraints;
import java.awt.GridBagLayout;
import java.awt.Insets;
import javax.swing.JFrame;
import javax.swing.JLabel;
import javax.swing.JSpinner;
import javax.swing.JTextField;
import javax.swing.SpinnerNumberModel;
import javax.swing.event.ChangeEvent;
import javax.swing.event.ChangeListener;


public class MilesToKm extends JFrame implements ChangeListener {
    private JSpinner miSpinner;    // Triggers miles conversion
    private JTextField kmField; // Displays conversion to km
    private JLabel miLabel;        // Label for # miles
    private JLabel kmLabel;     // Label for km conversion


    /* Constructor creates GUI components and adds GUI components
       using a GridBagLayout. */
    MilesToKm() {
        // Used to specify GUI component layout
        GridBagConstraints layoutConst = null;


        // Specifies the types of values displayed in spinner
        SpinnerNumberModel spinnerModel = null;


        // Set frame's title
        setTitle("Miles to Km Conversion");


        // Create labels
        miLabel = new JLabel("Miles:");
        kmLabel = new JLabel("Kilometers:");


        // Create a spinner model, the spinner, and set the change listener
        spinnerModel = new SpinnerNumberModel();
        miSpinner = new JSpinner(spinnerModel);
        miSpinner.addChangeListener(this);


        // Create field
        kmField = new JTextField(15);
        kmField.setEditable(false);
        kmField.setText("0");


        // Use a GridBagLayout
        setLayout(new GridBagLayout());


        // Specify component's grid location
        layoutConst = new GridBagConstraints();
        layoutConst.insets = new Insets(10, 10, 10, 1);
        layoutConst.anchor = GridBagConstraints.LINE_END;
        layoutConst.gridx = 0;
        layoutConst.gridy = 0;
        add(miLabel, layoutConst);


        layoutConst = new GridBagConstraints();
        layoutConst.insets = new Insets(10, 1, 10, 10);
        layoutConst.fill = GridBagConstraints.HORIZONTAL;
        layoutConst.gridx = 1;
        layoutConst.gridy = 0;
        add(miSpinner, layoutConst);


        layoutConst = new GridBagConstraints();
        layoutConst.insets = new Insets(10, 10, 10, 1);
        layoutConst.anchor = GridBagConstraints.LINE_END;
        layoutConst.gridx = 0;
        layoutConst.gridy = 1;
        add(kmLabel, layoutConst);


        layoutConst = new GridBagConstraints();
        layoutConst.insets = new Insets(10, 1, 10, 10);
        layoutConst.fill = GridBagConstraints.HORIZONTAL;
        layoutConst.gridx = 1;
        layoutConst.gridy = 1;
        add(kmField, layoutConst);
    }


    @Override
    public void stateChanged(ChangeEvent event) {
        Integer mi;     // # miles
        Double km;      // conversion to km


        mi = (Integer) miSpinner.getValue();
        km = mi*1.6;

        // Choose output based on dog's age component
        switch (mi) {
            case 0:
                kmField.setText("0 - 15");
                break;
            default:
                kmField.setText(km.toString());
        }
    }


    /* Creates a DogYearsFrame and makes it visible */
    public static void main(String[] args) {
        // Creates DogYearsFrame and its components
        MilesToKm myFrame = new MilesToKm();


        myFrame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        myFrame.pack();
        myFrame.setVisible(true);
    }
}

```

## Challenges:
This assignment was a little more challenging for me because I am still navigating JSpinners and its components. The most difficult part for me was figuring out stateChanged and the SpinnerNumberModel.
