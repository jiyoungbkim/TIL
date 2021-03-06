### 1) C 기초

**C언어**

```c
#include <stdio.h>int main(void)
{
    printf("hello, world\n");
}

```

C는 아주 오래되고 전통적인 순수 텍스트 기반의 언어입니다.

하나하나 설명하자면 int main(void)는 스크래치의 “초록색 깃발을 클릭했을 때” 블록과 같은 역할을 합니다.

즉 '**시작한다**'의 의미를 가지고 있다고 보면 됩니다.

앞으로 우리가 작성할 코드 모두는 이 int main(void) { }의 중괄호 사이에 작성하게 될 것 입니다.


C에서는 스크래치에서의 say라는 함수는 없습니다. 대신에 **printf**라는 함수가 있습니다.

**printf(“hello, world\n”)** 은 스크래치의 “‘hello, world’라고 말하기” 블록과 같은 역할을 합니다.

글자나 단어, 문장을 적을 때는 **언제나 텍스트에 " " 쌍따옴표로 감싸야 합니다**.

그리고 우리가 일상에서 문장의 끝에 마침표(.)를 붙이는 것 처럼 C에서는 **세미콜론(;)**을 붙여야 합니다.

(아래 사진파일에는 나와있지 않지만 **\n**은 줄바꿈의 기능을 합니다. 키보드에서 ENTER의 기능과 동일합니다.)



#include <stdio.h>는 “stdio.h”라는 이름의 파일을 찾아서 “printf” 함수에 접근할 수 있도록 해줍니다.

제일 중요한 것은 중간에 있는 printf("hello, world")입니다.

우리가 Word로 문서를 저장했을때 "문서.docx"와 같이 .docx가 붙는 것 처럼, C로 작성한 코드는 “파일이름.c”로 저장해야 합니다. (확장자 “.c”는 C로 작성된 코드라는 의미입니다.)

마이크로소프트의 Word 처럼 자동적으로 붙여주지 않기 때문에 C의 경우에는 직접 .c를 붙여줘야 합니다.

**컴파일러**

우리가 직접 작성한 코드는 **“소스 코드”** 라고 불립니다. 이를 2진수로 작성된 “머신 코드”로 변환해야 컴퓨터가 이해할 수 있습니다. 이런 작업을 컴파일러라는 프로그램이 수행해줍니다.

터미널창의 명령어 프롬프트에서 “$” 기호 옆에우리가 원하는 명령어를 입력하면 됩니다.

clang hello.c 라는 명령어는 “clang” 이라는 컴파일러로 “hello.c”라는 코드를 컴파일하라는 의미입니다.

그 결과 **a.out** 이라는 파일이 생성됩니다.

**./a out** 이라는 명령어를 실행하면 컴퓨터가 현재 디렉토리에 있는 a.out이라는 프로그램을 실행하게 해줍니다.(**.**/a out에서 제일 앞에 있는 .은 지금 있는 현재 폴더를 나타냅니다.)

```c
$ clang hello.c // 컴파일
$ ./a.out // 실행
hello, world
$ clang -o hello hello.c // hello라는 이름으로 컴파일
$ ./hello // 실행
hello, world
$ ls // 파일 목록 보기 
a.out* hello* hello.c // *붙은 것은 머신코드 없는 것은 소스코드
$ rm a.out // a.out 지우기
rm: remove regular file 'a.out'? y
$ ls // 지워졌는지 확인
hello* hello.c
```

### 2) 문자열

저번 강의에서는 간단하게 Hello World를 출력해보았습니다. 이번 시간에는 좀 더 다이나믹한 것을 해보도록 하죠. 스크래치 강의에서 사용자의 이름을 입력으로 받고 그리고 그 사람의 이름을 불러서 인사를 했습니다.

그럼 이것을 C로 해보면 어떻게 될까요?

CS50 Sandbox에서는 스크래치의 ask함수와 가장 비슷한 것은 **get_string 함수**입니다.

String은 단어나 구절, 문장을 부르는 말입니다. (숫자와는 다른 종류의 데이터 입니다.)

사용자의 이름을 받아서 저장할**변수**를 스크래치와 같이 **answer**이라고 정해보겠습니다. 이때 변수는 xyz, name 등과 같이 **여러분 마음대로 정하셔도 무관합니다**.

하지만 여기서 유의해할 점은 C는 오래된 언어이기 때문에 변수가 저장하는 **데이터의 종류를 아주 정확하게 명시해줘야 합니다**.

