# Bank-Management-System-Using-C-
#include <iostream>
#include <string>
using namespace std;

class BankAccount {
private:
    string name;
    double balance;

public:
    // Constructor
    BankAccount(string accountName, double initialBalance) {
        name = accountName;
        balance = initialBalance;
    }

    // Deposit money
    void deposit(double amount) {
        if (amount > 0) {
            balance += amount;
            cout << "Successfully deposited $" << amount << endl;
        } else {
            cout << "Invalid deposit amount!" << endl;
        }
    }

    // Withdraw money
    void withdraw(double amount) {
        if (amount > 0 && amount <= balance) {
            balance -= amount;
            cout << "Successfully withdrew $" << amount << endl;
        } else {
            cout << "Insufficient funds or invalid amount!" << endl;
        }
    }

    // Display account details
    void display() {
        cout << "\n----- Account Details -----" << endl;
        cout << "Account Holder: " << name << endl;
        cout << "Current Balance: $" << balance << endl;
        cout << "---------------------------\n" << endl;
    }
};

int main() {
    string name;
    double initialDeposit;
    int choice;
    double amount;

    cout << "===== Bank Management System =====" << endl;
    cout << "Enter your name: ";
    getline(cin, name);

    cout << "Enter initial deposit amount: $";
    cin >> initialDeposit;

    // Create the account
    BankAccount account(name, initialDeposit);
    cout << "\nAccount created successfully!\n" << endl;

    do {
        cout << "1. Deposit" << endl;
        cout << "2. Withdraw" << endl;
        cout << "3. Display Balance" << endl;
        cout << "4. Exit" << endl;
        cout << "Enter your choice: ";
        cin >> choice;

        switch (choice) {
            case 1:
                cout << "Enter amount to deposit: $";
                cin >> amount;
                account.deposit(amount);
                break;

            case 2:
                cout << "Enter amount to withdraw: $";
                cin >> amount;
                account.withdraw(amount);
                break;

            case 3:
                account.display();
                break;

            case 4:
                cout << "Thank you for using the Bank Management System. Goodbye!" << endl;
                break;

            default:
                cout << "Invalid choice! Please try again." << endl;
        }

    } while (choice != 4);

    return 0;
}