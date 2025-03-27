#include <iostream>
#include <algorithm>
#include <limits>
using namespace std;

template <typename T>
class StatisticalCalculation {
private:
    T* data;
    int size;

public:
    StatisticalCalculation(int size) : size(size) {
        data = new T[size];
    }

    ~StatisticalCalculation() {
        delete[] data;
    }

    void inputData() {
        for (int i = 0; i < size; i++) {
            cout << "Enter element " << i + 1 << ": ";
            while (!(cin >> data[i])) {
                cout << "Invalid input. Please enter a valid number: ";
                cin.clear();
                cin.ignore(numeric_limits<streamsize>::max(), '\n');
            }
        }
    }

    void sort() {
        // Insertion Sort algo
        for (int i = 1; i < size; i++) {
            T key = data[i];
            int j = i - 1;
            while (j >= 0 && data[j] > key) {
                data[j + 1] = data[j];
                j--;
            }
            data[j + 1] = key;
        }
    }

    double findMedian() { //in classroom the TA said to change the return type from T to double
        sort();
        if (size % 2 == 0)
            return (data[size / 2 - 1] + data[size / 2] ) / 2.0;
        else
            return data[size / 2];
    }

    T findMin() {
        return *min_element(data, data + size);
    }

    T findMax() {
        return *max_element(data, data + size);
    }

    double findMean() {
        T sum = findSummation();
        return static_cast<double>(sum) / size;
    }

    T findSummation() {
        T sum = 0;
        for (int i = 0; i < size; i++) {
            sum += data[i];
        }
        return sum;
    }

    void displayArray() {
        cout << "Sorted array: ";
        for (int i = 0; i < size; i++) {
            cout << data[i] << " ";
        }
        cout << endl;
    }

    void statisticsMenu() {
        string choice;
        do {
            cout << "\nSelect a statistical calculation:\n";
            cout << "1. Find Median\n";
            cout << "2. Find Minimum\n";
            cout << "3. Find Maximum\n";
            cout << "4. Find Mean\n";
            cout << "5. Find Summation\n";
            cout << "6. Exit\n";
            cout << "Enter your choice (1-6): ";
            cin >> choice;

            if(choice == "1") cout << "Median: " << findMedian() << endl;
            else if(choice == "2") cout << "Minimum: " << findMin() << endl;
            else if(choice == "3") cout << "Maximum: " << findMax() << endl;
            else if(choice == "4") cout << "Mean: " << findMean() << endl;
            else if(choice == "5") cout << "Summation: " << findSummation() << endl;
            else if(choice =="6")  cout << "Exiting program...\n";
            else cout << "Invalid choice! Please enter a valid option.\n";



        } while (choice != "6");
    }
};

int main() {
    int n;
    cout << "Enter the number of elements: ";
    //validate that number of elements n is a positive integer
    while (true) {
        cin >> n;
        if (cin.fail() || n <= 0) {
            cout << "Invalid input. Please enter a positive integer: ";
            cin.clear();
            cin.ignore(numeric_limits<streamsize>::max(), '\n');
        } else {
            break;
        }
    }

    StatisticalCalculation<double> stats(n); // Changed to double
    stats.inputData();
    stats.statisticsMenu();

    return 0;
}


//todo
//1) test cases file
//2) file function
//3) defensive programming
//4) sorting (DONE)
//5) datatype menu
