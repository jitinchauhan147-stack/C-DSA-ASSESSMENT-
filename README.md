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