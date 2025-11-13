# CSS

### 1. CSS 적용 방법

| 적용 방법 | 사용 빈도 | 상세 설명 |
| --- | --- | --- |
| **인라인 스타일 (inline style)** | 거의 사용하지 않음 | HTML 태그마다 style 속성으로 CSS 코드를 넣어주는 방식입니다. 여러 요소들에 공통 속성을 재사용하여 부여할 수 없고 HTML 코드와 CSS 코드가 분리되지 않기 때문에 특별한 경우를 제외하고는 사용되지 않습니다. |
| **내부 스타일 시트 (internal style sheet)** | 코드량이 적을 때 | head 태그 안에 style 태그를 두고 그 안에 CSS 코드를 작성하는 방식입니다. HTML과 CSS의 전체 코드량이 많지 않고 CSS가 해당 HTML 문서에서만 적용될 경우 유용하게 사용될 수 있습니다. |
| **링킹 스타일 시트(linking style sheet)** | ⭐️ 주로 사용 | 외부의 CSS 파일을 HTML 문서에 연결하는 것입니다. HTML과 CSS의 코드가 분리되고 CSS 코드를 여러 HTML 파일에서 공통으로 사용할 수 있으므로 가장 널리 사용되는 방식입니다. |

### 2. 선택자

```css
/* 모든 요소 선택 */
* {
  font-weight: bold;
  color: darkorange;
}

/* 같은 선택자의 경우 뒤에 오는 것이 우선순위 높음 */
* {
  color: plum;
}

/* 태그 선택자 */
p {
  color: olivedrab;
}

/* class 선택자 */
/* 태그보다 우선순위 높음 */
/* 페이지상의 여러 요소가 같은 class를 가질 수 있음 */
.blue {
  color: lightblue;
}

/* 다른 선택자에 이어붙일 수 있음(태그, 클래스 등...) */
/* 선택자는 구체적일수록 우선순위 높음 */
p.blue {
  color: slateblue;
}

.blue.dark {
  color: mediumblue;
}

p.blue.dark {
  color: darkblue;
}

/* id 선택자 */
/* class보다 우선순위 높음 */
/* id는 페이지상에서 요소마다 고유해야 함 */
#red {
  color: tomato;
}

/* 그룹 선택자 */
span, .dark, #red {
  text-decoration: underline;
}
```

### 3. 결합자와 가상 클래스

**1) 결합자**

```css
/* 자손 결합자 */
.outer li {
  color: olivedrab;
}

/* 자식(1촌 자손) 결합자 */
.outer > li {
  color: dodgerblue;
}

.outer > li li {
  text-decoration: underline;
}

/* 뒤따르는 모든 동생들 결합자 */
.starter ~ li {
  font-style: italic;
}

/* 뒤따르는 바로 다음 동생 결합자 */
.starter + li {
  font-weight: bold;
}
```

**2) 가상 클래스**

```css
/* 첫 번째, 마지막 요소 가상 클래스 */
ol li:first-child,
ol li:last-child {
  color: yellowgreen;
}

/* ~가 아닌 요소 가상 클래스 */
.outer > li:not(:last-child) {
  text-decoration: line-through;
}

ul:not(.outer) li {
  font-weight: bold;
}

/* ~번째 요소 가상 클래스 */
/* #, #n, #n+#, odd, even 등 시도해보기 */
ol li:nth-child(3) {
  font-weight: bold;
  color: deeppink;
}

/* 마우스오버 가상 클래스 */
li:hover {
  font-weight: bold;
  color: blue;
}
```

### 4. CSS 기본 문법

```css
선택자 {
  속성1: 값;
  속성2: 값;
  /* ... */
}
```

### 5. 글자와 텍스트 스타일

