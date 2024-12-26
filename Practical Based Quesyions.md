### **Write a program to move all zeros to the end of an array while maintaining the relative order of non-zero elements.**

```cpp
#include <iostream>
using namespace std;

int main() {
    int arr[] = {0, 1, 0, 3, 12, 0, 5, 6};
    int n = sizeof(arr) / sizeof(arr[0]);
    int index = 0; // Position for placing non-zero elements

    cout << "Original array: ";
    for (int i = 0; i < n; i++) {
        cout << arr[i] << " ";
    }
    cout << endl;

    // Move non-zero elements to the front
    for (int i = 0; i < n; i++) {
        if (arr[i] != 0) {
            arr[index] = arr[i];
            index++;
        }
    }

    // Fill remaining positions with zeros
    for (int i = index; i < n; i++) {
        arr[i] = 0;
    }

    cout << "Modified array: ";
    for (int i = 0; i < n; i++) {
        cout << arr[i] << " ";
    }
    cout << endl;

    return 0;
}
```

### Explanation:
1. **Step 1**: Print the original array.
2. **Step 2**: Traverse the array, moving all non-zero elements to the beginning (`index` keeps track of the next position for a non-zero element).
3. **Step 3**: After processing all elements, set the remaining positions to zero.
4. **Step 4**: Print the modified array.

### Output:
For the input `{0, 1, 0, 3, 12, 0, 5, 6}`:
```
Original array: 0 1 0 3 12 0 5 6 
Modified array: 1 3 12 5 6 0 0 0 
``` 


### Bank Code

```cpp
#include <iostream>
#include <string>
using namespace std;

struct Bank {
    static int acc_num;
    string name, gender;
    int age, amount, pin;
    bool status;

    // Constructor equivalent in struct
    void create(string name, string gender, int age, int amount) {
        this->name = name;
        this->gender = gender;
        this->age = age;
        this->amount = amount;
        this->status = false;
        acc_num++;
    }

    void set_pin(int pin) {
        this->pin = pin;
        this->status = true;
    }

    void deposit() {
        int deposit_amount;
        cout << "How much money would you like to deposit? ";
        cin >> deposit_amount;
        amount += deposit_amount;
        cout << "Great, you have successfully deposited Rs. " << deposit_amount << endl;
    }

    void withdraw() {
        int withdraw_amount;
        cout << "How much money would you like to withdraw? ";
        cin >> withdraw_amount;
        if (amount < withdraw_amount) {
            cout << "Sorry. Your balance is too low." << endl;
        } else if (amount - withdraw_amount < 3000) {
            cout << "You have to have a minimum of Rs. 3000 in your account." << endl;
        } else {
            amount -= withdraw_amount;
            cout << "You have successfully withdrawn Rs. " << withdraw_amount << endl;
        }
    }

    void check_balance() {
        cout << "You have Rs. " << amount << " in your account." << endl;
    }

    void reset_pin() {
        int old_pin;
        cout << "Please enter your old pin: ";
        cin >> old_pin;
        if (old_pin != pin) {
            cout << "Invalid pin. We are not able to reset your pin." << endl;
        } else {
            int new_pin, new_pin_confirm;
            cout << "Please enter your new 4-digit pin: ";
            cin >> new_pin;
            cout << "Please re-enter your pin: ";
            cin >> new_pin_confirm;
            if (new_pin != new_pin_confirm) {
                cout << "The two pins do not match. We cannot reset your pin." << endl;
            } else {
                pin = new_pin;
                cout << "Great! Your pin has been reset!" << endl;
            }
        }
    }
};

int Bank::acc_num = 2024100;

int main() {
    Bank all_bankers[100];  // Array to store up to 100 bankers
    int total_accounts = 0;
    char choice = 'a';

    while (choice != 'q') {
        cout << "1. Create an account\n2. Access your account\nq. Quit" << endl;
        cout << "Choose an option: ";
        cin >> choice;

        if (choice == '1') {
            string name, gender;
            int age, amount;
            char amt_choice;

            cout << "Name: ";
            cin >> name;
            cout << "Gender (M/F): ";
            cin >> gender;
            cout << "Age: ";
            cin >> age;
            cout << "Do you have more than Rs. 3000 to deposit (y/n)? ";
            cin >> amt_choice;

            if (amt_choice == 'n') {
                cout << "Sorry we cannot create an account for you." << endl;
                continue;
            }

            cout << "How much money do you have to deposit? ";
            cin >> amount;

            while (amount <= 3000) {
                cout << "Please enter a number greater than 3000: ";
                cin >> amount;
            }

            all_bankers[total_accounts].create(name, gender, age, amount);
            cout << "Your account has been created. Your account number is " << Bank::acc_num << endl;
            total_accounts++;

        } else if (choice == '2') {
            int acc, pin;
            bool found = false;
            int index = -1;

            cout << "Enter your account number please: ";
            cin >> acc;

            // Search for the account in the array
            for (int i = 0; i < total_accounts; i++) {
                if (Bank::acc_num - total_accounts + i == acc) {
                    found = true;
                    index = i;
                    break;
                }
            }

            if (!found) {
                cout << "Invalid account number." << endl;
                continue;
            }

            Bank* current = &all_bankers[index];

            if (!current->status) {
                char set_pin_choice;
                cout << "We can see you have not set your pin. Do you want to set it right now (y/n)? ";
                cin >> set_pin_choice;

                if (set_pin_choice == 'y') {
                    cout << "Please enter your four digit pin: ";
                    cin >> pin;
                    current->set_pin(pin);
                    cout << "Great! Your pin is set!" << endl;
                } else {
                    cout << "Sorry, we cannot access your account!" << endl;
                    continue;
                }
            } else {
                cout << "Please enter your pin: ";
                cin >> pin;
                int attempts = 0;
                bool correct = false;

                while (attempts < 2 && pin != current->pin) {
                    cout << "Invalid pin. Please enter your pin: ";
                    cin >> pin;
                    attempts++;
                }

                if (pin == current->pin) {
                    correct = true;
                }

                if (!correct) {
                    cout << "We could not access your account." << endl;
                    continue;
                }
            }

            cout << "Welcome, " << current->name << endl;
            char choice2 = 'x';

            while (choice2 != 'b') {
                cout << "What would you like to do today? " << endl;
                cout << "1. Deposit\n2. Withdraw\n3. Check Balance\n4. Reset Pin\nb. Back to Main Menu" << endl;
                cout << "Enter your choice: ";
                cin >> choice2;

                if (choice2 == '1') {
                    current->deposit();
                    current->check_balance();
                } else if (choice2 == '2') {
                    current->withdraw();
                    current->check_balance();
                } else if (choice2 == '3') {
                    current->check_balance();
                } else if (choice2 == '4') {
                    current->reset_pin();
                } else if (choice2 != 'b') {
                    cout << "Please choose a valid option: 1, 2, 3, 4, b" << endl;
                }
            }
        } else if (choice == 'q') {
            cout << "Thank you for joining us today!" << endl;
        } else {
            cout << "Please choose a valid option: 1, 2, q." << endl;
        }
    }

    return 0;
}
```

