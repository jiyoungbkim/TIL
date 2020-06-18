## CSS 이해하기
### 1. CSS 소개

웹 페이지를 사람에 비유해보자면, 마크업 언어(HTML)는 몸의 구조(뼈, 근육)를 담당하고

CSS는 옷과 신발과 같이 외적으로 꾸며주는 역할을 한다고 생각하면 이해하기 쉽습니다.

Cascading Style Sheets

- HTML(마크업 언어)을 꾸며주는 표현용 언어
- HTML이 웹페이지의 정보를 표현한다면, CSS는 HTML을 보기 좋게 디자인하는 역할

**CSS와 HTML**

CSS는 간단히 이야기하면 HTML(마크업 언어)을 꾸며주는 표현용 언어입니다.

HTML이 문서의 정보, 구조를 설계한다면 CSS는 문서를 보기 좋게 디자인합니다.

CSS는 분명히 HTML과는 독립된 다른 언어지만 마크업 문서 자체가 존재하지 않으면 CSS는 무용지물이나 마찬가지입니다.

왜냐하면, CSS는 표현을 위한 언어인데 마크업 문서가 없다면 표현할 대상이 없기 때문입니다.

그래서 CSS는 보통 마크업 언어인 HTML과 같이 묶어서 이야기합니다.

**CSS로 표현한 다양한 웹 사이트들**

전 세계에 많은 웹 사이트들이 있습니다.

그리고 그것들 모두 HTML 태그를 이용해서 만들어졌고, 자주 사용되는 태그의 개수는 10여 개밖에 되지 않습니다.

결국, 모든 사이트가 비슷한 HTML 태그를 사용해서 만들어졌음에도 불구하고 각각 다양하고 독창적인 디자인으로 표현 가능한 이유가 바로 CSS 덕분입니다.

CSS는 문서를 디자인하는 강력한 힘을 가졌습니다.

아래 참고 링크를 방문하면 하나의 HTML이 다양한 CSS를 통해 바뀌는 것을 확인할 수 있습니다.

참고링크

[CSS Zen Garden](http://www.csszengarden.com/)

### 2. CSS 문법과 적용

CSS는 HTML 요소를 꾸며주는 역할을 합니다.

CSS는 꾸밀 대상이 되는 요소와 그에 대한 스타일 내용으로 이루어져 있습니다.

**CSS 구문**

```css
h1 { color: yellow; font-size:2em; }
```

- 선택자(selector) - "h1"
- 속성(property) - "color"
- 값(value) - "yellow"
- 선언(declaration) - "color: yellow", "font-size: 2em"
- 선언부(declaration block) - "{ color: yellow; font-size:2em; }"
- 규칙(rule set) - "h1 { color: yellow; font-size:2em; }"

CSS 파일은 여러 개의 규칙으로 이루어져 있습니다.

선택자와 선언부 사이, 선언과 선언 사이는 앞뒤로 개행을 해도 상관이 없습니다.

하지만 속성이름과 속성값 사이에는 개행을 하면 안 됩니다.


**CSS의 속성(Property)과 HTML의 속성(Attribute)**

HTML에도 속성이 있고, CSS에도 속성이 있습니다. 두 가지는 전혀 다른 것입니다.

HTML의 속성은 영어로 attribute이고, CSS의 속성은 property입니다.

둘 다 한국어로 번역할 때 "속성"이라고 하므로 잘 구분하셔야 합니다.


**CSS의 적용**

CSS와 문서를 연결하는 방법은 4가지가 있습니다.

- 1. Inline
- 2. Internal
- 3. External
- 4. Import
