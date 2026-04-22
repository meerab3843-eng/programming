#include <iostream>
#include <fstream>   // For file handling
using namespace std;

// Function Prototypes
void inputArray(int arr[], int size);        // Part (A)
void displayArray(int arr[], int size);      // Part (B)
int calculateSum(int arr[], int size);       // Part (B)
void writeToFile(int arr[], int size);       // Part (C)
void readFromFile(int arr[], int size);      // Part (D)

// ================= MAIN FUNCTION =================
int main() {
    const int SIZE = 10;
    int arr[SIZE];

    // Part (A): Input array elements
    inputArray(arr, SIZE);

    // Part (B): Display array
    cout << "\nArray Elements are:\n";
    displayArray(arr, SIZE);

    // Part (E): Calculate sum using value-returning function
    int sum = calculateSum(arr, SIZE);
    cout << "\nSum of array elements = " << sum << endl;

    // Part (C): Write array to file
    writeToFile(arr, SIZE);

    // Part (D): Read array from file and display
    cout << "\nReading data from file:\n";
    readFromFile(arr, SIZE);

    return 0;
}

// ================= FUNCTION DEFINITIONS =================

// Function to input values into array
// Demonstrates parameter passing (array passed by reference)
void inputArray(int arr[], int size) {
    cout << "Enter " << size << " elements:\n";
    for(int i = 0; i < size; i++) {
        cout << "Element " << i + 1 << ": ";
        cin >> arr[i];
    }
}

// Function to display array elements
void displayArray(int arr[], int size) {
    for(int i = 0; i < size; i++) {
        cout << arr[i] << " ";
    }
    cout << endl;
}

// Function to calculate sum (value-returning function)
int calculateSum(int arr[], int size) {
    int sum = 0;
    for(int i = 0; i < size; i++) {
        sum += arr[i];
    }
    return sum;   // Returning the result
}

// Function to write array data into a file
void writeToFile(int arr[], int size) {
    ofstream outFile("array.txt");  // Creating file

    if(!outFile) {
        cout << "Error opening file for writing!\n";
        return;
    }

    for(int i = 0; i < size; i++) {
        outFile << arr[i] << " ";
    }

    outFile.close(); // Closing file
    cout << "\nData successfully written to file.\n";
}

// Function to read array data from file and display it
void readFromFile(int arr[], int size) {
    ifstream inFile("array.txt");  // Opening file

    if(!inFile) {
        cout << "Error opening file for reading!\n";
        return;
    }

    for(int i = 0; i < size; i++) {
        inFile >> arr[i];
    }

    inFile.close(); // Closing file

    cout << "Data read from file:\n";
    displayArray(arr, size);
}
