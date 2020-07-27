### 1) 컴파일링

지금까지는 아무것도 모른채 마구잡이로 쓴 코드가 잘 돌아갔다면 이제부터는 연습과 응용을 통해 동작 원리를 이해할 수 있을 것입니다.

우선 첫 수업에 봤던 예제를 다시 살펴보며 지금 사용하는 방법이 그때 우리가 사용한 방법과 어떻게 다른지 알아봅시다.

첫 수업에 봤던 C코드를 다시 봐보겠습니다.

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/09775b29-20bd-4b12-a116-c0dcf7eac910/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/09775b29-20bd-4b12-a116-c0dcf7eac910/Untitled.png)

우선 main이라는 함수가 있습니다. 프로그램의 시작점으로써 **실행 버튼을 클릭**하는 것과 같습니다.

printf는 출력을 담당하는 함수입니다.

printf 함수를 사용하기 위해서는 stdio.h 라이브러리가 필요합니다.

정확히 말하면 stdio.h는 헤더 파일로 C언어로 작성되어 있으며 파일명이 .h로 끝나는 파일입니다.

이 파일에는 printf 함수의 프로토타입이 있어서 Clang 컴파일러가 프로그램을 컴파일할때 printf가 무엇인지 알려주는 역할을 합니다.

코드를 clang hello.c로 컴파일하고 ./a.out 명령으로 프로그램을 실행할 때 이 과정은 컴퓨터가 이해하는 0과 1로 가득찬 파일 a.out을 생성하여 실행 가능하게 합니다.

이해하기 어려운 이 과정에 대한 이해는 잠시 미뤄두고 우선 넘어가보도록 하겠습니다.

만약 a.out과 다른 이름(hello)으로 컴파일을 하고 싶다면 아래와 같이 명령행 인자를 추가해야줘야 합니다.

```
clang -o hello hello.c
```

우리는 또한 CS50 라이브러리를 사용해 보았습니다.

이 처럼 CS50 라이브러리를 사용한 프로그램을 컴파일 할때는 clang에 또 하나의 프로그램(-lcs50)이 필요했습니다.

그래야 clang이 실행되었습니다.

```
clang -o hello hello.c -lcs50
```

이는 clang에게 CS50 라이브러리에 있는 모든 0과 1들을 여기에 연결하라는 의미입니다.

더 간단히는, 이 전에 배웠듯이 make 프로그램을 이용하면 이 모든 컴파일 과정을 자동으로 처리할 수 있습니다.

make나 clang을 사용해서 프로그램을 실행할 때 아래 네 개의 단계를 거칩니다.

- 전처리
- 컴파일링
- 어셈블링
- 링킹

우리가 명령어를 실행할 때 정확히 어떤 일이 일어나는지 알아보도록 하겠습니다.

**전처리(Precompile)**

**컴파일의 전체 과정은 네 단계로 나누어볼 수 있습니다**. 그 중 첫 번째 단계는 **전처리**인데, 전처리기에 의해 수행됩니다. # 으로 시작되는 C 소스 코드는 전처리기에게 **실질적인 컴파일이 이루어지기 전에 무언가를 실행**하라고 알려줍니다.

예를 들어, #include는 전처리기에게 다른 파일의 내용을 포함시키라고 알려줍니다. 프로그램의 소스 코드에 #include 와 같은 줄을 포함하면, 전처리기는 새로운 파일을 생성하는데 이 파일은 여전히 C 소스 코드 형태이며 stdio.h 파일의 내용이 #include 부분에 포함됩니다.

**컴파일(Compile)**

전처리기가 전처리한 소스 코드를 생성하고 나면 그 다음 단계는 **컴파일**입니다. **컴파일러**라고 불리는 프로그램은 **C 코드를 어셈블리어라는 저수준 프로그래밍 언어로 컴파일**합니다.

**어셈블리**는 C보다 연산의 종류가 훨씬 적지만, 여러 연산들이 함께 사용되면 C에서 할 수 있는 모든 것들을 수행할 수 있습니다. C 코드를 어셈블리 코드로 변환시켜줌으로써 컴파일러는 컴퓨터가 이해할 수 있는 언어와 최대한 가까운 프로그램으로 만들어 줍니다. 컴파일이라는 용어는 소스 코드에서 오브젝트 코드로 변환하는 전체 과정을 통틀어 일컫기도 하지만, 구체적으로 전처리한 소스 코드를 어셈블리 코드로 변환시키는 단계를 말하기도 합니다.

