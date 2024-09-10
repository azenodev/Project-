import java.util.ArrayList;
import java.util.List;

// Interface for Account
interface Account {
    void deposit(double amount);
    void withdraw(double amount);
    double calculateInterest();
    double viewBalance();
}

// Class Bank
class Bank {
    private List<Account> accounts;

    public Bank() {
        accounts = new ArrayList<>();
    }

    public void addAccount(Account account) {
        accounts.add(account);
    }

    public void displayAccounts() {
        for (Account account : accounts) {
            System.out.println("Account Balance: " + account.viewBalance());
        }
    }
}

// SavingsAccount class implementing Account interface
class SavingsAccount implements Account {
    private double balance;
    private double interestRate = 0.05; // 5% interest rate

    public SavingsAccount(double balance) {
        this.balance = balance;
    }

    @Override
    public void deposit(double amount) {
        balance += amount;
        System.out.println("Deposited " + amount + " to Savings Account");
    }

    @Override
    public void withdraw(double amount) {
        if (balance >= amount) {
            balance -= amount;
            System.out.println("Withdrawn " + amount + " from Savings Account");
        } else {
            System.out.println("Insufficient funds in Savings Account");
        }
    }

    @Override
    public double calculateInterest() {
        return balance * interestRate;
    }

    @Override
    public double viewBalance() {
        return balance;
    }
}

// CurrentAccount class implementing Account interface
class CurrentAccount implements Account {
    private double balance;
    private double overdraftLimit = 5000; // Overdraft limit

    public CurrentAccount(double balance) {
        this.balance = balance;
    }

    @Override
    public void deposit(double amount) {
        balance += amount;
        System.out.println("Deposited " + amount + " to Current Account");
    }

    @Override
    public void withdraw(double amount) {
        if (balance + overdraftLimit >= amount) {
            balance -= amount;
            System.out.println("Withdrawn " + amount + " from Current Account");
        } else {
            System.out.println("Overdraft limit exceeded in Current Account");
        }
    }

    @Override
    public double calculateInterest() {
        return 0; // Current accounts typically don't earn interest
    }

    @Override
    public double viewBalance() {
        return balance;
    }
}

// Main class to test the system
public class BankingSystem {
    public static void main(String[] args) {
        Bank bank = new Bank();

        SavingsAccount savings = new SavingsAccount(1000);
        CurrentAccount current = new CurrentAccount(2000);

        bank.addAccount(savings);
        bank.addAccount(current);

        savings.deposit(500);
        current.withdraw(1000);

        bank.displayAccounts();
    }
}


// Interface for Searchable
interface Searchable {
    boolean search(String keyword);
}

// Document class implementing Searchable interface
class Document implements Searchable {
    private String content;

    public Document(String content) {
        this.content = content;
    }

    @Override
    public boolean search(String keyword) {
        return content.contains(keyword);
    }
}

// WebPage class implementing Searchable interface
class WebPage implements Searchable {
    private String htmlContent;

    public WebPage(String htmlContent) {
        this.htmlContent = htmlContent;
    }

    @Override
    public boolean search(String keyword) {
        return htmlContent.contains(keyword);
    }
}

// Main class to test the system
public class SearchSystem {
    public static void main(String[] args) {
        Document document = new Document("This is a sample document text.");
        WebPage webpage = new WebPage("<html>This is a sample webpage content</html>");

        String keyword = "sample";

        System.out.println("Document contains keyword: " + document.search(keyword));
        System.out.println("WebPage contains keyword: " + webpage.search(keyword));
    }
}

// Interface for Encryptable
interface Encryptable {
    String encrypt(String data);
    String decrypt(String encryptedData);
}

// AES encryption class
class AES implements Encryptable {
    @Override
    public String encrypt(String data) {
        return "AES Encrypted: " + data;  // Simple simulation for AES encryption
    }

    @Override
    public String decrypt(String encryptedData) {
        return "AES Decrypted: " + encryptedData.replace("AES Encrypted: ", "");
    }
}

// RSA encryption class
class RSA implements Encryptable {
    @Override
    public String encrypt(String data) {
        return "RSA Encrypted: " + data;  // Simple simulation for RSA encryption
    }

    @Override
    public String decrypt(String encryptedData) {
        return "RSA Decrypted: " + encryptedData.replace("RSA Encrypted: ", "");
    }
}

// Main class to test the system
public class EncryptionSystem {
    public static void main(String[] args) {
        Encryptable aesEncryptor = new AES();
        Encryptable rsaEncryptor = new RSA();

        String data = "SensitiveData";

        String aesEncrypted = aesEncryptor.encrypt(data);
        System.out.println(aesEncrypted);
        System.out.println(aesEncryptor.decrypt(aesEncrypted));

        String rsaEncrypted = rsaEncryptor.encrypt(data);
        System.out.println(rsaEncrypted);
        System.out.println(rsaEncryptor.decrypt(rsaEncrypted));
    }
}
