### 3. 선택자

**3-1. 요소 선택자**

선택자 중에 가장 기본이 되는 선택자이며, 태그 선택자라고도 합니다.

```html
h1 { color: yellow; }
h2 { color: yellow; }
h3 { color: yellow; }
h4 { color: yellow; }
h5 { color: yellow; }
h6 { color: yellow; }

```

요소 선택자는 위 코드처럼 선택자 부분에 태그 이름이 들어갑니다.

문서 내에 선택자에 해당하는 모든 요소에 스타일 규칙이 적용됩니다.

**그룹화**

- 선택자

    선택자는 쉼표를 이용해서 그룹화를 할 수 있습니다.

    ```html
    h1, h2, h3, h4, h5, h6 { color: yellow; }
    ```

    위 코드는 요소 선택자의 예제 코드와 같은 코드입니다.

- 전체 선택자

    그리고 전체 선택자 라고 불리는 간단한 선택자도 있습니다.

    ```html
    * { color: yellow; }
    ```

    *(별표, asterisk) 기호로 문서 내에 모든 요소를 선택할 수 있습니다.

    이렇게 선언하면, 한 번의 선언만으로 문서 내에 모든 요소에 스타일 규칙이 적용됩니다.

    전체 선택자는 매우 편리하지만, 성능에 좋지 않으므로 될 수 있으면 사용을 지양합니다.

- 선언

    선택자뿐만 아니라 선언들도 그룹화가 가능합니다.

    ```html
    h1 { color: yellow; font-size: 2em; background-color: gray; }
    ```

- 선택자 & 선언

    그리고 마지막으로 선택자와 선언이 동시에 그룹화도 가능합니다.

    ```html
    h1, h2, h3, h4, h5, h6 { color: yellow; font-size: 2em; background-color: gray; }
    ```

**3-2. class 선택자**

요소에 구애받지 않고 스타일 규칙을 적용할 수 있는 가장 일반적인 방법은 class 선택자를 활용하는 것입니다.

class 선택자를 사용하기 위해서는 HTML을 수정해 class 속성을 추가해야 합니다.

class 속성은 글로벌 속성이므로 어느 태그에서도 사용할 수 있습니다.

class 속성에 값을 넣게 되면, class 선택자를 이용해서 해당 요소에 스타일 규칙을 적용할 수 있습니다.

```css
.foo { font-size: 30px; }
```

```html
<p class="foo"> ... </p>
```

위 코드처럼 <p>의 class 속성의 값으로 "foo"라는 값을 넣었다면, CSS에서 그 값("foo")을 선택자로 지정하면 됩니다.

클래스 선택자를 쓸 때는, 맨 앞에 .(마침표)를 찍어주셔야 합니다.

이렇게 되면 어느 요소든지 class 속성값이 "foo"로 선언된 요소가 있다면 해당 스타일 규칙을 적용받게 됩니다.

그럼 이제 클래스 선택자를 이용해서 퀴즈를 풀어보겠습니다.

- Q. 아래 HTML 문서에서 "HTML"이라는 문자에는 보라색 글자를 지정하고, "CSS"라는 문자에는 밑줄을 선언하고 싶으면 어떻게 선택자를 사용해야 할까요?

    ```css
    .html { color: purple; }
    .css { text-decoration: underline; }

    ```

    ```html
    <dl>
    	<dt class="html">HTML</dt>
    	<dd><span class="html">HTML</span>은 문서의 구조를 나타냅니다.</dd>
    	<dt class="css">CSS</dt>
    	<dd><span class="css">CSS</span>는 문서의 표현을 나타냅니다.</dd>
    </dl>
    ```

```html
<dl>
	<dt>HTML</dt>
	<dd><span>HTML</span>은 문서의 구조를 나타냅니다.</dd>
	<dt>CSS</dt>
	<dd><span>CSS</span>는 문서의 표현을 나타냅니다.</dd>
</dl>
```

**다중 class**

class 속성은 꼭 하나의 값만 가질 수 있는 것은 아닙니다.

공백으로 구분하여 여러 개의 class 값을 넣을 수 있습니다.

```css
.foo { font-size: 30px; }
.bar { color: blue; }
```

```html
<p class="foo bar"> ... </p>
```

위의 <p>에 class 속성에 "foo" 와 "bar" 2개의 값을 넣었습니다.

그리고 foo class 선택자에는 폰트의 크기를 30px로, bar class 선택자에는 글자를 파란색으로 적용하는 스타일 규칙이 선언되어있습니다.

그렇게 되면 이 <p>에는 2개의 규칙이 모두 적용이 됩니다.

