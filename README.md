# mini_ATM_system
import java.util.Scanner;

public class test2 {

    float Balance;
    int pin = 7852;// employee
    int pin1 = 9696;// client
    String name;

    void org() {
        try {

            System.out.println("-------------------------------------------------");
            System.out.println("chose number 1 or 2:");
            System.out.println("1 : you are a bank employee");
            System.out.println("2 : you are a bank client");
            Scanner sc = new Scanner(System.in);
            int ent = sc.nextInt();
            if (ent == 1) {
                System.out.println("--------------------------------------------------- ");
                Scanner s = new Scanner(System.in);
                System.out.println("enter your name: ");
                this.name = s.nextLine();
                // System.out.println(naam);
                System.out.println("enter your pin: ");
                int input = s.nextInt();
                if (input == pin) {
                    employee();
                }

                else {
                    System.out.println("invalid pin \n" + "please try again");
                    org();
                    // inputpin();
                }
            } else if (ent == 2) {
                Scanner s = new Scanner(System.in);
                System.out.println("---------------------------------------->");
                System.out.println("enter your name: ");
                this.name = s.nextLine();
                System.out.println("enter your pin: ");
                int input = s.nextInt();
                if (input == pin1) {
                    menu();
                } else {
                    System.out.println("invalid pin \n" + "please try again");
                    org();
                }
            } else {
                System.out.println("invalid choice");
                org();
            }
        } catch (Exception e) {
            System.out.println("Invalid input. Please enter an integer.");
            org();
        }
    }

    public void employee() {
        try {

            System.out.println("-------------------------------------------------");
            System.out.println("Welcome " + this.name + "\n----------------->>>");
            System.out.println("Enter choise number:\n");
            System.out.println("1 : Add  amount in client account");
            System.out.println("2 : Reset Pin");
            System.out.println("3 : Back");
            System.out.println("4 : Exit");
            Scanner sc = new Scanner(System.in);
            int klo = sc.nextInt();
            if (klo == 1) {
                update();
            } else if (klo == 2) {
                Resetpin();
            } else if (klo == 3) {
                org();
            } else if( klo == 4) {
                return;
            }
            // employee();
        } catch (Exception e) {
            System.out.println("Invalid input. Please enter an integer.");
            employee();
        }

    }

    void menu() {
        try {

            System.out.println("-------------------------------------------------");
            System.out.println("Welcome " + this.name + "\n---------------->>");
            System.out.println("Enter your choice:");
            System.out.println("1: FOR CHECK BALANCE");
            System.out.println("2: FOR  WITHDRAWAL");
            System.out.println("3: Reset Pin");
            System.out.println("4: Back");
            System.out.println("5: Exit");
            Scanner sc = new Scanner(System.in);
            int num = sc.nextInt();
            if (num == 1) {
                System.out.println("--------------------------------------");
                System.out.println("your available balance is $" + Balance);
                menu();
            } else if (num == 2) {
                Withdrawal();
            } else if (num == 3) {

                Resetpin2();

            } else if (num == 4) {
                org();
            } else if (num == 5) {
                return;
            }
        } catch (Exception e) {
            System.out.println("Invalid input. Please enter an integer.");
            menu();
        }
    }

    void update() {
        try {

            System.out.println("-------------------------------------------------");

            System.out.println("enter amount");
            Scanner i = new Scanner(System.in);
            float a = i.nextInt();
            Balance = Balance + a;
            System.out.println("add successfully in your account!!!");
            System.out.println("Total amount :$" + Balance);
            employee();

        } catch (Exception e) {
            System.out.println("Invalid input. Please enter an integer.");
            update();
        }

    }

    void Withdrawal() {
        try {

            System.out.println("-------------------------------------------------");
            // System.out.println("-------------------------------------------------");
            System.out.println("enter amount");
            Scanner i = new Scanner(System.in);
            float a = i.nextInt();
            if (Balance >= a) {
                Balance = Balance - a;
                System.out.println("  Withdrawal money successfully: $" + a);
                System.out.println("  outstanding amount $" + Balance);
                menu();
            } else {
                System.out.println("insufficient balance");
                menu();
            }
        } catch (Exception e) {
            System.out.println("Invalid input. Please enter an integer.");
            Withdrawal();
        }

    }

    // employee's pin
    void Resetpin() {
        // int temp;
        try {

            System.out.println("----------------------------->");
            System.out.println("enter your old pin:");
            Scanner sc = new Scanner(System.in);
            int client = sc.nextInt();
            if (pin == client) {

                System.out.println("enter your new pin:");
                // Scanner i = new Scanner(System.in);
                int new1 = sc.nextInt();
                // temp = pin;
                pin = new1;
                System.out.println("Update successfully your pin:");
                org();
            } else {
                System.out.println("invalid pin \n" + "please try again");
                menu();


            }
        } catch (Exception e) {
            System.out.println("Invalid input. Please enter an integer.");
            Resetpin();
        }

    }

    // client's pin
    void Resetpin2() {
        // int temp;
        try {

            System.out.println("----------------------------->");
            System.out.println("enter your old pin");
            Scanner sc = new Scanner(System.in);
            int employee = sc.nextInt();
            if (employee == pin1) {

                System.out.println("enter your new pin");
                // Scanner i = new Scanner(System.in);
                int new1 = sc.nextInt();
                // temp = pin1;
                pin1 = new1;
                System.out.println("Update successfully your pin:");
                org();
            } else {
                System.out.println("invalid pin");
                menu();
            }
        } catch (Exception e) {
            System.out.println("Invalid input. Please enter an integer.");
        }
        Resetpin2();

    }

    public static void main(String[] args) {
        System.out.println("------------------------------------------------->>");
        System.out.println("Welcome to SBI ATM");
        System.out.println("------------------------------------------------->>");
        System.out.println("NOTE !  Employee pin (7852) \n   : clinte pin (9696)");
        // System.out.println("");
        // System.out.println();
        test2 obj = new test2();
        // obj.inputpin();
        obj.org();
        System.out.println("thank you for visiting us");
    }
}
