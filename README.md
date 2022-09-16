# rock-paper-scissor-2.0
This is a program for a level up version of rock paper scissor game in C programming.


#include <stdio.h>
#include <string.h>
#include <stdlib.h>
#include <time.h>

int generaterandomnumber(int n)
{
    srand(time(NULL));
    return rand() % n;
}
int main()
{
    int playerScore = 0, compScore = 0;
    char Name[20];
    static int win = 0;
    static int draw = 0;
    static int loose = 0;
    char dict[] = {'r', 'p', 's'};
    char c, t;
    int n;
    printf("Rock=r,Paper=p,Scissor=s\n");
    printf("Press 1 for Rock, 2 for Paper, 3 for Scissor\n");
    printf("Enter your name:\n");
    scanf("%s", Name);

    int i = 0;
    while (i < 3)
    {
        srand(time(NULL));
        int s = rand() % 3;
        printf("PLAYER 1: %s Turn\n", strupr(Name));
        scanf("%d", &n);
        c = dict[n - 1];
        printf("%s:%c\n", strupr(Name), c);
        printf("PLAYER 2: COMPUTER Turn\n");
        n = generaterandomnumber(3) + 1;
        t = dict[n - 1];
        printf("COMPUTER:%c\n", t);

        if (c == t)
        {
            printf("MATCH DRAWS AND BOTH GET 0 POINTS\n");
            draw++;
        }
        else if (c == 'p' && t == 'r' || c == 's' && t == 'p' || c == 'r' && t == 's')
        {
            printf("%s WINS AND GET 1 POINT\n", strupr(Name));
            win++;
        }
        else
        {
            printf("COMPUTER WINS AND GET 1 POINT\n");
            loose++;
        }
        i++;
    }

    printf("\n\n");

    if (win == 1 && draw == 1 && loose == 1 || draw == 3)
    {
        printf("MATCH IS DRAWN\n");
        printf("PLEASE TRY AGAIN\n");
    }
    else if (win == 2 || win == 1 && draw == 2)
    {
        printf("CONGRATULATIONS %s IS THE WINNER\n", strupr(Name));
    }
    else
    {
        printf("OOPS YOU LOOSE THE GAME\n");
    }

    return 0;
}
