### 버블정렬
```
#include <cs50.h>
#include <stdio.h>

int main(void)
{
    int numbers[5] = {3,2,4,1,5};
    int temp;
    
    for(int i=0; i < 5; i++)
    {
        for(int j=0; j < 5-i-1; j++)
        {
            if(numbers[j] > numbers[j+1])
            {
                temp = numbers[j+1];
                numbers[j+1] = numbers[j];
                numbers[j] = temp;
            }
        }
    }
    for(int i=0; i < 5; i++)
    {
        printf("%i", numbers[i]);
    }
    printf("\n");
}
```
