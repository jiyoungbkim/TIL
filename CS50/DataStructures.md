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

\* : 메모리 덩어리로 접근할 수 있는 역참조 연산자

데이터 구조 : 컴퓨터 메모리를 더 효율적으로 관리하기 위해 새로 정의하는 구조체. 일종의 메모리 레이아웃 또는 지도라고 생각할 수 있다. 

배열 : 각 인덱스의 값이 메모리상에서 연이어 저장 

배열의 단점 : 고정된 메모리 덩어리. 배열의 크기를 조절해서 추가할 때 더 많은 메모리를 할당해야하고 기존 배열에서 새 배열로 모든 값을 복사해야 하기 때문에 배열에 값을 추가하는 과정은 O(n)이 된다.

배열의 장점 : 대괄호를 이용해서 문법적으로 쉽게 인덱싱할 수 있고 원하는 위치로 바로 접근할 수 있기 때문에 빠르고 바이너리 검색에 적용할 수 있다.

연결 리스트 : 데이터 구조중 하나. 자신의 값과 함께 바로 다음 값의 주소(포인터)를 저장 

연결 리스트의 장점 : 새로운 값을 추가할 때 다시 메모리를 할당하지 않아도 된다.

연결 리스트의 단점 : 임의 접근이 불가능하다. 연결 리스트에 값을 추가하거나 검색하는 경우 해당하는 위치까지 연결 리스트의 각 node들을 따라 이동해야 하기 때문에 연결 리스트의 크기가 n일때 그 실핼 시간은 O(n)이 된다. 배열의 경우 이진 검색을 이용하면 O(log n)의 실행 시간이 소요 되는 것에 비해 다소 불리

### 연결 리스트: 코딩
```
#include <stdio.h>
#include <stdlib.h>

//연결 리스트의 기본 단위가 되는 node 구조체를 정의합니다.
typedef struct node
{
    //node 안에서 정수형 값이 저장되는 변수를 name으로 지정합니다.
    int number; 

    //다음 node의 주소를 가리키는 포인터를  *next로 지정합니다.
    struct node *next;
}
node;

int main(void)
{
    // list라는 이름의 node 포인터를 정의합니다. 연결 리스트의 가장 첫 번째 node를 가리킬 것입니다. 
    // 이 포인터는 현재 아무 것도 가리키고 있지 않기 때문에 NULL 로 초기화합니다.
    node *list = NULL;

    // 새로운 node를 위해 메모리를 할당하고 포인터 *n으로 가리킵니다.
    node *n = malloc(sizeof(node));
    if (n == NULL)
    {
        return 1;
    }

    // n의 number 필드에 1의 값을 저장합니다. “n->number”는 “(*n).numer”와 동일한 의미입니다. 
    // 즉, n이 가리키는 node의 number 필드를 의미하는 것입니다. 
    // 간단하게 화살표 표시 ‘->’로 쓸 수 있습니다. n의 number의 값을 1로 저장합니다.
    n->number = 1;

    // n 다음에 정의된 node가 없으므로 NULL로 초기화합니다.
    n->next = NULL;

    // 이제 첫번째 node를 정의했기 떄문에 list 포인터를 n 포인터로 바꿔 줍니다.
    list = n;

    // 이제 list에 다른 node를 더 연결하기 위해 n에 새로운 메모리를 다시 할당합니다.
    n = malloc(sizeof(node));
    if (n == NULL)
    {
        return 1;
    }

    // n의 number와 next의 값을 각각 저장합니다.
    n->number = 2;
    n->next = NULL;

    // list가 가리키는 것은 첫 번째 node입니다. 
    //이 node의 다음 node를 n 포인터로 지정합니다.
    list->next = n;

    // 다시 한 번 n 포인터에 새로운 메모리를 할당하고 number과 next의 값을 저장합니다.
    n = malloc(sizeof(node));
    if (n == NULL)
    {
        return 1;
    }

    n->number = 3;
    n->next = NULL;

    // 현재 list는 첫번째 node를 가리키고, 이는 두번째 node와 연결되어 있습니다. 
    // 따라서 세 번째 node를 더 연결하기 위해 첫 번째 node (list)의 
    // 다음 node(list->next)의 다음 node(list->next->next)를 n 포인터로 지정합니다.
    list->next->next = n;

    // 이제 list에 연결된 node를 처음부터 방문하면서 각 number 값을 출력합니다. 
    // 마지막 node의 next에는 NULL이 저장되어 있을 것이기 때문에 이 것이 for 루프의 종료 조건이 됩니다.
    for (node *tmp = list; tmp != NULL; tmp = tmp->next)
    {
        printf("%i\n", tmp->number);
    }

    // 메모리를 해제해주기 위해 list에 연결된 node들을 처음부터 방문하면서 free 해줍니다.
    while (list != NULL)
    {
        node *tmp = list->next;
        free(list);
        list = tmp;
    }
}
```

### 연결 리스트: 트리

트리 : 연결리스트를 기반으로 한 새로운 데이터 구조.

트리에서의 노드들의 연결은 2차원적으로 구성되어 있다. 각 노드는 일정한 층에 속하고, 다음 층의 노드들을 가리키는 포인터를 가진다.

루트 : 가장 높은 층에서 트리가 시작되는 노드

자식 노드 : 루트 노드가 가리키는 다음 층의 노드

이진 검색 트리 : 하나의 노드는 두 개의 자식 노드를 가진다. 왼쪽 자식 노드는 자신의 값보다 작고, 오른쪽 자식 노드는 자신의 값보다 크다.

이진 검색 트리의 노드 구조체와 '50'을 재귀적으로 검색하는 이진 검색 함수
```
//이진 검색 트리의 노드 구조체
typedef struct node
{
    // 노드의 값
    int number;

    // 왼쪽 자식 노드
    struct node *left;
 
   // 오른쪽 자식 노드
    struct node *right;
} node;

// 이진 검색 함수 (*tree는 이진 검색 트리를 가리키는 포인터)
bool search(node *tree)
{
    // 트리가 비어있는 경우 ‘false’를 반환하고 함수 종료
    if (tree == NULL)
    {
        return false;
    }
    // 현재 노드의 값이 50보다 크면 왼쪽 노드 검색
    else if (50 < tree->number)
    {
        return search(tree->left);
    }
    // 현재 노드의 값이 50보다 작으면 오른쪽 노드 검색
    else if (50 > tree->number)
    {
        return search(tree->right);
    }
    // 위 모든 조건이 만족하지 않으면 노드의 값이 50이므로 ‘true’ 반환
    else {
        return true;
    }
}
```
