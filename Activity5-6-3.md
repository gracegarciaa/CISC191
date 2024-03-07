# My Code
```
public class Book
{
    private String title;
    private String author;
    private String publisher;
    private String pubDate;

    public void setTitle(String title)
    {
        this.title = title;
    }
    public void setAuthor(String author)
    {
        this.author = author;
    }
    public void setPublisher(String publisher)
    {
        this.publisher = publisher;
    }
    public void setPubDate(String pubDate)
    {
        this.pubDate = pubDate;
    }
    public void printInfo()
    {
        System.out.println("Book Information:");
        System.out.println("Book Title: " + title);
        System.out.println("Author: " + author);
        System.out.println("Publisher: " + publisher);
        System.out.println("Publish Date: " + pubDate);
    }
}
```

```
public class Encyclopedia extends Book
{
    private String edition;
    private int pages;
    public void setEdition(String edition)
    {
        this.edition = edition;
    }
    public void setPages(int pages)
    {
        this.pages = pages;
    }
    @Override
    public void printInfo()
    {
        super.printInfo();
        System.out.println("Edition: " + edition);
        System.out.println("Number of Pages: " + pages);
    }
}
```

```
public class Main {
    public static void main(String[] args)
    {
        Book b1 = new Book();
        Encyclopedia b2 = new Encyclopedia();

        b1.setTitle("The Hobbit");
        b1.setAuthor("J. R. R. Tolkien");
        b1.setPublisher("George Allen & Unwin");
        b1.setPubDate("21 September 1937");
        b2.setTitle("The Illustrated Encyclopedia of the Universe");
        b2.setAuthor("Ian Ridpath");
        b2.setPublisher("Watson-Guptill");
        b2.setPubDate("2001");
        b2.setEdition("2nd");
        b2.setPages(384);

        b1.printInfo();
        System.out.println();
        b2.printInfo();
    }
}
```
__Boldface__
