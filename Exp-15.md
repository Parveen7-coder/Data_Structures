#include <stdio.h>
#define SIZE 10  // Size of the hash table

int hashTable[SIZE];

// Initialize hash table with -1 (empty)
void initialize() {
    for(int i = 0; i < SIZE; i++)
        hashTable[i] = -1;
}

// Hash function
int hash(int key) {
    return key % SIZE;
}

// Insert element using linear probing
void insert(int key) {
    int index = hash(key);
    int originalIndex = index;
    while(hashTable[index] != -1) {  // While slot is not empty
        index = (index + 1) % SIZE;  // Move to next slot
        if(index == originalIndex) {
            printf("Hash Table Overflow! Cannot insert %d\n", key);
            return;
        }
    }
    hashTable[index] = key;
    printf("%d inserted at index %d\n", key, index);
}

// Search element in hash table
void search(int key) {
    int index = hash(key);
    int originalIndex = index;
    while(hashTable[index] != -1) {
        if(hashTable[index] == key) {
            printf("%d found at index %d\n", key, index);
            return;
        }
        index = (index + 1) % SIZE;
        if(index == originalIndex) break;  // Came full circle
    }
    printf("%d not found in hash table\n", key);
}

// Display hash table
void display() {
    printf("Hash Table: \n");
    for(int i = 0; i < SIZE; i++)
        printf("Index %d: %d\n", i, hashTable[i]);
}

int main() {
    initialize();
    int choice, key;

    do {
        printf("\n--- Linear Probing Hash Table ---\n");
        printf("1. Insert\n");
        printf("2. Search\n");
        printf("3. Display\n");
        printf("4. Exit\n");
        printf("Enter your choice: ");
        scanf("%d", &choice);

        switch(choice) {
            case 1:
                printf("Enter key to insert: ");
                scanf("%d", &key);
                insert(key);
                break;
            case 2:
                printf("Enter key to search: ");
                scanf("%d", &key);
                search(key);
                break;
            case 3:
                display();
                break;
            case 4:
                printf("Exiting...\n");
                break;
            default:
                printf("Invalid choice! Try again.\n");
        }
    } while(choice != 4);

    return 0;
}