그래서 우리는 저장하고자 하는 값의 종류가 문자열(string)이라는 것을 알려줘야 합니다. 이때 string을 **형식지정자**라고 합니다.

왜냐하면 너무나 당연하게 이름은 숫자가 아닌 문자이기 때문에 컴퓨터에게 "answer에 들어갈 것들은 문자야!"라고 말해주는 것이죠


우리가 일반적으로 사용하는 =은 같다 입니다. 하지만 프로그래밍 언어에서는 오른쪽에서 왼쪽으로 가는 화살표와 비슷하다고 생각해주시면 좋습니다. 쉽게 말하자면 오른쪽에 있는 것을 왼쪽에 **지정**한다는 것이죠. 이를 할당 연산자라고 합니다.

**get_string 함수가 사용자의 이름을 반환하면 그 이름을 anwser이라는 변수에 저장**하는 것입니다.


그럼 이 것을 printf 함수로 출력을 해보도록 하겠습니다.

이때 유의할 점은 printf("hello, answer");이 아니라는 점입니다.

이 코드를 실행한다면 answer이 출력이 되어 hello, answer이 그대로 결과로 나옵니다.

우리는 answer이라는 변수에 들어있는 이름을 출력을 해야하기 때문에 %를 사용해 줍니다.

이 때도 어떤 종류의 인자를 받는지 말해줘야 합니다.

우리는 이름이라는 문자열을 받기때문에 **string**에서의 **s**를 %뒤에 붙여서 인자를 받아줍니다.

그래서 최종적으로는 printf("hello, %s\n", answer);이 되는 것입니다.

가장 위에 포함된 cs50.h 파일 안에 string이라는 문자열 형식과 get_string 이라는 함수에 대한 코드가 포함되어 있습니다. 이 파일을 포함해야만 전체 코드를 컴파일 하고 실행할 수 있습니다.

터미널창에 아래 명령어를 입력하여 컴파일을 할 수 있습니다.

```
$ clang -o string string.c -lcs50
```

여기서 -o string 은 string.c 를 string.out 이라는 머신코드로 저장하도록 하는 명령어입니다.

-lcs50은 “link”라는 의미를 지닌 -l 이라는 인자에 우리가 추가로 포함한 “cs50” 파일을 합친 것입니다. 이를 통해 컴파일시 cs50 파일을 연결하도록 알려줄 수 있습니다.

다소 복잡한 이런 과정 대신에, 아래 make 명령어를 통해 간단하게 컴파일을 수행할 수도 있습니다.

```
$make string //make 프로그램명
```

이와 같이 작성한 코드를 컴파일 하고 실행하면, 사용자에게 입력값을 받고 문장 내에 포함하여 출력하는 프로그램이 됩니다.

### 3) 조건문과 루프

스크래치에서 counter 라는 변수를 생성하고 0을 저장하기 위해서는 아래와 같은 블록을 사용하였었습니다.


저번 강의에서 말씀드렸던 C는 오래된 언어라 저장하고자 하는 변수의 종류를 꼭 알려줘야 한다는 것을 기억하시나요?

우리는 counter라는 변수에 **숫자**를 저장하고 싶습니다.

여기서 int 는 변수가 정수(integer)라는 것을 알려주는 것이고, counter는 변수의 이름, 0은 그 값에 0을 저장(초기화)하는 것입니다. 

스크래치에서 변수의 값을 1씩 증가시키는 것을 해보았습니다. 그럼 C에서는 어떻게 하면 될까요?

즉, counter에 1을 더한 값을 다시 counter에 저장(할당)한다는 의미가 됩니다.

"**=은 오른쪽에서 왼쪽이다**"를 기억해 주세요.

이를 더 간단하게 아래 두 가지 방식으로 수행할 수도 있습니다.



마찬가지로 스크래치의 **조건문** 블록을 C코드로 나타내볼 수 있습니다.



if ( ) 의 괄호 안에는 검사하고자 하는 **조건**이 들어가고, { } 안에는 조건을 만족할 때 수행하고자 하는 작업이 들어갑니다.

여기에서는 조건이 True면 "x is less than y"를 출력을 하라는 것입니다.

else를 이용해 처음 조건이 아닌 경우에는 어떤 것을 하라라고 적어줄 수 있습니다.



이 경우에는 첫 번째 x < y 조건이 False, 즉 x가 y보다 작지 않을 경우에는 "x is not less than y"를 출력하라는 것입니다.

