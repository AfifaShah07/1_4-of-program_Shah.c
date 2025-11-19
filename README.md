#include <stdio.h>
#include <stdlib.h>

#define MAX 50

int arr[MAX];
int front1 = -1, rear1 = -1;     // Queue 1 (left side)
int front2 = MAX, rear2 = MAX;   // Queue 2 (right side)

// Enqueue in Queue 1
void enqueue1(int value) {
    if (rear1 + 1 == rear2) {
        printf("Queue Overflow!\n");
    } else {
        if (front1 == -1)
            front1 = 0;
        rear1++;
        arr[rear1] = value;
        printf("%d inserted into Queue 1\n", value);
    }
}

// Enqueue in Queue 2
void enqueue2(int value) {
    if (rear2 - 1 == rear1) {
        printf("Queue Overflow!\n");
    } else {
        if (front2 == MAX)
            front2 = MAX - 1;
        rear2--;
        arr[rear2] = value;
        printf("%d inserted into Queue 2\n", value);
    }
}

// Dequeue from Queue 1
void dequeue1() {
    if (front1 == -1 || front1 > rear1) {
        printf("Queue 1 Underflow!\n");
    } else {
        printf("%d removed from Queue 1\n", arr[front1]);
        front1++;
    }
}

// Dequeue from Queue 2
void dequeue2() {
    if (front2 == MAX || front2 < rear2) {
        printf("Queue 2 Underflow!\n");
    } else {
        printf("%d removed from Queue 2\n", arr[front2]);
        front2--;
    }
}

// Display Queue 1
void display1() {
    if (front1 == -1 || front1 > rear1) {
        printf("Queue 1 is empty!\n");
    } else {
        printf("Queue 1 elements:\n");
        for (int i = front1; i <= rear1; i++) {
            printf("%d ", arr[i]);
        }
        printf("\n");
    }
}

// Display Queue 2
void display2() {
    if (front2 == MAX || front2 < rear2) {
        printf("Queue 2 is empty!\n");
    } else {
        printf("Queue 2 elements:\n");
        for (int i = front2; i >= rear2; i--) {
            printf("%d ", arr[i]);
        }
        printf("\n");
    }
}

int main() {
    int choice, value;

    while (1) {
        printf("\n--- Two Queues Menu ---\n");
        printf("1. Enqueue Queue 1\n");
        printf("2. Enqueue Queue 2\n");
        printf("3. Dequeue Queue 1\n");
        printf("4. Dequeue Queue 2\n");
        printf("5. Display Queue 1\n");
        printf("6. Display Queue 2\n");
        printf("7. Exit\n");
        printf("Enter your choice: ");
        scanf("%d", &choice);

        switch (choice) {
            case 1:
                printf("Enter value: ");
                scanf("%d", &value);
                enqueue1(value);
                break;

            case 2:
                printf("Enter value: ");
                scanf("%d", &value);
                enqueue2(value);
                break;

            case 3:
                dequeue1();
                break;

            case 4:
                dequeue2();
                break;

            case 5:
                display1();
                break;

            case 6:
                display2();
                break;

            case 7:
                exit(0);

            default:
                printf("Invalid choice!\n");
        }
    }

    return 0;
}
# 1_4-of-program_Shah.c
Two Queues using single array
