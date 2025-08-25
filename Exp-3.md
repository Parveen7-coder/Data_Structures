#include <stdio.h>

int main() {
    int n, i;
    unsigned long long factorial = 1;  // Use long long to handle large factorials

    printf("Enter a number: ");
    scanf("%d", &n);

    if (n < 0) {
        printf("Factorial is not defined for negative numbers.\n");
    } else {
        for(i = 1; i <= n; i++) {
            factorial *= i;  // Multiply factorial by i in each iteration
        }
        printf("Factorial of %d is %llu\n", n, factorial);
    }

    return 0;
}
