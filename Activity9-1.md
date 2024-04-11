# Acrivity 9.1: Collections

## My Code:
```
import java.util.Scanner;

public class Main
{
    public static void main(String[] args)
    {
        Scanner reader = new Scanner(System.in);
        System.out.println("Enter a String to check if it's a palindrome: ");
        String word = reader.nextLine();

        Palindrome a = new Palindrome();
        boolean pal = a.checkPalindrome(word);
        if(pal == true)
        System.out.println(word + " is a palindrome");
        else
            System.out.println(word + " is NOT a palindrome");
    }
}
```

```
import java.util.Deque;
import java.util.LinkedList;
import java.util.ListIterator;

public class Palindrome
{
    public boolean checkPalindrome(String word)
    {
        boolean pal = false;
        Deque<Character> palindrome = new LinkedList<Character>();

        //adds chars to LinkedList
        for (int i = 0; i < word.length(); i++)
        {
            char current = word.charAt(i);
            if(Character.isLetter(current) == true )
            {
                palindrome.add(current);
            }
        }

        while(!palindrome.isEmpty())
        {
            if(palindrome.size() == 1)
            {
                break;
            }
            char first = palindrome.removeFirst();
            char last = palindrome.removeLast();
            if(first == last)
            {
                pal = true;
            }
            else
                pal = false;
        }
        return pal;
    }
}
```

## Challenges:
Overall, this lab was fairly straight forward so I did notr have many challenges. 
However, I think the most difficult part about this activity was figuring out how to implement LinkedLists 
and the Deque class. I was referencing the lecture a lot but since it is new material, I expect it'll take 
a little longer to get the hang of it.
