### 연결 리스트

struct 구조체 : C에서 두 개의 값을 가진 자신만의 구조를 만들 수 있는 키워드.

```
#include <cs50.h>
#include <stdio.h>
#include <string.h>

typedef struct
{
    string name;
    string number;
}
person;

int main(void)
{
    // string names[4] = {"EMMA", "RODRIGO", "BRIAN", "DAVID"};
    // string numbers[4] = {"617–555–0100", "617–555–0101", "617–555–0102", "617–555–0103"};
    person people[4];
    
    people[0].name = "EMMA";
    people[0].number = "617–555–0100";
    
    people[1].name = "RODRIGO";
    people[1].number = "617–555–0101";
    
    people[2].name = "BRIAN";
    people[2].number = "617–555–0102";
    
    people[3].name = "DAVID";
    people[3].number = "617–555–0103";
    
    for (int i = 0; i < 4; i++)
    {
        if(strcmp(people[i].name, "EMMA") == 0)
        {
            printf("number: %s\n", people[i].number);
            return 0;
        }
    }
    printf("Not found\n");
    return 1;
}
```

. : 속성값을 가져올 때 사용. 구조체의 속성을 가져올 때도 사용<br>
변수 이름과 점 연산자를 사용해서 자료 구조 안으로 들어가야 함

* : 메모리 덩어리로 접근할 수 있는 역참조 연산자

데이터 구조 : 컴퓨터 메모리를 더 효율적으로 관리하기 위해 새로 정의하는 구조체. 일종의 메모리 레이아웃 또는 지도라고 생각할 수 있다. 연결 
리스트도 데이터 
구조중 
구조중 하나


배열 : 각 인덱스의 값이 메모리상에서 연이어 저장 
연결 리스트 : 데이터 구조중 하나. 자신의 값과 함께 바로 다음 값의 주소(포인터)를 저장 
