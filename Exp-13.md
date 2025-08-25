#include <stdio.h>
#define MAX 100  // Maximum size of queue

int queue[MAX];
int front = -1, rear = -1;

// Function to add an element to the queue (ENQUEUE)
void enqueue(int value) {
    if(rear == MAX - 1) {
        printf("Queue Overflow! Cannot enqueue %d\n", value);
    } else {
        if(front == -1)  // If queue is empty
            front = 0;
        rear++;
        queue[rear] = value;
        printf("%d enqueued to queue\n", value);
    }
}

// Function to remove an element from the queue (DEQUEUE)
void dequeue() {
    if(front == -1 || front > rear) {
        printf("Queue Underflow! Queue is empty\n");
    } else {
        printf("%d dequeued from queue\n", queue[front]);
        front++;
    }
}

// Function to display the queue elements
void display() {
    if(front == -1 || front > rear) {
        printf("Queue is empty\n");
    } else {
        printf("Queue elements: ");
        for(int i = front; i <= rear; i++) {
            printf("%d ", queue[i]);
        }
        printf("\n");
    }
}

// Main function with menu
int main() {
    int choice, value;

    do {
        printf("\n--- Queue Operations ---\n");
        printf("1. Enqueue\n");
        printf("2. Dequeue\n");
        printf("3. Display Queue\n");
        printf("4. Exit\n");
        printf("Enter your choice: ");
        scanf("%d", &choice);

        switch(choice) {
            case 1:
                printf("Enter value to enqueue: ");
                scanf("%d", &value);
                enqueue(value);
                break;
            case 2:
                dequeue();
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
