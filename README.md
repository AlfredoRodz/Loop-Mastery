#include <iostream>
#include <string>
#include <limits>  // for input validation

using namespace std;

// Function for factorial calculation using a while loop
int factorial(int n) {
    int result = 1;
    while (n > 1) {
        result *= n;
        n--;
    }
    return result;
}

// Function to print a number pyramid using nested for loops
void numberPyramid(int rows) {
    for (int i = 1; i <= rows; i++) {
        // Print leading spaces
        for (int j = i; j < rows; j++) {
            cout << " ";
        }
        // Print numbers
        for (int k = 1; k <= i; k++) {
            cout << k << " ";
        }
        cout << endl;
    }
}

// Function to sum even or odd numbers up to a limit using a do-while loop
void sumEvenOrOdd(bool even) {
    int sum = 0;
    int limit;
    cout << "Enter the upper limit: ";
    while (!(cin >> limit) || limit <= 0) {  // input validation
        cout << "Please enter a valid positive integer for the upper limit: ";
        cin.clear(); // clear error flag
        cin.ignore(numeric_limits<streamsize>::max(), '\n'); // discard invalid input
    }

    int i = (even) ? 2 : 1; // start with either 2 (even) or 1 (odd)
    do {
        sum += i;
        i += 2; // increment by 2 to keep it even/odd
    } while (i <= limit);

    cout << "Sum is: " << sum << endl;
}

// Function to reverse a string using a while loop
string reverseString(const string& input) {
    string reversed = "";
    int i = input.length() - 1;
    while (i >= 0) {
        reversed += input[i];
        i--;
    }
    return reversed;
}

// Function to exit the program
void exitProgram() {
    cout << "Goodbye! Thank you for using the Interactive Math & String Utility Program." << endl;
}

int main() {
    int choice;
    do {
        // Display Menu
        cout << "========= Interactive Utility Program =========\n";
        cout << "1. Factorial Calculator\n";
        cout << "2. Number Pyramid\n";
        cout << "3. Sum of Even or Odd Numbers\n";
        cout << "4. Reverse a String\n";
        cout << "5. Exit\n";
        cout << "==============================================\n";
        cout << "Enter your choice (1-5): ";
        
        while (!(cin >> choice) || choice < 1 || choice > 5) {  // input validation
            cout << "Please enter a valid choice between 1 and 5: ";
            cin.clear(); // clear error flag
            cin.ignore(numeric_limits<streamsize>::max(), '\n'); // discard invalid input
        }

        switch (choice) {
            case 1: {
                int n;
                cout << "Enter a positive integer: ";
                while (!(cin >> n) || n <= 0) {  // input validation
                    cout << "Please enter a valid positive integer: ";
                    cin.clear(); // clear error flag
                    cin.ignore(numeric_limits<streamsize>::max(), '\n'); // discard invalid input
                }
                cout << "Factorial of " << n << " is: " << factorial(n) << endl;
                break;
            }
            case 2: {
                int rows;
                cout << "Enter number of rows: ";
                while (!(cin >> rows) || rows <= 0) {  // input validation
                    cout << "Please enter a valid positive integer for rows: ";
                    cin.clear(); // clear error flag
                    cin.ignore(numeric_limits<streamsize>::max(), '\n'); // discard invalid input
                }
                numberPyramid(rows);
                break;
            }
            case 3: {
                char choice;
                cout << "Sum of (E)ven or (O)dd numbers? (Enter E for even, O for odd): ";
                cin >> choice;
                bool even = (choice == 'E' || choice == 'e');
                sumEvenOrOdd(even);
                break;
            }
            case 4: {
                cin.ignore();  // clear the newline character from previous input
                string str;
                cout << "Enter a string (with spaces if needed): ";
                getline(cin, str);  // use getline to allow multi-word input
                cout << "Reversed string: " << reverseString(str) << endl;
                break;
            }
            case 5:
                exitProgram();
                break;
            default:
                cout << "Invalid choice, please try again.\n";
        }
    } while (choice != 5);

    return 0;
}