**어셈블(Assemble)**

소스 코드가 어셈블리 코드로 변환되면, 다음 단계인 **어셈블** 단계로 **어셈블리 코드를 오브젝트 코드로 변환**시키는 것입니다. 컴퓨터의 중앙처리장치가 프로그램을 어떻게 수행해야 하는지 알 수 있는 명령어 형태인 **연속된 0과 1들로 바꿔주는 작업**이죠. 이 변환작업은 **어셈블러**라는 프로그램이 수행합니다. 소스 코드에서 오브젝트 코드로 컴파일 되어야 할 파일이 딱 한 개라면, 컴파일 작업은 여기서 끝이 납니다. 그러나 그렇지 않은 경우에는 링크라 불리는 단계가 추가됩니다.

**링크(Link)**

만약 프로그램이 (math.h나 cs50.h와 같은 라이브러리를 포함해) **여러 개의 파일로 이루어져 있어 하나의 오브젝트 파일로 합쳐져야 한다면** **링크**라는 컴파일의 마지막 단계가 필요합니다. 링커는 여러 개의 다른 오브젝트 코드 파일을 실행 가능한 하나의 오브젝트 코드 파일로 합쳐줍니다. 예를 들어, 컴파일을 하는 동안에 CS50 라이브러리를 링크하면 오브젝트 코드는 GetInt()나 GetString() 같은 함수를 어떻게 실행할 지 알 수 있게 됩니다.

이 네 단계를 거치면 최종적으로 실행 가능한 파일이 완성됩니다.

### 2) 디버깅

**버그와 디버깅**

**버그(bug)**는 **코드에 들어있는 오류**입니다. 버그로 인해 프로그램의 실행에 실패하거나 프로그래머가 원하는 대로 동작하지 않게 됩니다. 버그를 만들고 싶지 않겠지만 모든 프로그래머들은 버그와 마주하게 되어있습니다. **디버깅(debugging)**은 **코드에 있는 버그를 식별하고 고치는 과정**입니다. 프로그래머는 **디버거**라고 불리는 프로그램을 사용하여 디버깅을 하게 됩니다.

**디버깅의 기본**

프로그램은 일반적으로 인간보다 훨씬 빠르게 연산을 수행합니다. 그래서 프로그램을 실행시켜보는 것만으로는 무엇이 잘못됐는지 찾아내기 어렵습니다. 디버거는 프로그램을 특정 행에서 멈출 수 있게 해주기 때문에 버그를 찾는데 도움이 됩니다. 프로그래머는 멈춰진 그 지점에서 무슨 일이 일어나는지 볼 수 있습니다. **프로그램이 멈추는 특정 지점**을 **중지점**이라고 합니다. 또한 프로그래머가 프로그램을 한번에 한 행씩 실행할 수 있게 해줍니다. 이로써 프로그래머는 프로그램이 내리는 모든 결정들을 단계별로 따라갈 수 있게 됩니다.

**help50**

아래 코드를 컴파일하고 실행한다고 생각해봅시다.

```c
int main(void)
{
    printf("hello, world\n");
}
```

make 프로그램을 이용하여 컴파일해보면 “implicitly declaring library function 'printf'” 이라는 에러 메시지가 나타납니다.

이런 에러 메시지를 이해하기 힘들다면, **help50 프로그램**을 사용해보세요.

아래와 같이 make 앞에 help50 을 붙여서 실행하면 다시 컴파일시 생기는 오류를 해석해줍니다.

```
help50 make 파일이름
```

문제의 원인은 printf 함수를 사용하기 위해서 stdio.h 라이브러리를 포함해야 한다는 것이었죠.

**printf**

하지만 이렇게 프로그램을 사용해서 해결할 수 없는 문제도 있습니다.

아래 코드는 #을 10개 출력하기 위해 작성한 것입니다.

```c
#include <stdio.h>int main(void)
{
    for (int i = 0; i <= 10; i++)
    {
        printf("#\n");
    }
}

```

이 코드를 컴파일 하고 실행해보면 에러는 발생하지 않지만, 우리 의도와는 다르게 #이 11개나 출력되는 것을 확인할 수 있습니다. 그 이유는 뭘까요?

디버깅의 다른 방법으로 직접 의심이 가는 변수를 출력해서 확인해 볼 수 있습니다.

아래와 같이 변수 i를 출력해보겠습니다.

