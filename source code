#include <iostream>
#include <fstream>
#include <chrono>
#include <iomanip>
#include <string>
using namespace std;

class Temp {
    string id, name,bname, author, search;
    fstream file;
    fstream file1;
    
public:
    void addBook();
    void showBooks();
    void extractBook();
    void borrowBook();
};

Temp obj;

int main() {
    char choice;
    do {
        cout << "----------------------------------" << endl;
        cout << "1-Show All Books" << endl;
        cout << "2-Extract Book" << endl;
        cout << "3-Add books(ADMIN)" << endl;
        cout << "4-Borrow book\n5-Exit" << endl;
        cout << "----------------------------------" << endl;
        cout << "Enter Your Choice :: ";
        cin >> choice;

        switch (choice) {
        case '1':
            cin.ignore();
            obj.showBooks();
            break;
        case '2':
            cin.ignore();
            obj.extractBook();
            break;
        case '3':
            cin.ignore();
            obj.addBook();
            break;
        case '4':
            cin.ignore();
            obj.borrowBook();
        case '5':
            return 0;
        default:
            cout << "Invalid Choice...!" << endl;
        }
    } while (choice != '5');

    return 0;
}

void Temp::addBook() 
{
    cout << "\nEnter Book ID :: ";
    getline(cin, id);
    cout << "Enter Book Name :: ";
    getline(cin, name);
    cout << "Enter Book's Author Name :: ";
    getline(cin, author);

    file.open("bookData.txt", ios::out | ios::app);
    if (file.is_open()) {
        file << id << "\t" << name << "\t" << author << endl;
        file.close();
    } else {
        cout << "Unable to open file for writing." << endl;
    }
}

void Temp::showBooks() 
{
    file.open("bookData.txt", ios::in);
    if (file.is_open()) {
        cout << "\n\n";
        cout << "\t\t Book Id \t\t Book Name \t\t Author's Name" << endl;
        cout << "---------------------------------------------------------------" << endl;
        while (getline(file, id, '\t')) {
            getline(file, name, '\t');
            getline(file, author);
            cout << "\t\t " << id << "\t\t " << name << "\t\t " << author << endl;
        }
        file.close();
    } else {
        cout << "Unable to open file for reading." << endl;
    }
}

void Temp::extractBook() 
{
    cout << "Enter Book Id :: ";
    getline(cin, search);

    file.open("bookData.txt", ios::in);
    if (file.is_open()) {
        bool found = false;
        cout << "\n\n";
        cout << "\t\t Book Id \t\t Book Name \t\t Author's Name" << endl;
        cout << "---------------------------------------------------------------" << endl;
        while (getline(file, id, '\t')) {
            getline(file, name, '\t');
            getline(file, author);
            if (search == id) {
                cout << "\t\t " << id << "\t\t " << name << "\t\t " << author << endl;
                found = true;
                break;
            }
        }
        if (!found) {
            cout << "Book not found." << endl;
        }
        file.close();
    } else {
        cout << "Unable to open file for reading." << endl;
    }
}
void Temp::borrowBook()
{
    cout << "\nEnter Book ID :: ";
    getline(cin, id);
    cout << "Enter Borrower Name :: ";
    getline(cin, bname);

    file1.open("borrow.txt", ios::out | ios::app);
    if (file1.is_open()) {
        file1 << id << "\t\t" << bname << "\t\t" ;
        auto now = chrono::system_clock::now();
        time_t currentTime = chrono::system_clock::to_time_t(now);
        file1  << put_time(localtime(&currentTime), "%Y-%m-%d") <<endl;
        file1.close();
    } else {
        cout << "Unable to open file for writing." << endl;
    }
}
