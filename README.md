# Blog-management
import java.util.ArrayList;
import java.util.Scanner;

class BlogPost {
    private String title;
    private String content;

    public BlogPost(String title, String content) {
        this.title = title;
        this.content = content;
    }

    public String getTitle() {
        return title;
    }

    public String getContent() {
        return content;
    }

    @Override
    public String toString() {
        return "Title: " + title + "\nContent: " + content;
    }
}

class BlogManagementSystem {
    private ArrayList<BlogPost> blogPosts;
    private Scanner scanner;

    public BlogManagementSystem() {
        blogPosts = new ArrayList<>();
        scanner = new Scanner(System.in);
    }

    public void addBlogPost(String title, String content) {
        BlogPost newPost = new BlogPost(title, content);
        blogPosts.add(newPost);
        System.out.println("Blog post added: " + title);
    }

    public void displayBlogPosts() {
        System.out.println("\n--- Blog Posts ---");
        for (BlogPost post : blogPosts) {
            System.out.println(post);
            System.out.println("-------------");
        }
    }

    public static void main(String[] args) {
        BlogManagementSystem blogSystem = new BlogManagementSystem();
        int choice;

        do {
            System.out.println("\n1. Add Blog Post");
            System.out.println("2. Display Blog Posts");
            System.out.println("3. Exit");
            System.out.print("Enter your choice: ");
            choice = blogSystem.scanner.nextInt();

            switch (choice) {
                case 1:
                    System.out.print("Enter blog post title: ");
                    String title = blogSystem.scanner.next();
                    System.out.print("Enter blog post content: ");
                    String content = blogSystem.scanner.next();
                    blogSystem.addBlogPost(title, content);
                    break;
                case 2:
                    blogSystem.displayBlogPosts();
                    break;
                case 3:
                    System.out.println("Exiting Blog Management System. Goodbye!");
                    break;
                default:
                    System.out.println("Invalid choice. Please try again.");
            }
        } while (choice != 3);
    }
}
