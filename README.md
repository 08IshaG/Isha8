# isha
public class ATM {
static Scanner keyboard = new Scanner(System.in);
static String acctNum, pwd, result;
static double oldBalance, newBalance, deposit, withdraw;
static int choose;

public static void main(String[] args) {
    for (int run = 0; run < 3; run++) {
        System.out.println("Enter your account number");
        acctNum = keyboard.nextLine();
        System.out.println("Enter your account password");
        pwd = keyboard.nextLine();

        result = checkID(acctNum, pwd);
        if (!result.equals("ERROR")) {
            break;
        } else if (run == 2) {// you cannot try to log in anymore than 3
                                // times
            System.out.println("MAXIMUM TRIES EXCEEDED");
            return;
        }

    }
    menu();
}

public static String checkID(String acctNum, Object pwd) {
    String result = "ERROR";
    String a = "44567-5 mypassword 520.36";
    String b = "1234567-6 anotherpassword 48.20";
    String c = "4321-0 betterpassword 96.74";

    if (acctNum.equals("44567-5") && pwd.equals("mypassword")) {
        result = "520.36";
    } else if (acctNum.equals("1234567-6") && pwd.equals("anotherpassword")) {
        result = "48.20";
    } else if (acctNum.equals("4321-0") && pwd.equals("betterpassword")) {
        result = "96.74";
    }
    System.out.println(result);
    return result;
}

public static int menu() {
    System.out
            .println("Choose one of the following: \n1.Display Balance\n2.Deposit\n3.Withdraw\n4.Log Out");
    choose = keyboard.nextInt();

    if (choose == 1) {// 1. Display Balance
        displayBalance();
        menu();
        return 1;

    }
    if (choose == 2) {// 2. Deposit
        deposit();
        menu();
        return 2;

    }
    if (choose == 3) {// 3. Withdraw
        withdraw();
        menu();
        return 3;

    }
    if (choose == 4) {// 4. Log out
        System.out.println("You are logged out.");
        return 4;

    }
    if (choose <= 5) {// type in anything greater than 4 and you will get a
                        // system error
        System.out.println("System Error");
        menu();
        return 5;
    }
    if (choose >= 1) {// type in anything less than 1 and you will get a
                        // system error
        System.out.println("System Error");
        menu();
        return 6;
    }
    return choose;

}
