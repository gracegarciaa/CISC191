# Activity 7: Inheritance

## My Code:

```
import java.util.Scanner;
import java.util.InputMismatchException;
public class Main
{
    public static void main(String[] args)
    {
        Scanner reader = new Scanner(System.in);
        Pedometer a = new Pedometer();

        System.out.println("Enter # of steps to convert to miles: ");
        int steps = reader.nextInt();
        try
        {
            a.stepsToMiles(steps);
        }
        catch (InputMismatchException e)
        {
            System.out.println("Must enter a number!");
        }
        try
        {
            a.stepsToMiles(steps);
        }
        catch (NegativeValueException e)
        {
            System.out.println(e.getMessage());
        }
    }
}
```

```
public class Pedometer
{
    public double stepsToMiles(int steps)
    {
        double miles = (double)steps / 2000;
        System.out.printf("%.2f", miles);
        return miles;
    }
}
```

```
public class NegativeValueException extends Exception
{
    public NegativeValueException(String message)
    {
        super(message);
        message = "Exception: negative step count entered.";
    }
}
```
## Flowchart:
[click here](https://drive.google.com/file/d/11MREC2DopeBRpNZnwLqE_HEkZgXPhu3h/view?usp=sharing)

## Challenges:
I'm still a little lost on how to implement exceptions, especially when calling a method. 
I was also not sure if I should create my own exception for the negatives or if one already exists. 
I hope I can work it out with you if possible.
