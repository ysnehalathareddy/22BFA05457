#include <stdio.h>
#include <stdlib.h>

struct Queue {
    int* arr;
    int front;
    int rear;
    int capacity;
};

// Function prototypes
void initQueue(struct Queue* queue, int capacity);
int isFull(struct Queue* queue);
int isEmpty(struct Queue* queue);
void push(struct Queue* queue, int value);
int pop(struct Queue* queue);
int peek(struct Queue* queue);
int size(struct Queue* queue);
void printElements(struct Queue* queue);

int main() {
    struct Queue queue;
    int capacity;

    // Ask the user for the capacity of the queue
    printf("Enter the capacity of the queue: ");
    scanf("%d", &capacity);

    // Initialize the queue with the user-defined capacity
    initQueue(&queue, capacity);

    int choice, value;

    while (1) {
        printf("\nMenu:\n");
        printf("1. Enqueue (Push)\n");
        printf("2. Dequeue (Pop)\n");
        printf("3. Peek\n");
        printf("4. Size\n");
        printf("5. Is Empty\n");
        printf("6. Is Full\n");
        printf("7. Print Elements\n");
        printf("8. Exit\n");
        printf("Enter your choice: ");
        scanf("%d", &choice);

        switch (choice) {
            case 1:
                printf("Enter value to enqueue: ");
                scanf("%d", &value);
                push(&queue, value);
                break;
            case 2:
                value = pop(&queue);
                if (value != -1) {
                    printf("Dequeued element: %d\n", value);
                }
                break;
            case 3:
                value = peek(&queue);
                if (value != -1) {
                    printf("Front element: %d\n", value);
                }
                break;
            case 4:
                printf("Size of the queue: %d\n", size(&queue));
                break;
            case 5:
                if (isEmpty(&queue)) {
                    printf("Queue is empty.\n");
                } else {
                    printf("Queue is not empty.\n");
                }
                break;
            case 6:
                if (isFull(&queue)) {
                    printf("Queue is full.\n");
                } else {
                    printf("Queue is not full.\n");
                }
                break;
            case 7:
                printElements(&queue);
                break;
            case 8:
                printf("Exiting...\n");
                free(queue.arr); // Free dynamically allocated memory before exit
                exit(0);
            default:
                printf("Invalid choice! Please try again.\n");
        }
    }

    return 0;
}

// Function to initialize the queue with user-defined capacity
void initQueue(struct Queue* queue, int capacity) {
    queue->capacity = capacity;
    queue->front = 0;
    queue->rear = -1;
    queue->arr = (int*)malloc(capacity * sizeof(int)); // Dynamically allocate memory for queue
    if (queue->arr == NULL) {
        printf("Memory allocation failed!\n");
        exit(1);
    }
}

// Function to check if the queue is full
int isFull(struct Queue* queue) {
    return queue->rear == queue->capacity - 1;
}

// Function to check if the queue is empty
int isEmpty(struct Queue* queue) {
    return queue->front > queue->rear;
}

// Function to enqueue (push) an element into the queue
void push(struct Queue* queue, int value) {
    if (isFull(queue)) {
        printf("Queue overflow! Cannot enqueue %d\n", value);
        return;
    }
    queue->arr[++queue->rear] = value;
    printf("Enqueued element: %d\n", value);
}

// Function to dequeue (pop) an element from the queue
int pop(struct Queue* queue) {
    if (isEmpty(queue)) {
        printf("Queue underflow! Queue is empty.\n");
        return -1;
    }
    int dequeuedValue = queue->arr[queue->front++];
    return dequeuedValue;
}

// Function to peek at the front element of the queue
int peek(struct Queue* queue) {
    if (isEmpty(queue)) {
        printf("Queue is empty.\n");
        return -1;
    }
    return queue->arr[queue->front];
}

// Function to get the size of the queue
int size(struct Queue* queue) {
    return queue->rear - queue->front + 1;
}

// Function to print all the elements in the queue
void printElements(struct Queue* queue) {
    if (isEmpty(queue)) {
        printf("Queue is empty.\n");
        return;
    }
    printf("Queue elements: ");
    for (int i = queue->front; i <= queue->rear; i++) {
        printf("%d ", queue->arr[i]);
    }
    printf("\n");
}
