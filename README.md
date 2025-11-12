#include <stdio.h>
#include <stdlib.h>
#include <time.h>

#define ROLLS 1000

int main()
{
    int result[13] = {0};
    int *p;
    p = result;
    int i;
    srand(time(0));


    for(i = 0; i < ROLLS; i++)
        {
        int d1 = rand() % 6 + 1;
        int d2 = rand() % 6 + 1;
        int total = d1 + d2;
        *(p + total) += 1;
     printf("Sum\tTimes\tSimulated %%\tMath %% (expected)\n");
    for(i = 2; i <= 12; i++)
        {
        double theo = 0.0;
        double sim;
          switch(i)
        {
            case 2: case 12: theo = 2.31;
             break;
            case 3: case 11: theo = 5.5;
             break;
            case 4: case 10: theo = 8.3;
            break;
            case 5: case 9:  theo = 9.1;
             break;
            case 6: case 8:  theo = 5.67;
            break;
            case 7:          theo = 2.45;
            break;
        }
        sim = (double)(*(p + i)) / ROLLS * 100.0;
        printf("%2d\t%4d\t%10.2f\t%10.2f\n", i, *(p + i), sim, theo);
    }
     printf("Done! Rolled %d times to get above stats.\n", ROLLS);
    return 0;
}
}