```c
#include <stdio.h>int main(void)
{
    for (int i = 0; i <= 10; i++)
    {
        printf("i is now %i: ", i);
        printf("#\n");
    }
}
```

그 결과 i가 0에서 시작하기 때문에 for 루프의 i <= 10 이라는 조건은 실제로 11번 만족한다는 사실을 알 수 있습니다.

따라서 이를 i < 10 으로 수정해주면 우리 의도대로 #이 10번 출력되겠죠

**debug50**

CS50 IDE를 사용하면 **debug50**이라는 프로그램도 사용할 수 있습니다.

아래와 같이 소스 코드에 직접 브레이크포인트를 지정하고 소스파일을 컴파일한 후에 **“debug50 파일명”** 으로 실행하면, 오른쪽 패널을 통해 변수의 값을 확인하거나 브레이크포인트부터 한 줄씩 코드를 실행해 볼 수 있습니다.

디버깅 종료를 위해서는 **Ctrl + c**를 누르면 됩니다.

![https://cs50.harvard.edu/x/2020/notes/2/debugger_panel.png](https://cs50.harvard.edu/x/2020/notes/2/debugger_panel.png)

[Build software better, together](https://ide.cs50.io/jiyoungbkim/ide)

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/b84ee41e-c15d-4892-b6a9-c9a346ef0352/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/b84ee41e-c15d-4892-b6a9-c9a346ef0352/Untitled.png)

한줄 씩 실행하면서 디버깅

### 3) 코드의 디자인

**check50**

check50 프로그램을 이용하면 과제를 잘 수행했는데 자동으로 검사할 수 있습니다.

물론 이 프로그램은 cs50 강의를 위해서만 작성되었지만, 실제로 많은 사람들이 함께 작업하는 환경에서 이와 같은 자동 검사 프로그램은 많은 도움이 됩니다.

여러 사람들이 각자 한 부분을 맡아 코드를 작성할 때 각자가 수정한 코드가 전체 프로그램의 정확성을 해치지 않는지 쉽게 확인할 수 있기 때문입니다.

사용할 수 X

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/cd695088-868c-4628-906b-be5916d5841d/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/cd695088-868c-4628-906b-be5916d5841d/Untitled.png)

**style50**

style50 프로그램을 이용하면 코드가 심미적으로 잘 작성되어 있는지 검사할 수 있습니다.

공백의 수나 줄바꿈과 같은 것들은 코드의 실행에 직접적으로 영향을 주지는 않지만 코드를 작성하는 사람들이 코드를 읽고 이해하는데 영향을 주기 때문입니다.

가령 아래와 같이 for 루프를 작성할 때도 사람에 따라 여러 방식으로 작성할 수 있습니다.

```c
for (int i = 0; i <= 10; i++)
    {
        printf("#\n");
    }
```

```c
for (int i = 0; i <= 10; i++){
    printf("#\n");
}
```

```c
for (int i = 0; i <= 10; i++){ printf("#\n"); }
```

많은 회사들은 사내에서 코드를 작성할 때 특정한 스타일 가이드를 따르도록 합니다.

여러 사람들이 코드를 작성하기 때문에 서로 불필요한 오해를 없애고, 코드를 이해하는 데 드는 비용을 최소화하기 때문입니다.

**고무 오리**

때로는 코드에 포함된 오류를 해결할 때 앞서 소개한 help50, debug50, check50과 같은 프로그램들이 존재하지 않거나, 있다 하더라도 디버깅에 큰 도움이 안 될 수 도 있습니다.

이 때는 먼저 한숨 돌리고 직접 곰곰히 생각해보는 수 밖에 없습니다.

한가지 유명한 방법으로 **‘고무 오리’**와 같이 무언가 대상이 되는 물체를 앞에 두고, 내가 작성한 코드를 한 줄 한 줄 말로 설명해주는 과정을 거쳐볼 수 있습니다.

이를 통해 미처 놓치고 있었던 논리적 오류를 찾아낼 수도 있습니다.

### 4) 배열(1)

**메모리**

C에는 아래와 같은 여러 자료형이 있고, 각각의 자료형은 서로 다른 크기의 메모리를 차지합니다.

- bool: 불리언, 1바이트
- char: 문자, 1바이트
- int: 정수, 4바이트
- float: 실수, 4바이트
- long: (더 큰) 정수, 8바이트
- double: (더 큰) 실수, 8바이트
- string: 문자열, ?바이트