**3-3. id 선택자**

id 선택자를 쓸 때는, .(마침표) 기호 대신 #(해시) 기호를 써주시면 되고, 요소에는 class 속성 대신 id 속성만 써주면 됩니다.

```css
#bar { background-color: yellow; }
```

```html
<p id="bar"> ... </p>
```

이 <p>는 id 선택자의 스타일 규칙이 적용됩니다.

**class 선택자와의 차이점**

1. .기호가 아닌 #기호 사용
2. 태그의 class 속성이 아닌 id 속성을 참조
3. 문서 내에 유일한 요소에 사용
4. 구체성

가장 큰 차이점은 class와 달리 id는 문서 내에서 유일해야 한다는 점입니다.

클래스 선택자는 여러 요소에 같은 클래스를 넣고 같은 규칙을 적용 할 수 있었습니다. 그리고 그것이 클래스 선택자의 장점이기도 합니다.

하지만 id 속성값은 문서 내에 유일하게 사용이 되어야 합니다.

결국, id 선택자로 규칙을 적용할 수 있는 요소는 단 하나뿐입니다.

그리고 마지막으로 구체성의 값이 다릅니다. (이에 대한 자세한 설명은 이후 구체성 수업에서 다룹니다.)

**선택자의 조합**

```css
/* 요소와 class의 조합 */
p.bar { ... }

/* 다중 class */
.foo.bar { ... }

/* id와 class의 조합 */
#foo.bar { ... }

```

첫 번째는 요소와 클래스를 조합한 경우입니다.

이 경우에는 <p>이면서 class 속성에 bar가 있어야 적용됩니다.

두 번째는 다중 클래스의 경우입니다.

이 경우에는 class 속성에 foo와 bar가 모두 있어야 적용됩니다.

class="foo bar"

마지막은 id와 class를 조합한 경우입니다.

이 경우에는 id가 foo이며 class가 bar인 요소에 적용됩니다.

**3-4. 속성 선택자**

- **단순 속성으로 선택**

    ```css
    p[class] { color: silver; }
    p[class][id] { text-decoration: underline; }

    ```

    ```html
    <p class="foo">Hello</p>
    <p class="bar">CSS</p>
    <p class="baz" id="title">HTML</p>
    ```

    속성 선택자는 대괄호를 이용해서 선언하며 대괄호 안에 속성 이름이 들어갑니다.

    요소에 해당 이름의 속성이 있다면 해당 사항이 적용됩니다.

    위 CSS 코드는 요소 선택자와의 조합으로 이루어진 코드입니다.

    첫 번째는 <p>이면서 class 속성이 있는 요소이면 color: silver 규칙이 적용됩니다.

    두 번째는 <p>이면서 class 속성과 id 속성이 함께 있어야 text-decoration: underline 규칙이 적용됩니다.

    바로 위 HTML 코드에는 3개의 <p>가 있습니다.

    그렇다면 이 3개의 <p>에는 각자 어떤 스타일이 적용될까요?

    먼저 예측을 하시고 직접 실습을 하는 게 좋습니다.

    p[class] 선택자의 규칙은 class 속성만 존재하면 적용이 되기 때문에 3가지 요소 모두에 적용됩니다.

    p[class][id] 선택자의 규칙은 class 속성과 id 속성 모두 있는 요소만 해당하기 때문에 마지막 요소에만 적용됩니다.

    두 규칙 모두 속성의 값은 상관하지 않습니다.

- **정확한 속성값으로 선택**

    정확한 속성값으로 선택은 제목 그대로 속성의 값으로 요소를 선택합니다.

    선택자는 대괄호 안에 속성 이름과 속성값을 다 적으면 됩니다.

    ```css
    p[class="foo"] { color: silver; }
    p[id="title"] { text-decoration: underline; }

    ```

    p[class="foo"]는 <p>이면서 class 속성의 값이 foo이면 적용되고, p[id="title"]는 <p> 이면서 id 속성의 값이 title이면 적용됩니다.

