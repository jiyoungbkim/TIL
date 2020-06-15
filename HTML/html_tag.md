## HTML 태그 간단히 보기

### 1. 제목과 단락 요소

- 제목(Heading) : h1~h6
- 단락(Paragrah) : p
- 개행(Linebreak) : br

### 2. 텍스트를 꾸며주는 요소

- <b> : bold 태그</b>
- <i> : italic 태그</i>
- <u> : underline 태그</u>
- <s> : strike 태그</s>

### 3. 앵커 요소

다른 문서로 이동할 수 있는 링크를 생성

<a>(anchor 태그)는 a태그, 앵커, 링크 등 여러 이름으로 불립니다.

```html
<a href="[http://www.naver.com/](http://www.naver.com/)" target="_blank">네이버</a>
```

- href(hypertext reference) 속성
- target 속성
- 내부링크
- 기타 속성

### 4. 의미없이 요소를 묶기 위한 컨테이너 요소

- div : block-level
- span : inline-level

### 5. 리스트 요소

- ul(unordered list) 태그
- ol(ordered list) 태그
- dl(definition/description list) 태그
- 리스트 중첩

### 6. 이미지 요소

<img>는 문서에 이미지를 삽입하는 태그로, 닫는 태그가 없는 빈 태그

```html
<img src="./images/pizza.png" alt="피자">
```

- src 속성
- alt 속성
- width/height 속성
- 상대경로와 절대경로
- *이미지 파일 형식

### 7. 테이블 요소

### 표의 구성 요소

- table : 표를 나타내는 태그
- tr : 행을 나타내는 태그
- th : 제목 셀을 나타내는 태그
- td : 셀을 나타내는 태그

### 표의 구조와 관련된 태그

- caption: 표의 제목을 나타내는 태그
- thead : 제목 행을 그룹화하는 태그
- tbody : 본문 행을 그룹화하는 태그
- tfoot : 바닥 행을 그룹화하는 태그
- HTML 버전에 따라 tfoot의 위치가 변경
- colgroup
- col

### 테이블 관련 속성

- colspan : 셀을 가로방향으로 병합
- rowspan : 셀을 세로방향으로 병합
- scope 속성
- header 속성

### 8. 폼 관련 요소

서버에 데이터를 전달하기 위한 요소들

- input : 대표적인 폼 요소. 인라인 레벨 요소
- select : 선택 목록 상자 또는 콤보박스
- textarea : 여러 줄의 텍스트를 입력할 때 사용
- button : 버튼을 만들 때 사용
- label : form 컨트롤과 연결 시켜주기 위함으로 웹 접근성 향상에 도움(필수적)
- fieldset : 여러 개의 폼 요소를 그룹화하여 구조화
- legend : 폼 요소의 제목으로 <fieldset> 내부에 작성
- form : 데이터를 묶어서 실제 서버로 전송해주는 역할을 하는 태그

출처 : [부스트코스] 비전공자를 위한 HTML/CSS
