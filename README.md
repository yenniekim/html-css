# CSS

### 1. CSS 적용 방법

| 적용 방법 | 언제 쓰나 | 상세 설명 |
| --- | --- | --- |
| **인라인 스타일 (inline style)** | 거의 안 씀 | HTML 태그 안에 직접 `style=""` 로 작성. 재사용 불가, 유지보수 어려움. 디버깅할 때 응급 패치 수준에서만 잠깐 사용 |
| **내부 스타일 시트 (internal style sheet)** | 코드량 적음, 단일 HTML 파일 프로젝트 | `<head>` 안의 `<style>` 태그에 CSS 작성. HTML과 CSS가 같은 파일에 있어 편하지만, 문서가 커지면 유지보수 어려움 |
| **외부 스타일 시트 (linking style sheet)** | 실전 웹 개발 전부 ⭐️ | CSS를 `.css` 파일로 분리. 여러 HTML 문서에서 공통으로 사용 가능. 구조 분리로 유지보수 최고 |


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

### 5. 글자 스타일

| 속성 | 값 | 목적 |
| --- | --- | --- |
| **font-style** | normal, italic, oblique | 글자를 기울임 |
| **font-weight** | normal or bold, 100 ~ 900 | 글자의 굵기를 조절 |
| **font-size** | px, %, em, rem | 글자의 크기를 지정 |
| **text-decoration** | none, underline, line-through, wavy, dotted | 밑줄, 취소선, 물결선 등으로 글을 꾸밈 |
| **text-transform** | none, capitalize, uppercase, lowercase | 알파벳의 대소문자 표시 |
| **text-shadow** | x좌표, y좌표, 흐림(선택), 색 | 텍스트에 그림자 |


### 6. 문단 스타일

| 속성 | 값 | 목적 |
| --- | --- | --- |
| **text-align** | left, right, center, justify | 글자를 기울일 때 사용 |
| **letter-spacing** | px, %, em, rem | 자간 |
| **word-spacing** | px, %, em, rem | 단어 간격 |
| **line-height** | px, %, em, rem | 줄 높이 |
| **text-indent** | px, %, em, rem | 들여쓰기 |


### 7. 목록 스타일

| 속성 | 분류 | 값 | 목적 |
| --- | --- | --- | --- |
| **list-style** | ul | disc, circle, square | 기본 도형 불릿 |
|  |  | “- “, “👉 ” | 커스텀 기호 불릿 |
|  |  | url(./yennie.png) | 이미지 불릿 |
|  | ol | decimal | 1, 2, 3… |
|  |  | lower-alpha, upper-alpha | a, b, c… / A, B, C… |
|  |  | lower-roman, upper-roman | i, ii, iii… / I, II, III… |
|  |  | lower-greek | α, β, γ… |
|  |  | none | 불릿 제거 |

```css
ul {
  list-style: circle;
}

/* li별로 지정하는 것도 가능 */
ul > li:first-child {
  list-style: "🚩 ";
}

ol {
  list-style: lower-alpha;
}
```

### 8. 색상 표현하기

| 속성 | 분류 | 값 | 설명 | 언제 쓰나 |
| --- | --- | --- | --- | --- |
| background-color | keyword | white, black, skyblue | 기본 이름 색 | 간단한 스타일, 프로토타입 |
|  | RGB(A) | rgb(225, 225, 225) | 빛 기반 색 표현 / 알파 가능 | 가벼운 투명도 설정 |
|  | HEX | #FFFFFF | RGB, Alpha 값을 16진수로 표현 | 웹 전반에서 가장 보편적 |
|  | HSL(A) | hsl(0, 100%, 100%) | 색상(Hue)·채도(Saturation)·명도(Lightness) | 브랜드 컬러 튜닝 할 때 직관적 |


### 9. 인라인 요소와 블록 요소

- inline : 흐름 속 텍스트
- block : 한 줄 독점 박스
- inline-block : 두 세계의 장점만 가져간 하이브리드

| 속성 | 값 | 기본 너비 | 가로 공간 | margin / padding | width / height  | 언제 쓰나 |
| --- | --- | --- | --- | --- | --- | --- |
| display | inline | 컨텐츠 만큼 (Hug) | 공유 | 가로만 ↔️  | ❌ | 링크, 텍스트 조각 |
|  | block | 부모의 너비 (Fill) | 독점 ⭐️ | 전체 | ⭕️ | 섹션, div, 레이아웃 |
|  | inline-block | 컨텐츠 만큼 (Hug) | 공유 | 전체 | ⭕️ | 버튼, 태그, 뱃지 |


### 10. 박스

**1) 단위**