- **부분 속성값으로 선택**

    부분 속성값으로 선택은 속성 이름과 속성값 사이에 사용되는 기호에 따라 동작이 조금 다릅니다.

    - [class~="bar"] : class 속성의 값이 공백으로 구분한 "bar" 단어가 포함되는 요소 선택
    - [class^="bar"] : class 속성의 값이 "bar"로 시작하는 요소 선택
    - [class$="bar"] : class 속성의 값이 "bar"로 끝나는 요소 선택
    - [class*="bar"] : class 속성의 값이 "bar" 문자가 포함되는 요소 선택

    ```css
    p[class~="color"] { font-style: italic; }
    p[class^="color"] { font-style: italic; }
    p[class$="color"] { font-style: italic; }
    p[class*="color"] { font-style: italic; }
    ```

    ```html
    <p class="color hot">red</p>
    <p class="cool color">blue</p>
    <p class="colorful nature">rainbow</p>
    ```

    위의 코드에서는 모두 class 속성값으로 "color"를 선택합니다.

    요소 순서대로 기호에 따라 규칙이 적용되는 결과는 다음과 같습니다.

    ```css
    p[class~="color"] { font-style: italic; } /* 1, 2번째 요소 */
    p[class^="color"] { font-style: italic; } /* 1, 3번째 요소 */
    p[class$="color"] { font-style: italic; } /* 2번째 요소 */
    p[class*="color"] { font-style: italic; } /* 1, 2, 3번째 요소 */
    ```

**3-5. 문서 구조 관련 선택자**

**문서 구조의 이해**

선택자와 문서의 관계를 이해하기 위해 먼저 어떻게 문서가 구조화되는지를 다시 한 번 살펴보겠습니다

```html
<html>
<body>
	<div>
		<h1><span>HTML</span>: Hyper Text Markup Language</h1>
	</div>
	<p>HTML과 CSS와 JAVASCRIPT를 이용해서 멋진 웹 사이트를 제작할 수 있습니다.</p>
</body>
</html>
```

위 HTML 코드에서 각 요소들을 짚어가면서 부모와 자식, 조상과 자손, 그리고 형제의 관계를 살펴보겠습니다.

- 부모와 자식

    부모 요소는 그 요소를 포함하는 가장 가까운 상위 요소로, 그 요소의 부모 요소는 단 하나뿐입니다.

    자식 요소는 부모 요소와 반대라고 생각하면 되며 자식 요소는 여러 개일 수도 있습니다.

- 조상과 자손

    조상과 자손의 관계는 부모와 자식의 관계와 비슷합니다.

    정확히 얘기하면 부모와 자식의 관계를 포함한 확장된 관계라고 생각하면 됩니다.

    조상 요소는 그 요소를 포함하는 모든 요소로, 부모 요소를 포함하여 여러 개일 수도 있습니다.

    자손 요소는 그 반대로, 그 요소가 포함하고 있는 모든 요소가 자손 요소입니다.


    보통 문서의 요소들은 모두 이처럼 어느 요소의 자식(자손) 요소이자 부모(조상) 요소가 되는 경우가 많습니다.

- 형제

    부모와 자식, 조상과 자손 말고도 형제 관계도 있습니다.

    같은 부모를 가지고 있는 요소들은 서로 형제 관계에 있습니다. 위 코드에서는 <div>, <p>가 형제 요소입니다.

    형제 관계 중에는 인접한 관계도 있습니다.

    형제 관계에 있는 요소 중 바로 뒤에 이어 나오는 요소를 인접해 있다고 합니다. 여기서 <p>가 <div>에 인접한 형제 요소가 됩니다.

문서의 구조는 흔히 가계도나 조직도의 관계와 비슷하다고 생각하면 이해하기가 쉽습니다.

**문서 구조 관련 선택자**

문서 구조를 이용한 선택자는 3가지

- 자손 선택자 : 공백

    ```css
    div span { color: red; }
    ```

    자손 선택자는 선택자 사이에 아무 기호없이 그냥 공백으로 구분을 합니다.

    이 선택자는 <div>의 자손 요소인 <span>를 선택하는 선택자 입니다.

- 자식 선택자 : 꺽쇠 기호(>)

    ```css
    div > h1 { color: red; }
    ```

    자식 선택자는 선택자 사이에 닫는 꺽쇠 기호(>)를 넣습니다.

    꺽쇠 기호와 선택자 기호 사이에는 공백은 있거나 없어도 상관이 없습니다.

    이 선택자는 <div>의 자식 요소인 <h1>를 선택하는 선택자 입니다.

- 인접 형제 선택자 : + 기호

    ```css
    div + p { color: red; }
    ```

    인접 형제 선택자는 선택자 사이에 + 기호를 넣습니다.

    자식 선택자와 마찬가지로 공백은 있거나 없어도 상관이 없습니다.

    인접 형제 선택자는 형제 관계이면서 바로 뒤에 인접해 있는 요소를 선택하는 선택자입니다.

    ```css
    /* body 요소의 자식인 div 요소의 자손인 table 요소 바로 뒤에 인접한 ul 요소 선택! */

    body > div table + ul { ... }
    ```

    위 코드처럼 문서 구조 관련 선택자는 더 복잡하게 사용할 수 있습니다.

    유의할 점은 요소들이 많이 나열되어 있더라도 제일 우측에 있는 요소가 실제 선택되는 요소라는 것입니다.

