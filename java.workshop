import java.util.*;

class Account {
    // A single Scanner can be shared by child classes
    Scanner sc = new Scanner(System.in);
    String name;
    long acc_no;
    int age; // Added age field
    String gender;
    String nationality;
    String address;
    long balance = 0; // Balance is now part of the single object

    // Method to create an account with age validation
    void createAccount() {
        System.out.println("Enter the name: ");
        name = sc.nextLine();
        System.out.println("Enter the account number: ");
        acc_no = sc.nextLong();
        sc.nextLine(); // Consume the leftover newline

        // --- Age Validation Loop ---
        // This loop will continue until an age of 18 or greater is entered.
        do {
            System.out.println("Enter your age: ");
            age = sc.nextInt();
            if (age < 18) {
                System.out.println("Sorry, you must be 18 or older to create an account. Please try again.");
            }
        } while (age < 18);
        sc.nextLine(); // Consume the leftover newline after reading the age

        System.out.println("Enter the gender: ");
        gender = sc.nextLine();
        System.out.println("Enter your nationality: ");
        nationality = sc.nextLine();
        System.out.println("Enter your address: ");
        address = sc.nextLine();
        System.out.println("\nCongratulations your Account is Created Successfully!");
    }

    void display() {
        System.out.println("\n--- Account Information ---");
        System.out.println("Account Holder Name: " + name);
        System.out.println("Account Number: " + acc_no);
        System.out.println("Age: " + age); // Display the age
        System.out.println("Current Balance: " + balance); // Display the current balance
        System.out.println("Gender: " + gender);
        System.out.println("Nationality: " + nationality);
        System.out.println("Address: " + address);
        System.out.println("-------------------------\n");
    }
}

class Savings extends Account {

    void deposit() { // Renamed for consistency
        System.out.println("Enter the amount you want to deposit: ");
        long amount = sc.nextLong();
        if (amount <= 0) {
            System.out.println("Invalid amount. Deposit must be positive.");
        } else {
            // FIX: Add to the balance instead of overwriting it.
            balance += amount;
            System.out.println(amount + " has been credited to your account.");
            System.out.println("New balance is: " + balance);
        }
    }

    void withdraw() {
        System.out.println("Enter the amount you want to withdraw: ");
        long amount = sc.nextLong();
        // Check for sufficient balance
        if (amount > balance) {
            System.out.println("Insufficient Balance. Cannot withdraw.");
        } else if (amount <= 0) {
            System.out.println("Invalid amount. Withdrawal must be positive.");
        } else {
            // FIX: Update the actual balance variable.
            balance -= amount;
            System.out.println(amount + " has been withdrawn.");
            System.out.println("Remaining balance is: " + balance);
        }
    }
}

public class Casestudy {

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        
        // FIX: Create only ONE object of the child class 'Savings'.
        // This object 'S' inherits all properties (name, balance) and methods from 'Account'.
        Savings S = new Savings();
        
        while (true) {
            System.out.println("\nEnter the operation you want to perform: ");
            System.out.println("1. Create Account");
            System.out.println("2. Display Account Information");
            System.out.println("3. Deposit Money");
            System.out.println("4. Withdraw Money");
            System.out.println("5. Exit"); // Added an exit option

            int choice = sc.nextInt();

            switch (choice) {
                case 1:
                    // Call all methods on the single object 'S'
                    S.createAccount();
                    break;

                case 2:
                    S.display();
                    break;

                case 3:
                    // The deposit method is now also called on 'S'
                    S.deposit();
                    break;

                case 4:
                    // The withdraw method is now also called on 'S'
                    S.withdraw();
                    break;
                    
                case 5:
                    System.out.println("Thank you for banking with us!");
                    sc.close(); // Close the scanner
                    // Also close the scanner inside the Account object to prevent resource leaks
                    S.sc.close();
                    return; // Exit the program

                default:
                    System.out.println("Invalid Operation");
                    break;
            }
        }
    }
}
