# CarRentalSystemLogin
import java.util.Scanner;

public class CarRentalLogin {

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        // Predefined username and password
        String correctUsername = "admin";
        String correctPassword = "pass123";

        int attempts = 3; // Maximum 3 attempts

        // Loop for 3 login attempts
        while (attempts > 0) {
            System.out.print("Enter Username: ");
            String username = sc.nextLine();

            System.out.print("Enter Password: ");
            String password = ""; // Store user input password
            char ch;

            // Reading password character by character
            try {
                // Using System.console() to read password hidden is ideal
                // But for IDEs we use Scanner to simulate character by character display
                password = sc.nextLine();
                System.out.print("You entered password characters: ");
                for (int i = 0; i < password.length(); i++) {
                    ch = password.charAt(i);
                    System.out.print(ch + " "); // Print each character while receiving
                }
                System.out.println(); // Move to next line
            } catch (Exception e) {
                System.out.println("Error reading password");
            }

            // Check credentials
            if (username.equals(correctUsername) && password.equals(correctPassword)) {
                System.out.println("Login Successful! Welcome " + username);
                break; // Exit loop if login is successful
            } else {
                attempts--; // Reduce remaining attempts
                System.out.println("Invalid Username or Password.");
                if (attempts > 0) {
                    System.out.println("You have " + attempts + " attempt(s) left.\n");
                } else {
                    System.out.println("You have used all attempts. Login blocked.");
                }
            }
        }

        sc.close();
    }
}