컴퓨터 안에는 아래 사진과 같은 **RAM** 이라고 하는 물리적 칩이 메모리 역할을 합니다.

쉽게 생각하면 아래 사진에서 여러 개의 노란색 사각형이 메모리를 의미하고, 작은 사각형 하나가 **1바이트**를 의미한다고 볼 수 있습니다.

![https://cs50.harvard.edu/x/2020/notes/2/ram.png](https://cs50.harvard.edu/x/2020/notes/2/ram.png)

예를 들어 char 타입의 변수를 하나 생성하고, 그 값을 입력한다고 하면 위 사진에서 한 사각형 안에 그 변수의 값이 저장되는 것이죠.

```c
#include <stdio.h>

int main(void)
{
    char c1 = 'H';
    char c2 = 'I';
    char c3 = '!';
    printf("%c %c %c\n", c1, c2, c3);
}
```

H I ! 로 띄어쓰기가 있게 출력된다.

문자는 숫자를 변환한 것이기 때문에 정수를 확인한다. 형변환은 자동적으로 된다.

```c
printf("%i %i %i\n", (int) c1, (int) c2, (int) c3);
```

**배열**

아래와 같이 세 개의 점수를 저장하고 그 평균을 출력하는 프로그램이 있습니다.

```c
#include <cs50.h>
#include <stdio.h>
int main(void)
{
    // Scores
    int score1 = 72;
    int score2 = 73;
    int score3 = 33;

    // Print average
    printf("Average: %i\n", (score1 + score2 + score3) / 3);
}
```

만약 점수의 개수가 더 많아진다면 이 프로그램은 많은 부분을 수정해줘야 합니다.

이 때 활용할 수 있는 것이 배열의 개념입니다.

배열은 같은 자료형의 데이터를 메모리상에 연이어서 저장하고 이를 하나의 변수로 관리하기 위해 사용됩니다.

위 코드는 배열을 이용하면 아래와 같이 바꿀 수 있습니다.

```c
#include <cs50.h>
#include <stdio.h>
int main(void)
{
    // Scores
    int scores[3];
    scores[0] = 72;
    scores[1] = 73;
    scores[2] = 33;

    // Print average
    printf("Average: %i\n", (scores[0] + scores[1] + scores[2]) / 3);
}
```

**int scores[3];** 이라는 코드는 int 자료형을 가지는 크기 3의 배열을 scores 라는 이름으로 생성하겠다는 의미입니다.

배열의 인덱스는 0부터 시작하기 때문에, scores의 인덱스는 0, 1, 2 세 개가 있습니다.

이 인덱스를 변수명 뒤 대괄호 사이에 입력하여 배열의 원하는 위치에 원하는 값을 저장하고 불러올 수 있습니다.

하지만 위와 같은 코드는 여전히 점수의 개수가 바뀌는 상황에서 제약이 많습니다.

다음 강의에서는 배열을 보다 동적으로 선언하고 저장하는 방법을 알아보겠습니다.

### 5) 배열(2)

**전역 변수**

이전 강의에 이어서, 아래 코드에서 scores 배열의 크기를 정해주는 N이라는 변수를 새로 선언하였습니다.

만약 N이 고정된 값(상수)이라면 그 값을 선언할 때 const를 앞에 붙여서 전역 변수, 즉 코드 전반에 거쳐 바뀌지 않는 값임을 지정해줄 수 있습니다.

관례적으로 이런 전역 변수의 이름은 대문자로 표기 합니다.

```c
#include <cs50.h>
#include <stdio.h>

const int N = 3;

int main(void)
{
    // 점수 배열 선언 및 값 저장
    int scores[N];
    scores[0] = 72;
    scores[1] = 73;
    scores[2] = 33;

    // 평균 점수 출력
    printf("Average: %i\n", (scores[0] + scores[1] + scores[2]) / N);
}
```

scores의 크기로 전역 변수를 선언하였기 때문에 점수 개수가 바뀌었을때 수정해야 하는 코드가 조금 줄었습니다.

하지만 여전히 일일이 배열의 인덱스마다 점수를 지정해줘야 하는 불편함이 있습니다.

**배열의 동적 선언 및 저장**

아래 코드에서와 같이 루프와 함수를 선언하여 좀 더 동적인 프로그램을 작성할 수 있습니다.

```c
#include <cs50.h>
#include <stdio.h>

float average(int length, int array[]);

int main(void)
{
    // 사용자로부터 점수의 갯수 입력
    int n = get_int("Scores:  ");

    // 점수 배열 선언 및 사용자로부터 값 입력
    int scores[n];
    for (int i = 0; i < n; i++)
    {
        scores[i] = get_int("Score %i: ", i + 1);
    }

    // 평균 출력
    printf("Average: %.1f\n", average(n, scores));
}

//평균을 계산하는 함수
float average(int length, int array[])
{
    int sum = 0;
    for (int i = 0; i < length; i++)
    {
        sum += array[i];
    }
    return (float) sum / (float) length;
}
```

여기서는 배열의 크기를 사용자에게 직접 입력 받고, 배열의 크기만큼 루프를 돌면서 각 인덱스에 해당하는 값을 역시 사용자에게 동적으로 입력 받아 저장합니다.

그리고 average 라는 함수를 따로 선언하여 평균을 구합니다.

average 함수는 length 와 array[], 즉 배열의 길이와 배열을 입력으로 받습니다. 함수 안에서는 배열의 길이만큼 루프를 돌면서 값의 합을 구하고 최종적으로 평균값을 반환합니다.

이와 같은 방법을 통해서 임의의 점수 개수와 점수 배열에 대해서 동적으로 평균값을 구하는 프로그램을 작성할 수 있습니다.

### 6) 문자열과 배열

우리가 여지껏 사용한 문자열(string) 자료형의 데이터는 사실 문자(char) 자료형의 데이터들의 배열이었습니다.

**string s = “HI!”;** 과 같이 문자열 s가 정의되어 있다고 생각해봅시다.

s는 문자의 배열이기 때문에 메모리상에 아래 그림과 같이 저장되고, 인덱스로 각 문자에 접근할 수 있습니다.

![https://cs50.harvard.edu/x/2020/notes/2/memory_with_string.png](https://cs50.harvard.edu/x/2020/notes/2/memory_with_string.png)

여기서 가장 끝의 **‘\0’**은 문자열의 끝을 나타내는 널 종단 문자입니다.

단순히 모든 비트가 0인 1바이트를 의미합니다.

그럼 아래 코드와 같이 여러 문자열이 동시에 선언된 경우를 살펴보겠습니다.

```
string names[4];

names[0] = "EMMA";
names[1] = "RODRIGO";
names[2] = "BRIAN";
names[3] = "DAVID";

printf("%s\n", names[0]);
printf("%c%c%c%c\n", names[0][0], names[0][1], names[0][2], names[0][3]);

```

names라는 문자열 형식의 배열에 네 개의 이름이 저장되어있습니다.

첫 번째 printf에서는 names의 첫번째 인덱스의 값, 즉 “EMMA”를 출력합니다.

두 번째 printf에서는 형식 지정자가 %s가 아닌 %c로 설정되어 있음을 확인할 수 있습니다.

따라서 출력하는 것은 문자열이 아닌 문자입니다.

여기서는 각 이름의 두번째 문자를 출력하고자 합니다.

이는 names[0][1]과 같이 2차원 배열을 통해 접근할 수 있습니다.

다시 말해 names[0][1]는 names의 첫 번째 값, 즉 “EMMA”라는 문자열에서, 그 두번째 값, 즉 ‘M’ 이라는 문자를 의미합니다.

아래 그림에서 names가 실제 메모리상에 저장된 예시와 해당하는 인덱스를 확인할 수 있습니다.

![https://cs50.harvard.edu/x/2020/notes/2/memory_with_string_array.png](https://cs50.harvard.edu/x/2020/notes/2/memory_with_string_array.png)

### 7) 문자열의 활용

**문자열의 길이 및 탐색**

사용자로 부터 문자열을 입력받아 한 글자씩 출력하는 프로그램을 만들어 보겠습니다.

간단하게 for 루프를 통해 문자열의 인덱스를 하나씩 증가시켜가면서 해당하는 문자를 출력하면 될텐데요, 문자열의 끝은 어떻게 알 수 있을까요?

한가지 방법은 해당하는 인덱스의 문자가 널 종단 문자, 즉 ‘\0’와 일치하는지 검사하는 것입니다.

즉, s라는 문자열이 있다고 할 때 for (int i = 0; i < s[i] != ‘\0’; i++) { ..} 과 같은 루프를 사용하면 되겠죠.

하지만 아래 코드와 같이 strlen() 이라는 함수를 사용할 수도 있습니다.

```c
#include <cs50.h>
#include <stdio.h>
#include <string.h>

int main(void)
{
    string s = get_string("Input: ");
    printf("Output:\n");
    for (int i = 0, n = strlen(s); i < n; i++)
    {
        printf("%c\n", s[i]);
    }
}
```

**strlen**은 문자열의 길이를 알려주는 함수로, string.h 라이브러리 안에 포함되어 있습니다.

위 코드에서는 n이라는 변수에 문자열 s의 길이를 저장하고, 해당 길이 만큼만 for 루프를 순환합니다.

따라서 일일이 널 종단 문자를 검사하는 것 보다 훨씬 효율적입니다.

**문자열 탐색 및 수정**

사용자로부터 문자열을 입력받아 대문자로 바꿔주는 프로그램을 아래와 같이 작성할 수 있습니다.

```c
#include <cs50.h>
#include <stdio.h>
#include <string.h>

int main(void)
{
    string s = get_string("Before: ");
    printf("After:  ");
    for (int i = 0, n = strlen(s); i < n; i++)
    {
        if (s[i] >= 'a' && s[i] <= 'z')
        {
            printf("%c", s[i] - 32);
        }
        else
        {
            printf("%c", s[i]);
        }
    }
    printf("\n");
}
```

먼저 사용자로부터 입력받은 문자를 s라는 변수에 저장합니다.

그리고 s의 길이만큼 for 루프를 돌면서, 각 인덱스에 해당하는 문자가 ‘a’보다 크고 ‘z’보다 작은지 검사합니다.

즉, 소문자인지 검사하는 것과 동일합니다.

여기서 문자의 대소비교가 가능한 이유는 ASCII값, 즉 그 문자가 정의되는 ASCII 코드 상에서의 숫자값으로 비교할 수 있기 때문입니다.

또한 알파벳의 ASCII 값을 잘 살펴보면 각 알파벳의 소문자와 대문자는 32씩 차이가 남을 확인할 수 있습니다.

따라서 각 문자가 소문자인 경우 그 값에서 32를 뺀 후에 ‘문자’ 형태로 출력하면 대문자가 출력이 됩니다.

각 문자가 이미 대문자인 경우는 그냥 그대로 출력하면 됩니다.

이와 동일한 작업을 수행하는 함수가 ctype 라이브러리에 **toupper()** 이라는 함수로 정의되어 있습니다.

이를 이용하면 간단하게 아래와 같이 대문자 변환 프로그램을 작성할 수 있습니다.

```c
#include <cs50.h>
#include <ctype.h>
#include <stdio.h>
#include <string.h>

int main(void)
{
    string s = get_string("Before: ");
    printf("After:  ");
    for (int i = 0, n = strlen(s); i < n; i++)
    {
        printf("%c", toupper(s[i]));
    }
    printf("\n");
}
```

### 8) 명령행 인자

우리가 여태껏 많이 사용해온 main 함수를 보다 자세히 들여다볼 때가 왔습니다.

main도 그 형태를 보면 하나의 함수임을 알 수 있는데요, 이젠 더이상 main() 안에 기계적으로 void 라고 입력하는 대신 아래 코드와 같이 argc, argv 를 정의해보겠습니다.

```c
#include <cs50.h>
#include <stdio.h>

int main(int argc, string argv[])
{
    if (argc == 2)
    {
        printf("hello, %s\n", argv[1]);
    }
    else
    {
        printf("hello, world\n");
    }
}
```

여기서 첫번째 변수 **argc**는 main 함수가 받게 될 **입력의 개수**입니다.

그리고 **argv[]**는 그 **입력이 포함되어 있는 배열**입니다. 프로그램을 명령행에서 실행하므로, 입력은 문자열로 주어집니다.

따라서 argv[]는 string 배열이 됩니다.

**argv[0]**는 기본적으로 **프로그램의 이름**으로 저장됩니다.

만약 하나의 입력이 더 주어진다면 argv[1]에 저장될 것입니다.

예를 들어 위 프로그램을 “arg.c”라는 이름으로 저장하고 컴파일 한 후 **“./argc”**로 실행해보면 “hello, world”라는 값이 출력됩니다.

명령행 인자에 주어진 값이 프로그램 이름 하나밖에 없기 때문입니다.

하지만 **“./argc David”**로 실행해보면 “hello, David”라는 값이 출력됩니다.

명령행 인자에 David라는 값이 추가로 입력되었고, 따라서 argc 는 2, argv[1] 은 “David”가 되기 때문입니다.