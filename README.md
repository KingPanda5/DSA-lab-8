# DSA-lab-8
Exercise 1:
#include<iostream>
using namespace std;

// Recursive function to compute Ackermann's function
int Ackermann(int m, int n) {
    if (m == 0)
        return n + 1;  // Base case
    else if (n == 0)
        return Ackermann(m - 1, 1);  // Case when n == 0
    else
        return Ackermann(m - 1, Ackermann(m, n - 1)); 
}

int main() {
    int M = 2, N = 2;
    cout << "Ackermann(" << M << ", " << N << ") = " << Ackermann(M, N) << endl;
    return 0;
}

Exercise 2:
#include <iostream>
using namespace std;

// Recursive function to compute the sum of array elements
int sum(int a[], int size) {
    if (size == 0)  // Base case: no elements left
        return 0;
    return a[size - 1] + sum(a, size - 1); 
}

int main() {
    int arr[] = {1, 2, 3, 4};  
    int result = sum(arr, 4);  
    cout << "Sum of array elements: " << result << endl;  
    return 0;
}

Exercise 3:
#include <iostream>
using namespace std;

// Definition of a node in the linked list
struct Node {
    int data;
    Node* next;

    Node(int value) : data(value), next(nullptr) {}
};

// Recursive function to reverse the linked list
void reverse(Node** head) {
    // Base case: If the list is empty or has one node, do nothing
    if (*head == nullptr || (*head)->next == nullptr)
        return;

    // Recursive case: Reverse the rest of the list
    Node* rest = (*head)->next;
    reverse(&rest);

    // Fix the current node
    (*head)->next->next = *head;
    (*head)->next = nullptr;

    // Update the head pointer
    *head = rest;
}

// Helper function to print the linked list
void printList(Node* head) {
    while (head != nullptr) {
        cout << head->data << " ";
        head = head->next;
    }
    cout << endl;
}

// Helper function to append a node at the end of the list
void append(Node** head, int data) {
    Node* newNode = new Node(data);
    if (*head == nullptr) {
        *head = newNode;
        return;
    }

    Node* temp = *head;
    while (temp->next != nullptr) {
        temp = temp->next;
    }
    temp->next = newNode;
}

int main() {
    Node* head = nullptr;

    // Create a linked list: 1 -> 2 -> 3 -> 4
    append(&head, 1);
    append(&head, 2);
    append(&head, 3);
    append(&head, 4);

    cout << "Original List: ";
    printList(head);

    // Reverse the linked list
    reverse(&head);

    cout << "Reversed List: ";
    printList(head);

    return 0;
}
OUTPUT:
Original List: 1 2 3 4 
Reversed List: 4 3 2 1

Exercise 4:

#include <iostream>
using namespace std;

// Recursive function to compute binomial coefficient
int binomialCoefficient(int n, int k) {
    // Base cases
    if (k == 0 || k == n)
        return 1;
    
    // Recursive case
    return binomialCoefficient(n - 1, k - 1) + binomialCoefficient(n - 1, k);
}

int main() {
    int n, k;

    // Input values of n and k
    cout << "Enter n: ";
    cin >> n;
    cout << "Enter k: ";
    cin >> k;

    // Ensure valid input
    if (k > n || n < 0 || k < 0) {
        cout << "Invalid input! Ensure 0 <= k <= n." << endl;
        return 1;
    }

    // Compute and display the binomial coefficient
    cout << "C(" << n << ", " << k << ") = " << binomialCoefficient(n, k) << endl;

    return 0;
}