| 속성 | 값 | 사용 예시 | 설명 | 언제 쓰나 |
| --- | --- | --- | --- | --- |
| width, height | *%* | 50% | 부모 기준 비율 | 반응형 레이아웃 |
|  | vw, vh | 50vw, 100vh | 뷰포트 (viewport) 기준 | 전체 화면 배너, 히어로 |
|  | vmin | 20vmin | 더 작은 축 기준 | 정사각 로고, 아이콘 |
|  | vmax | 20vmax | 더 큰 축 기준 | 큰 배경 텍스트, 연출 요소 |
|  | calc() | calc(100% - 50px) | 연산 가능 | 고정 + 유동 혼합 레이아웃 |

**2) 최대값 / 최솟값**

| 속성 | 값 | 목적 |
| --- | --- | --- |
| max-width | px, %, vw/vh | 최대 가로 제한 |
| min-width | px, %, vw/vh | 최소 가로 제한 |
| max-height | px, %, vh 등 | 최대 높이 제한 |
| min-height | px, %, vh 등 | 최소 높이 제한 |

**3) margin과 padding** 

값은 ‘북 동 남 서’로 시계 방향 ⏰으로 정의합니다.

| 속성 | 값 | 설명  | 언제 쓰나 |
| --- | --- | --- | --- |
| **margin (밖 여백)** | px | 고정 | 컴포넌트 내부 여백 |
|  | em | 부모의 font-size 기준 | 중첩될수록 비례 증가 |
|  | rem* | html 기준 고정 | 접근성 대응, 반응형 기본 |
|  | auto | 남는 공간 자동 분배 | 요소 가운데 정렬 |
| **padding (안 여백)** | px, vmin, em 등 |  |  |

**4) border**

| 속성 | 값 | 설명 |
| --- | --- | --- |
| **border** | 2px solid #ededed | 선 두께·스타일·색 |
| **border-top** | 1px dashed black | 속성값으로 방향 지정 가능 (border-bottom, border-left, border-bottom) |
| **box-sizing ⭐️** | border-box ⭐️ | padding과 border 값 포함 |
|  | content-box | padding과 border 값 미포함 |
| **border-radius** | px, em, % | 둥글게 |


**5) overflow**

부모 박스보다 자식이 커져서 튀어나올 때 그 튀어나온 부분을 어떻게 보여줄지 결정하는 속성입니다.

| 속성 | 값 | 설명 | 언제 쓰나 |
| --- | --- | --- | --- |
| **overflow** | visual | 넘쳐도 보임 | 기본값 |
|  | hidden | 잘라버림 | thumbnail mask |
|  | scroll | 항상 스크롤 표시 | 긴 리스트 |
|  | auto | 필요할 때만 스크롤 | modal 콘텐츠 |
| **overflow-x** | visual, hidden, auto, scroll |  |  |
| **overflow-y** | visual, hidden, auto, scroll |  |  |


**6) box-shadow**

`inset 여부 | offset-x | offset-y | blur | spread | color` 순서로 사용합니다.

| 속성 | 값 | 설명 |
| --- | --- | --- |
| box-shadow | inset | 안쪽 그림자 |
|  | offset-x | offset-y | 그림자 이동 |
|  | blur | 번짐 정도 |
|  | spread | 그림자의 크기 |


### 11. 배경

**1) 이미지**

| 속성 | 값 | 설명 |
| --- | --- | --- |
| background-image | url(./img/landscape.jpg) | 절대경로, 상대경로 모두 가능 |
| background-repeat | repeat, no-repeat / repeat-x, repeat-y | 가로·세로 반복(기본값), 반복 없음 / 가로만 반복, 세로만 반복 |
| background-position | top left, top, bottom / left, right | 기준 위치 설정 / 이미지 정렬 |
|  | 50% 50%  | 가운데 정렬 |
| background-size | auto | 원본 크기 그대로 |
|  | contain | 이미지 전체 보이게 맞춤 (빈틈 생김) |
|  | cover | 화면 꽉 채움 (잘릴 수 있음) |
|  | % | 부모 비율 기준 |
|  | 200px auto | 가로 200px + 세로 자동 비율 유지 |

2) 그라데이션

linear-gradient(`방향`, `색상1 종료%`, `색상2 종료%`, `색상3 종료%`) 순서로 사용합니다.

| 속성 | 값 |
| --- | --- |
| background | linear-gradient(90deg, red 10%, white 40%, blue 100%) |
|  | radial-gradient(#e66465, #9198e5) |
|  | repeating-linear-gradient(#f69d3c, #3f87a6 50px) |
|  | repeating-radial-gradient(#f69d3c, #3f87a6 50px) |
|  | conic-gradient(#f69d3c, #3f87a6) |