**3-6. 가상 선택자**

가상 선택자에는 가상 클래스와 가상 요소가 있습니다.

가상 클래스 선택자는 특정 요소의 상태를 미리 추정해서 가상의 클래스로 스타일을 적용할 수 있는 선택자입니다.

앞서 배운 class 선택자와는 조금 다르지만, 마치 클래스 선택자처럼 동작하기에 가상 클래스 선택자라고 부릅니다.

- **가상 클래스(pseudo class)**

    가상 클래스는 미리 정의해놓은 상황에 적용되도록 약속된 보이지 않는 클래스입니다.

    우리가 직접 요소에 클래스를 선언하는 것은 아니고, 약속된 상황이 되면 브라우저 스스로 클래스를 적용해줍니다.

    예를 들어, <p>가 있다고 가정하겠습니다.

    이 <p>에 마우스 커서를 올렸을 때만 특정 스타일을 주고 싶다고 한다면 어떻게 해야 할까요?

    가상 클래스가 없다면 이런 과정을 거치게 됩니다.

    1. 임의의 클래스 선택자를 선언하여 특정 스타일 규칙을 만든다.
    2. p 요소에 커서가 올라가면 p 요소에 클래스를 집어넣는다.
    3. p 요소에서 커서가 빠지면 p 요소에 클래스를 삭제한다.

    여기서 2, 3번은 동적으로 변화되어야 하는데, HTML과 CSS는 정적인 언어이기 때문에 처리할 수 없습니다.

    어쩔 수 없이 다른 언어를 사용해야 하는데, 이는 개발 비용이 들어가는 일입니다.

    그래서 CSS에서는 흔하게 사용되는 여러 패턴에 대해서 미리 정의해놓고, 가상 클래스로 제어할 수 있게 했습니다.

    ```css
    :pseudo-class {
        property: value;
    }
    ```

    위처럼 가상 클래스는 :(콜론) 기호를 써서 나타냅니다.

    가상 클래스를 이용하면 아래의 경우에도 CSS만으로 처리가 가능하므로 훨씬 효율적입니다.

    ":hover 가상 클래스 선택자를 이용해서 스타일 규칙을 만든다. (hover는 마우스 커서가 올라갔을 때 적용이 되도록 정의되어 있습니다.)"

    가상 클래스에는 여러 가지가 있습니다.

    이 수업에서는 가장 기초적이고 대표적인 가상 클래스만을 설명해 드리기 때문에 아래 링크를 참고 직접 공부하시길 바랍니다.

    [https://developer.mozilla.org/ko/docs/Web/CSS/Pseudo-classes](https://developer.mozilla.org/ko/docs/Web/CSS/Pseudo-classes)

    **문서 구조와 관련된 가상 클래스**

    문서 구조와 관련된 가상 클래스는 first-child와 last-child 가상 클래스 선택자 입니다.

    - :first-child : 첫 번째 자식 요소 선택
    - :last-child : 마지막 자식 요소 선택

    ```html
    <ul>
    	<li>HTML</li>
    	<li>CSS</li>
    	<li>JS</li>
    </ul>
    ```

    ```css
    li:first-child { color: red; }
    li:last-child { color: blue; }
    ```

    첫 번째 <li>와 마지막 <li>에 가상 클래스가 적용됩니다.

    실제 <li>에는 class 속성이 없지만 내부적으로 가상 클래스가 적용되어 마치 아래의 코드와 같이 동작하게 됩니다.

    ```html
    <ul>
    	<li class="first-child">HTML</li>
    	<li>CSS</li>
    	<li class="last-child">JS</li>
    </ul>
    ```

    **앵커 요소와 관련된 가상 클래스**

    앵커 요소와 관련된 가상 클래스로는 :link와 :visited가 있습니다.

    - :link : 하이퍼 링크이면서 아직 방문하지 않은 앵커
    - :visited : 이미 방문한 하이퍼링크를 의미

    하이퍼 링크는 앵커 요소에 href 속성이 있는 것을 의미합니다.

    ```css
    a:link { color: blue; }
    a:visited { color: gray; }

    ```

    **사용자 동작과 관련된 가상 클래스**

    이 클래스들도 <a>에 주로 많이 쓰입니다.

    <a>에만 쓸 수 있는 것은 아니며, 이 조건에 맞는 상황이 되는 요소들은 다 사용이 가능합니다.

    - :focus: 현재 입력 초점을 가진 요소에 적용
    - :hover: 마우스 포인터가 있는 요소에 적용
    - :active: 사용자 입력으로 활성화된 요소에 적용

    ```css
    a:focus { background-color: yellow; }
    a:hover { font-weight: bold; }
    a:active { color: red; }
    ```

    :focus는 현재 입력 초점을 가진 요소에 적용됩니다.

    focus(초점)는 지금 현재 선택을 받는 것을 의미합니다.

    예를 들면, 입력 폼 요소에 텍스트를 입력하려고 마우스 클릭해서 커서를 입력 폼 위에 올려놓으면 그때 입력 폼 요소가 초점을 받는 상태입니다.

    또 키보드의 탭 키를 이용해서 요소를 탐색하다 보면 링크나 버튼에 점선 테두리가 이동하는 것을 볼 수 있는데, 점선 테두리가 위치하는 것도 초점을 받은 상태입니다.

    :hover는 마우스 커서가 있는 요소에 적용됩니다. (마우스를 올렸을 때를 의미합니다.)

    :active는 사용자 입력으로 활성화된 요소를 의미하는데, <a>를 클릭할 때 또는 <button>를 눌렀을 때처럼 순간적으로 활성화됩니다.

가상 요소는 가상 클래스와 비슷합니다. 다만 클래스가 아닌 요소라는 점만 다릅니다.

가상 요소는 현재 문서 내에 존재하지 않는 구조, 즉 문서에 존재하지 않는 요소에 내용을 추가할 수 있고, 또 스타일도 부여할 수 있습니다.

예를 들어 가장 자주 쓰이는 가상 요소는, 요소의 앞이나 뒤에 별도의 내용을 추가하는 것입니다.

이 때 추가되는 새 콘텐츠는 HTML 코드에 직접 추가되지 않고 브라우저 화면에만 나타납니다.

- **가상 요소(pseudo element)**

    가상 요소는 HTML 코드에 존재하지 않는 구조 요소에 스타일을 부여할 수가 있습니다.

    가상 요소도 가상 클래스처럼 문서 내에 보이지 않지만, 미리 정의한 위치에 삽입되도록 약속이 되어있습니다.

    선언 방법은 가상 클래스와 같게 콜론을 사용하며,

    CSS3부터는 가상 클래스와 가상 요소를 구분하기 위해 가상 요소에는 ::(더블 콜론) 기호를 사용하기로 했습니다.

    하지만 하위 브라우저에서 :: 문법을 지원하지 않는 문제가 있으므로 상황에 따라 : 기호를 사용하셔야 합니다.

    ```css
    ::pseudo-element {
        property: value;
    }
    ```

    강의에서는 가상 클래스와 마찬가지로 기본적인 가상 요소만 설명해 드리고 마치도록 하겠습니다.

    다른 가상 요소들에 대한 자세한 내용은 아래 링크를 참고해주세요.

    [https://developer.mozilla.org/ko/docs/Web/CSS/Pseudo-elements](https://developer.mozilla.org/ko/docs/Web/CSS/Pseudo-elements) 

    - :before : 가장 앞에 요소를 삽입
    - :after : 가장 뒤에 요소를 삽입
    - :first-line : 요소의 첫 번째 줄에 있는 텍스트
    - :first-letter : 블록 레벨 요소의 첫 번째 문자

    ```html
    <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.</p>
    ```

    ```css
    p::before { content: "###" }
    p::after { content: "!!!" }
    p::first-line { ... }
    p::first-letter { ... }
    ```

    before와 after 가상 요소는 애초에 내용이 없는 상태로 생성되기 때문에 내용을 넣기 위해 content 속성을 이용해야 합니다.

    실제 HTML 코드에는 나타나지 않지만, before와 after가 어떻게 동작하는지 이해를 돕기 위해 코드를 아래와 같이 변경했습니다.

    ```html
    <p>
    	<before>###</before>
        Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.
      <after>!!!</after>
    </p>
    ```

    눈에 보이지 않지만, 내부에서 이처럼 요소가 생성됩니다.

    first-line과 first-letter도 마찬가지로 아래 코드와 같은 것으로 생각하시면 됩니다.

    ```html
    <p>
    	<first-letter>L</first-letter>orem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.
    </p>
    <p>
    <!-- 모니터 가로 해상도에 따라 요소가 포함하는 내용이 변동됩니다. -->
      <first-line>Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiu ..(..어딘가쯤..) </first-line>... unt ut labore et dolore magna aliqua.
    </p>
    ```

[반드시 기억해야 하는 CSS 선택자 30개](https://code.tutsplus.com/ko/tutorials/the-30-css-selectors-you-must-memorize--net-16048)
