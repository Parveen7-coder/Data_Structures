#include <stdio.h>

int main() {
    int n, i, num;

    // Ask user for how many numbers they want to input
    printf("Enter the number of elements: ");
    scanf("%d", &n);

    for(i = 1; i <= n; i++) {
        printf("Enter number %d: ", i);
        scanf("%d", &num);

        if(num % 2 == 0) {
            printf("%d is Even\n", num);
        } else {
            printf("%d is Odd\n", num);
        }
    }

    return 0;
}