| 속성 | 값 | 목적 | 설명 |
| --- | --- | --- | --- |
| **font-style** | normal, italic, oblique | 글자를 기울임 | *italic*과 *oblique*은 얼핏 보면 비슷한데 italic이 '기울여서 쓴' 서체라면 oblique는 본래 서체를 기울여 놓은 것입니다. 서체마다 둘 다 있거나 한 쪽만 있거나 둘 다 없을 수도 있는데이들은 한쪽이 없을 시 상호 교차되어 사용됩니다. |
| **font-weight** | normal or bold, 100 ~ 900 | 글자의 굵기를 조절 | 서체가 어떤 굵기를 지원하느냐에 따라 *normal*과 *bold*중에 선택하거나100~900 사이 100 단위의 수치를 사용합니다. |
| **font-size** | px, %, em, rem | 글자의 크기를 지정 | 단위로는 *px*과 *%*, *em*, *rem을* 사용합니다. *px*는 절대값으로서 픽셀 단위입니다. *100%*는 *1em*으로, 이들은 부모 요소와의 상대적 크기를 나타내죠. *rem*은 html 요소와의 상대적 크기를 가지므로, 요소의 중첩에 영향을 받지 않습니다. *pt*는 1인치/72로, 프린트할 컨텐츠에 사용됩니다. |
| **text-decoration** | none, underline, line-through, wavy, dotted | 밑줄, 취소선, 물결선 등으로 글을 꾸밈 | 여러 꾸밈요소를 함께 사용할 수 있으며 선의 형태, 색, 굵기 등 디테일을 지정할 수도 있습니다. |
| **text-transform** | none, capitalize, uppercase, lowercase | 알파벳의 대소문자 표시 | HTML, CSS와 같이 대문자로 작성된 텍스트는 *capitalize*에 영향을 받지 않습니다. |
| text-shadow | x좌표, y좌표, 흐림(선택), 색 | 텍스트에 그림자 | 'x좌표, y좌표, 흐림(선택), 색' 형식으로 그림자를 넣을 수 있고 쉼표로 구분해서 여럿을 넣을 수도 있습니다. |

### 6. 문단 스타일

| **속성** | 값 | 목적 |
| --- | --- | --- |
| **text-align** | left, right, center, justify | 글자를 기울일 때 사용 |
| **letter-spacing** | (px, %, em, rem) | 자간 |
| **word-spacing** | (px, %, em, rem) | 단어 간격 |
| **line-height** | (px, %, em, rem) | 줄 높이 |
| **text-indent** | (px, %, em, rem) | 들여쓰기 |

### 7. 목록 스타일

ul과 ol 목록의 불릿, 숫자 스타일을 지정할 수 있습니다. ul, ol 여부와 관계없이 기호, 서수, 원하는 문자, 이모지, 심지어 이미지까지 사용할 수 있습니다.

| **속성** | 값 | 목적 |
| --- | --- | --- |
| **list-style (ul)** | disc, circle, square, “- “, “👉 ”, url(./yennie.png), none | 도형 리스트 스타일 지정 |
| **list-style (ol)** | decimal, lower-alpha, upper-alpha, lower-roman, upper-roman, lower-greek | 숫자 리스트 스타일 지정 |

```css
ul {
  list-style: circle;
}

/* li별로 지정하는 것도 가능 */
ul > li:first-child {
  list-style: "🚩 "
}

ol {
  list-style: lower-alpha;
}
```

### 8. 색상 표현하기

| **속성** | 값 | 분류 | 목적 |
| --- | --- | --- | --- |
| background-color | white, black | keyword | 지정된 색상을 사용 |
|  | rgb(225, 225, 225) | RGB(A) | 빨강, 초록, 파랑의 광원으로 색을 혼합하는 방식이며, 끝에 알파값을 붙여서 투명도 조절 가능 |
|  | #FFFFFF | HEX | R, G, B, Alpha 값들을 16진수 형태로 나타낸 것 |
|  | hsl(0, 100%, 100%) | HSL(A) | 색상, 채도, 명도값 그리고 알파값을 조합한 것 |

### 9. 인라인 요소와 블록 요소

**인라인 요소**는 비닐이나 랩 안에 내용물을 넣은 것과 같습니다. 일정한 바깥 형태나 껍데기 없이 페이지의 흐름에 따라 다른 텍스트나 컨텐츠와 어우러져 배치됩니다. 반면, **블록 요소**는 딱딱한 상자와도 같습니다. 사각형의 형태를 갖고 있으며 너비와 높이, 안팎의 간격을 부여받을 수 있습니다.

| **속성** | 값 | 기본 너비 | 가로 공간 | `margin` (밖 여백) | `padding` (안 여백) | `width`, `height` |
| --- | --- | --- | --- | --- | --- | --- |
| display | inline | 컨텐츠 만큼 (Hug) | 공유 | ↔️ 가로만 | ↔️가로만, ↕️세로는 배경색만 | ❌ 무시 |
|  | block | 부모의 너비만큼 (Fill) | ⭐️ 독점 | 모두 적용 | 모두 적용 | 적용 |
|  | inline-block | 컨텐츠 만큼 (Hug) | 공유 | 모두 적용 | 모두 적용 | 적용 |