**else if**를 통해서 아래와 같이 조건을 추가할 수도 있습니다.



여기서 한 가지 이상한 점이 있습니다. 바로 == 입니다. 이전 강의에서 =는 **할당 연산자**라고 말씀드렸습니다. 이미 등호 표시 하나를 할당 연산자로 정해버린 것이죠.

그럼 이제 같다는 것을 어떻게 표현하지에 대한 난관에 봉착한 것입니다. 오래전 사람들이 합의하길 **=을 2개 사용하여 같다를 표현**하자라고 정한 것입니다. 이를 일치 연산자라고 합니다.

여기서 한 가지 또 알아가야 할 것이 있습니다.

if(x < y), else if (x > y), else if (x == y) 이렇게 3개의 조건문을 사용했습니다.

하지만 여기서 한 가지 굳이 물어볼 필요가 없는 것이 있습니다. 바로 else if (x == y) 입니다.

만약 x가 y보다 작지도 크지도 않다면 우리에게 남은 유일한 가능성은 x와 y가 같다는 것 입니다.

따라서 위의 코드를 수정하면 아래와 같습니다.



이렇게 좀 더 간결하게 만들 수 있습니다.

이렇듯 얼마나 효율적으로 코딩을 하는지, 혹은 얼마나 적은 메모리나 CPU를 사용해서 수행하는지는 정말 중요합니다.

추가로 if, else, else if 뒤에는 세미콜론(;)이 붙지 않은 것을 볼 수 있습니다. 보통 조건과 같은 것들의 끝에는 세미콜론을 붙이지 않습니다.

**루프**

마지막으로 스크래치에서의 루프는 “forever” 또는 “repeat 50”과 같은 블록을 통해서 수행했었습니다. 무언가를 계속 반복하는 것이였죠. C에서도 while 이나 for 을 통해서 루프를 구현할 수 있습니다.


먼저 while 의 경우 아래 코드와 같이 while ( )의 괄호 안에 조건을 넣고 { } 안에 수행할 작업을 포함시키면 됩니다.

즉, C에서 루프를 구현하고 싶다면 성립 조건을 정해줘야 합니다. 답이 네, 참, 혹은 1로 나올 수 있는 질문을 던져줘야 하는 것이죠. 

답이 참으로 나오게 하는 방법은 여러가지가 있을 수 있습니다. 5=5, 1<2 등등 하지만 가장 간단한 방법은 그냥 **true**를 적는 것입니다.

아래 코드에서는 true라는 항상 참이 되는 조건을 통해 while 루프가 영원히 수행되도록 합니다. 따라서 위의 코드는 계속해서 "hello, world"를 무한정 출력하게 될 것입니다.

만약 특정 횟수만큼 작업을 수행하고 싶으면 어떻게 할까요?


자 이제는 좀 더 프로그래머스럽게 작성을 해보겠습니다. counter라는 변수는 너무 긴 단어입니다. 그래서 프로그래머들은 무언가를 셀 때 간단하게 정수를 나타내는 **i**를 사용합니다.

다시 while문으로 돌아가서 이번에는 **i<50**이라는 조건을 추가해줍니다.

우리는 처음에 i를 0이라고 정해주었고 while는 계속해서 i가 50보다 작은지를 물어볼 것입니다.

따라서 이 코드가 정상적으로 작동하려면 i를 증가시켜야 합니다. (i = i + 1, i += 1, i++ 모두 같은 결과를 냅니다.)

진행 순서를 정리해보자면 아래와 같습니다.

i는 0으로 설정 -> i는 50보다 작은가? -> 작다 -> hello world를 출력한다 -> i를 1증가시킨다 -> i가 50보다 작은가?-> (반복) -> i가 50보다 작은가? -> 작지 않다 -> 종료

따로 변수를 선언해도 되지만 아래와 같이 **for** 를 사용하면 for ( ) 안에 각각 (변수 초기화; 변수 조건; 변수 증가) 에 해당하는 코드를 넣어서 간단하게 표현할 수 있습니다.

즉, 가장 먼저 정수 값을 가지는 i라는 변수를 0으로 초기화하고, i가 50인지 매번 검사를 하고, 이를 만족하면 { } 안의 내용을 수행한 후에, i를 1씩 증가시킨다는 의미입니다.


while문과 비교하여 코드가 엄청 간단해진 것을 확인할 수 있습니다.
