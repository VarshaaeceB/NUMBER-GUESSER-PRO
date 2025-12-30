# NUMBER-GUESSER-PRO
#include <stdio.h>
#include <stdlib.h>
void playGame(int *targetNumber, int *maxAttempts) {
    int *guess;
    int *attempts;
    guess = (int *)malloc(sizeof(int));
    attempts = (int *)malloc(sizeof(int));
    *attempts = 0;
    printf("\n Number Guesser Game \n");
    printf("Guess the number between 1 and 100\n");
    printf("You have %d attempts\n\n", *maxAttempts);
    while (*attempts < *maxAttempts) {
        printf("Enter your guess: ");
        scanf("%d", guess);
        (*attempts)++;
        if (*guess > *targetNumber) {
            printf("Too High!\n");
        } 
        else if (*guess < *targetNumber) {
            printf("Too Low!\n");
        } 
        else {
            printf("\n Correct! You guessed the number in %d attempts.\n", *attempts);
            free(guess);
            free(attempts);
            return;
        }
    }
    printf("\n Attempts Over!\n");
    printf("The correct number was: %d\n", *targetNumber);
    free(guess);
    free(attempts);
}
int main() {
    int *targetNumber;
    int *maxAttempts;
    int choice;
    targetNumber = (int *)malloc(sizeof(int));
    maxAttempts = (int *)malloc(sizeof(int));
    *targetNumber = rand() % 100 + 1;
    *maxAttempts = 5;
    printf(" NUMBER GUESSER PROJECT \n");
    do {
       playGame(targetNumber, maxAttempts);
        printf("\nPlay again?\n1. Yes\n0. No\nEnter choice: ");
        scanf("%d", &choice);
        if (choice == 1) {
            *targetNumber = rand() % 100 + 1;
        }

    } while (choice == 1);

    free(targetNumber);
    free(maxAttempts);

    printf("\nThank you for playing! \n");
    return 0;
}
