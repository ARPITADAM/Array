# Array
#include <stdio.h>

int main() {
    int MAX_SIZE;
    printf("Enter the size of the array: ");
    scanf("%d", &MAX_SIZE);

    int arr[MAX_SIZE];
    int n = 0;
    int choice, value, index, i, found;
    char cont;

    do {
        printf("\n1. Insert a number (at end or specific index)\n");
        printf("2. Update a number by index\n");
        printf("3. Delete a number by index\n");
        printf("4. Search for a number\n");
        printf("5. Find largest and smallest number\n");
        printf("6. Exit\n");
        printf("Enter your choice: ");
        scanf("%d", &choice);

        switch (choice) {
            case 1:
                if (n >= MAX_SIZE) {
                    printf("Array is full!\n");
                } else {
                    printf("Enter the number to insert: ");
                    scanf("%d", &value);

                    printf("Do you want to insert at a specific index? (1 = Yes, 0 = No): ");
                    int opt;
                    scanf("%d", &opt);

                    if (opt == 1) {
                        printf("Enter index (0 to %d): ", n);
                        scanf("%d", &index);
                        if (index >= 0 && index <= n) {
                            for (i = n; i > index; i--) {
                                arr[i] = arr[i - 1];
                            }
                            arr[index] = value;
                            n++;
                            printf("Inserted at index %d.\n", index);
                        } else {
                            printf("Invalid index!\n");
                        }
                    } else {
                        arr[n++] = value;
                        printf("Inserted at the end.\n");
                    }
                }
                break;

            case 2:
                printf("Enter index to update (0 to %d): ", n - 1);
                scanf("%d", &index);
                if (index >= 0 && index < n) {
                    printf("Enter new value: ");
                    scanf("%d", &value);
                    arr[index] = value;
                    printf("Updated successfully.\n");
                } else {
                    printf("Invalid index!\n");
                }
                break;

            case 3:
                printf("Enter index to delete (0 to %d): ", n - 1);
                scanf("%d", &index);
                if (index >= 0 && index < n) {
                    for (i = index; i < n - 1; i++) {
                        arr[i] = arr[i + 1];
                    }
                    n--;
                    printf("Deleted successfully.\n");
                } else {
                    printf("Invalid index!\n");
                }
                break;

            case 4:
                printf("Enter number to search: ");
                scanf("%d", &value);
                found = 0;
                for (i = 0; i < n; i++) {
                    if (arr[i] == value) {
                        printf("Found at index %d\n", i);
                        found = 1;
                        break;
                    }
                }
                if (!found) {
                    printf("Number not found.\n");
                }
                break;

            case 5:
                if (n == 0) {
                    printf("Array is empty!\n");
                } else {
                    int max = arr[0], min = arr[0];
                    for (i = 1; i < n; i++) {
                        if (arr[i] > max) max = arr[i];
                        if (arr[i] < min) min = arr[i];
                    }
                    printf("Largest: %d\nSmallest: %d\n", max, min);
                }
                break;

            case 6:
                printf("Goodbye!\n");
                return 0;

            default:
                printf("Invalid choice!\n");
        }

        printf("Current array: ");
        for (i = 0; i < n; i++) {
            printf("%d ", arr[i]);
        }
        printf("\n");

        printf("Do you want to perform another operation? (y/n): ");
        scanf(" %c", &cont);
    } while (cont == 'y' || cont == 'Y');

    printf("Program ended.\n");
    return 0;
}
