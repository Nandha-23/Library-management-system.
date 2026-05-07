Main.java

package library.main;

import library.model.Book;
import library.service.LibraryService;
import library.util.InputUtil;

public class Main {

    public static void main(String[] args) {

        LibraryService service = new LibraryService();

        while (true) {
            System.out.println("\n===== LIBRARY MANAGEMENT SYSTEM =====");
            System.out.println("1. Add Book");
            System.out.println("2. View Books");
            System.out.println("3. Issue Book");
            System.out.println("4. Exit");
            System.out.print("Enter choice: ");

            int choice = InputUtil.sc.nextInt();

            switch (choice) {
                case 1:
                    System.out.print("Enter Book ID: ");
                    int id = InputUtil.sc.nextInt();
                    InputUtil.sc.nextLine(); // clear buffer

                    System.out.print("Enter Title: ");
                    String title = InputUtil.sc.nextLine();

                    System.out.print("Enter Author: ");
                    String author = InputUtil.sc.nextLine();

                    service.addBook(new Book(id, title, author));
                    break;

                case 2:
                    service.viewBooks();
                    break;

                case 3:
                    System.out.print("Enter Book ID to issue: ");
                    int issueId = InputUtil.sc.nextInt();
                    service.issueBook(issueId);
                    break;

                case 4:
                    System.out.println("Thank you!...  Visit again");
                    System.exit(

                            0);

                default:
                    System.out.println("Invalid choice!");
            }
        }
    }
}

Book.java

package library.model;

public class Book {
    //Encapsulation concepts used

    private int id;
    private String title;
    private String author;
    private boolean issued;

    public Book(int id, String title, String author) {
        this.id = id;
        this.title = title;
        this.author = author;
        this.issued = false;
    }

    public int getId() {
        return id;
    }

    public String getTitle() {
        return title;
    }

    public String getAuthor() {
        return author;
    }

    public boolean isIssued() {
        return issued;
    }

    public void setIssued(boolean issued) {
        this.issued = issued;
    }
}

InputUtil.java

package library.util;

import java.util.Scanner;

public class InputUtil {

    public static Scanner sc = new Scanner(System.in);

}

