# C-DSA-ASSESSMENT-
#include <stdio.h>

// MAX defines the maximum size of the stack
#define MAX 5

// Array used to implement the stack
int stack[MAX];

// TOP keeps track of the top element
// -1 means the stack is empty
int top = -1;


// PUSH OPERATION
// Push is used to insert an element into the stack.
// Stack follows LIFO: Last In, First Out.
void push(int x)
{
    // If top reaches MAX-1, the stack is full.
    // This condition is called Stack Overflow.
    if (top == MAX - 1)
    {
        printf("Stack Overflow!\n");
        return;
    }

    // Increase top and insert the element.
    top++;
    stack[top] = x;

    printf("%d pushed into stack.\n", x);
}


// POP OPERATION
// Pop is used to remove the top element from the stack.
void pop()
{
    // If top is -1, the stack is empty.
    // Removing from an empty stack is called Stack Underflow.
    if (top == -1)
    {
        printf("Stack Underflow!\n");
        return;
    }

    // Display the top element before removing it.
    printf("%d popped from stack.\n", stack[top]);

    // Decrease top to remove the element.
    top--;
}


// PEEK OPERATION
// Peek is used to view the top element
// without removing it.
void peek()
{
    // Check whether the stack is empty.
    if (top == -1)
    {
        printf("Stack is Empty!\n");
        return;
    }

    // Display the current top element.
    printf("Top element = %d\n", stack[top]);
}


// DISPLAY OPERATION
// Display shows all elements of the stack
// from TOP to the bottom.
void display()
{
    // Check whether the stack is empty.
    if (top == -1)
    {
        printf("Stack is Empty!\n");
        return;
    }

    printf("Stack elements are:\n");

    // Print elements from top to bottom.
    for (int i = top; i >= 0; i--)
    {
        printf("%d\n", stack[i]);
    }
}


// MAIN FUNCTION
// Program execution starts from main().
int main()
{
    int choice, x;

    // Menu runs continuously until the user selects EXIT.
    while (1)
    {
        printf("\n--- STACK MENU ---\n");
        printf("1. PUSH\n");
        printf("2. POP\n");
        printf("3. PEEK\n");
        printf("4. DISPLAY\n");
        printf("5. EXIT\n");

        // Take the user's choice.
        printf("Enter your choice: ");
        scanf("%d", &choice);

        // Switch performs the selected stack operation.
        switch (choice)
        {
            case 1:
                // Take an element and insert it into stack.
                printf("Enter element: ");
                scanf("%d", &x);
                push(x);
                break;

            case 2:
                // Remove the top element.
                pop();
                break;

            case 3:
                // View the top element.
                peek();
                break;

            case 4:
                // Display all stack elements.
                display();
                break;

            case 5:
                // Exit the program.
                return 0;

            default:
                // Runs when the user enters an invalid choice.
                printf("Invalid choice!\n");
        }
    }
}








#include <stdio.h>

// MAX defines the maximum size of the Circular Queue
#define MAX 5

// Array used to implement the Circular Queue
int queue[MAX];

// FRONT points to the first element
// REAR points to the last element
// -1 means the queue is empty
int front = -1;
int rear = -1;


// ENQUEUE OPERATION
// Enqueue is used to insert an element into the queue.
// Circular Queue follows FIFO: First In, First Out.
void enqueue(int x)
{
    // Check whether the Circular Queue is full.
    // % MAX allows REAR to move back to index 0.
    if ((rear + 1) % MAX == front)
    {
        printf("Circular Queue is Full!\n");
        return;
    }

    // If the queue is empty, set both FRONT and REAR to 0.
    if (front == -1)
    {
        front = 0;
        rear = 0;
    }
    else
    {
        // Move REAR to the next circular position.
        rear = (rear + 1) % MAX;
    }

    // Insert the new element at REAR.
    queue[rear] = x;

    printf("%d inserted into queue.\n", x);
}


// DEQUEUE OPERATION
// Dequeue is used to remove an element from the FRONT.
void dequeue()
{
    // If FRONT is -1, the queue is empty.
    // Removing from an empty queue is called Underflow.
    if (front == -1)
    {
        printf("Circular Queue is Empty!\n");
        return;
    }

    // Display the element before deleting it.
    printf("%d deleted from queue.\n", queue[front]);

    // If FRONT and REAR are equal,
    // there is only one element in the queue.
    if (front == rear)
    {
        // Reset both to -1 because the queue becomes empty.
        front = -1;
        rear = -1;
    }
    else
    {
        // Move FRONT to the next circular position.
        front = (front + 1) % MAX;
    }
}


// FRONT OPERATION
// This operation displays the first element
// without removing it.
void frontElement()
{
    // Check whether the queue is empty.
    if (front == -1)
    {
        printf("Queue is Empty!\n");
        return;
    }

    // Display the element present at FRONT.
    printf("Front element = %d\n", queue[front]);
}


// DISPLAY OPERATION
// This operation displays all elements
// from FRONT to REAR.
void display()
{
    // Check whether the queue is empty.
    if (front == -1)
    {
        printf("Queue is Empty!\n");
        return;
    }

    printf("Queue elements are: ");

    // Start displaying from FRONT.
    int i = front;

    while (1)
    {
        // Print current element.
        printf("%d ", queue[i]);

        // Stop when REAR is reached.
        if (i == rear)
            break;

        // Move to the next circular position.
        i = (i + 1) % MAX;
    }

    printf("\n");
}


// MAIN FUNCTION
// Program execution starts from main().
int main()
{
    int choice, x;

    // Menu continues until the user selects EXIT.
    while (1)
    {
        printf("\n--- CIRCULAR QUEUE MENU ---\n");
        printf("1. ENQUEUE\n");
        printf("2. DEQUEUE\n");
        printf("3. FRONT\n");
        printf("4. DISPLAY\n");
        printf("5. EXIT\n");

        // Take the user's choice.
        printf("Enter your choice: ");
        scanf("%d", &choice);

        // Perform operation according to user's choice.
        switch (choice)
        {
            case 1:
                // Take an element and insert it.
                printf("Enter element: ");
                scanf("%d", &x);
                enqueue(x);
                break;

            case 2:
                // Remove the front element.
                dequeue();
                break;

            case 3:
                // Display the front element.
                frontElement();
                break;

            case 4:
                // Display all queue elements.
                display();
                break;

            case 5:
                // Exit the