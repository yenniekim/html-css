#HTML

### List

여러 항목을 구조적으로 나열해 콘텐츠를 그룹화하고, 정보의 위계·순서를 명확하게 전달하는 역할을 합니다.

| Element | Attribute |  | Description |
| --- | --- | --- | --- |
| ul |  |  | unordered list, 순서가 없는 목록 |
| ol |  |  | ordered list, 순서가 있는 목록 |
|  | type | 1, I, i, A, a | 등 다양한 타입 선택 가능 |
|  | start | `{정수}` | 1~ 시작 지점 선택 가능 |
| li |  |  | list item, 목록 아이템. `ul`, `ol` 태그의 1촌 자식으로 이 태그만 가능 |

```html
<ol>
   <li>재료 준비
	      <ul>
	        <li>밥
			       <ul>
				       <li>쌀 10kg 구매 필요</li>
				       <li>22시 전까지 구매 필요</li>
			       </ui>
			    </li>
	        <li>파</li>
	        <li>간장</li>
	       </ul>
   </li>
   <li>파를 기름에 볶기</li>
   <li>밥 넣고 볶기</li>
   <li>계란을 넣고 스크램블</li>
   <li>간장을 넣고 마저 볶아 완성</li>
</ol>
```

### Image

외부 이미지 파일을 문서에 표시하기 위한 요소로, `src`로 경로를 지정해 이미지를 렌더링합니다.

| Element | Attribute | Attribute value | Description |
| --- | --- | --- | --- |
| img | src | `{URL}` | source, 원본파일 경로. 절대경로 또는 상대경로 |
|  | alt | `{글자}` | alternative text, 대체 텍스트. 스크린 리더, 원본파일 무효시 |
|  | title | `{글자}` | hover 시 표시. alt의 대체제나 반복이 되어서는 안됨 |
|  | width | `{정수}` | 너비. 픽셀 단위의 정수로 표현 |
|  | height | `{정수}` | 높이. 픽셀 단위의 정수 |

```html
<img 
	src="./coding.png" 
	alt="코딩중인 노트북" 
	title="프로그래밍"
	wight="600"
	height="400"
>
```

### Table

행(row)과 열(column) 구조로 데이터를 표 형태로 정렬·표현하는 요소이며, 표는 왼쪽에서 오른쪽 ➡️ 위에서 아래 ⬇️ 순으로 채웁니다.

| Element | Attribute | Attribute value | Description |
| --- | --- | --- | --- |
| table |  |  | 표 전체를 감싸는 태그 |
| caption |  |  | 표의 제목 또는 설명 (선택 사항) |
| thead |  |  | 헤더 부분으로 각 기둥 제목 |
| tbody |  |  | 실제 데이터 부분 |
| tfoot |  |  | 합계, 요약 같은 마지막 부분 |
| tr |  |  | table row, 가로 한 줄 |
| th | scope | row, col | table header, 헤더 셀로 제목 역할. 범위 지정 |
| td | scope | row, col | table data, 일반 데이터 셀. 범위 지정 |
|  | colspan | `{정수}` | column span, 열 (세로) 병합 |
|  | rowspan | `{정수}` | row span, 행 (가로) 병합 |
| colgroup |  |  | 열 단위로 스타일을 주고 싶을 때 사용. `caption` 보다 뒤, 그 외 요소보다 앞에 와야 함 |
| col | span | `{정수}` | column, 각 열 하나. `span` 속성으로 범위 지정 |
|  | class | `{글자}` | `class` 속성을 통해 CSS에서 스타일 지정 |

**셀 병합**

```html
<table>
	<tr>
		<td>1</td>
		<td colspan="2">2</td>
		<td>1</td>
	</tr>
	<tr>
		<td rowspan="3">3</td>
		<td>1</td>
		<td>1</td>
		<td>1</td>
	</tr>
	<tr>
		<td>1</td>
		<td colspan="2" rowspan="2">4</td>
	</tr>
	<tr>
		<td>1</td>
	</tr>
</table>
```

**thead 및 th**

```html
	<table>
		<caption>웹개발 공부 기록</caption>
		<thead>
			<tr>
				<th scope="col">과목</th>
				<th scope="col">월</th>
				<th scope="col">화</th>
			</tr>
		</thead>
		<tbody>
			<tr>
				<th scope="row">HTML</th>
				<td>60분</td>
				<td>60분</td>
			</tr>
			<tr>
				<th scope="row">CSS</th>
				<td>0분</td>
				<td>30분</td>
			</tr>
			<tr>
				<th scope="row">JS</th>
				<td>0분</td>
				<td>0분</td>
			</tr>
		</tbody>
		<tfoot>
			<tr>
				<th scope="row">총 시간</th>
				<td>60분</td>
				<td>90분</t
			</tr>
		</tfoot>
	</table>
```

**colgroup 및 col 사용**

```html
<table>
		<colgroup>
			<col class="weekend">
			<col span="5">
		</colgroup>
		<thead>
			<tr>
				<th scope="col">일</th>
				<th scope="col">월</th>
				<th scope="col">화</th>
				<th scope="col">수</th>
				<th scope="col">목</th>
				<th scope="col">금</th>
				<th scope="col">토</th>
			</tr>
		</thead>
		<tbody>
			<tr>
				<td>_</td>
				<td>_</td>
				<td>_</td>
				<td>_</td>
				<td>_</td>
				<td>_</td>
				<td>_</td>
			</tr>
		</tbody>
	</table>
```

### Link

사용자가 클릭하면 웹의 한 지점에서 다른 지점으로 즉시 이동하도록 만들어주는 연결 요소입니다.

| Element | Attribute | Attribute value | Description |
| --- | --- | --- | --- |
| a | href | `{URL}` | anchor, **h**ypertext **ref**erence, 페이지 이동이 필요한 주소 및 `#{...}` |
|  |  | mailto:, tel: | 주소(`mailto:`) 및 연락처(`tel:`) 정보 표현 가능 |
|  | target | _self | 링크를 열 옵션 선택. 현재 창에서 페이지 이동 (기본) |
|  |  | _blank | 새 창 열림. 텍스트나 내부 이미지의 alt 등으로 명시 필요 |
|  |  | _parent | 바로 밖 부모 페이지에서 열기 (`iframe` 사용시) |
|  |  | _top | 최상위 페이지에서 열기 (`iframe` 사용시) |
| iframe | src | `{URL}` | 페이지 안에 다른 페이지 집어 넣기. 유튜브 영상 및 구글 지도 삽입 시 사용.  |
| address |  |  | 주소 표현 시, a 태그와 함께 사용 |

```html
<!-- 텍스트 링크 -->
<a href="https://www.koreanair.com/" target="_blank">
	대한항공 홈페이지
</a>

<!-- 이미지 링크 -->
<a href="https://www.koreanair.com/" target="_blank"> 
	<img
		src="../image/Korean Air Logo.jpeg"
		alt="Korean Air"
	>
</a>

<!-- 타깃으로 이동 -->
<a href="#target_8">타깃으로 이동</a>
<p id="target_1">id:target_1</p>
<p id="target_2">id:target_2</p>
<p id="target_3">id:target_3</p>
<p id="target_4">id:target_4</p>
<p id="target_5">id:target_5</p>
<p id="target_6">id:target_6</p>
<p id="target_7">id:target_7</p>
<p id="target_8">id:target_8</p>

<!-- 주소 -->
<address>
  웹사이트 주소: <a href="https://www.koreanair.com/">koreanair.com</a> <br>
  오피스: 서울특별시 강서구 하늘길 260(공항동) <br>
  전화 <a href="tel:010-1234-5678">010-1234-5678</a> <br>
  이메일: <a href="mailto:yekim.ux@gmail.com">yekim.ux@gmail.com</a>
</address>
```

### Input 요소

input은 사용자가 값을 직접 입력하거나 선택할 수 있도록 하는 폼 요소로, 폼 제출 시 서버로 전달할 데이터를 생성하는 역할을 합니다.

| Element | Attribute | Attribute value | Description |
| --- | --- | --- | --- |
| form |  |  | 입력값을 서버로 묶어서 보내는 툴 |
|  | action | `{URL}` | 어디로 보낼지 |
|  | method | get | 어떻게 보낼지 (조회 및 검색 등) |
|  |  | post | 어떻게 보낼지 (변경, 등록, 로그인 등) |
| label  | for ⭐ | `{글자}` | `input` 요소의 라벨. `label for` 과 `input id`와 연결로 input의 클릭 영역 확장 |
| input  | id ⭐ | `{글자}` | 입력창. 브라우저가 읽는 이름, HTML 안에서 특정할 수 있는 고유 이름. CSS & JS 처리 시 필요. `label for`과 연결할 때 사용 (브라우저 문서 기준) |
|  | name | `{글자}` | 서버가 읽는 데이터의 이름 (서버 데이터 단위 기준) |
|  | value | `{글자}` | 서버에 전송되는 실제 데이터 값  |
|  | type ⭐⭐ (텍스트) | text | 일반 텍스트 입력, 기본 입력 필드. 한 줄 텍스트 |
|  |  | password | 비밀번호 입력, 입력값을 •••로 마스킹 |
|  |  | search | 검색창, 브라우저 기본 clear 버튼 제공 |
|  |  | email | 이메일 형식 입력, 모바일에서 @ 키패드 노출 (이메일 형식 자동 검증) |
|  |  | tel | 전화번호 입력, 숫자 키패드 노출 (형식 검증 없음) |
|  |  | url | URL 형식 입력 (URL 형식 자동 검증) |
|  | (숫자·범위) | number | 숫자만 입력, 숫자 화살표(↑↓) 제공, min/max/step 지원 |
|  |  | range | 슬라이더 형태, 시각적으로 범위 선택, 값은 JS로 읽음 |
|  | (날짜·시간) | date | 날짜 형식, 캘린더 UI 제공 |
|  |  | time | 시간, 시간 선택 UI |
|  |  | datetime-local | 날짜 + 시간, 지역 기준 Datetime 선택 |
|  |  | month | 월 선택, "2025-12" 형태 |
|  |  | week | 주 단위 선택, "2025-W48" 형태 |
|  | (선택) | checkbox | 다중 선택, 여러 값 선택 가능 |
|  |  | radio | 단일 선택, 같은 name 그룹 안에서 하나만 선택 |
|  | (파일) | file | 파일 첨부, `accept`로 파일 타입 제한 가능 (ex. 이미지만) |
|  |  | accept | 받아들일 수 있는 파일 형식 |
|  | (버튼) | button | 기본 버튼, 클릭 기능만, 동작은 JS로 정의 |
|  |  | submit | 폼 제출, form action으로 전송 |
|  |  | reset | 입력 초기화, form 내 모든 필드 리셋 |
|  |  | image | 이미지 submit 버튼, `<input type="image" src="...">` 형태로 버튼 역할 |
|  | (UX 강화용) | color | 컬러 피커, 색상 선택 UI 제공 |
|  |  | hidden | 화면에 표시되지 않음, 데이터를 숨겨서 전송할 때 |
|  | placeholder | `{글자}` | 빈 칸에 보이는 안내문 |
|  | readonly |  | 입력창이 읽기만 가능하고 사용자 편집은 불가하지만, 폼 전송은 가능한 상태 |
|  | autofocus |  | 페이지 로드 시 해당 input에 자동으로 포커스(커서)가 이동 |
|  | required |  | 필드 미입력 시, 폼 제출이 차단되는 필수 입력 필드 |
|  | disabled |  | input이 완전히 비활성화되며 클릭/포커스/수정 모두 불가, 폼 전송도 제외 |
|  | checked |  | `checkbox` 및 `radio`에서 사전 선택을 정의 |
|  | maxlength | `{정수}` | 최대 길이 |
|  | minlength | `{정수}` | 최소 길이. 위반 시 submit 거부 |
| button | type | button | 기본 동작 없는 버튼 |
|  |  | reset | 초기화 |
|  |  | submit | 제출  |
| fieldset |  |  | form 태그 내 여러 입력요소와 label의 그룹화. CSS로 수정 가능 |
| legend |  |  | 필드셋 요소의 제목 또는 설명 |

```html
<!-- form: 입력값을 하나로 묶어서 서버(URL)로 보냄 -->
<form 
  action="/signup"
  method="post"
  autocomplete="off"
>

  <!-- fieldset: 관련 입력 요소들을 그룹화 -->
  <fieldset>
    <!-- legend: 그룹 제목 -->
    <legend>회원 가입</legend>

    <!-- label: 클릭 영역 확대용. for = input의 id와 반드시 매칭 -->
    <label for="username">아이디</label>
    <input
      id="username"        
      type="text"
      name="username"
      placeholder="아이디를 입력하세요"
      maxlength="20"
      required
    >

    <label for="password">비밀번호</label>
    <input
      id="password"
      type="password"
      name="password"
      minlength="8"
      required
    >

    <label for="email">이메일</label>
    <input
      id="email"
      type="email"
      name="email"
      placeholder="example@email.com"
      required
    >

    <!-- 전화번호 -->
    <label for="tel">연락처</label>
    <input
      id="tel"
      type="tel"
      name="phone"
      placeholder="010-1234-5678"
    >
  </fieldset>

  <!-- 분리된 새로운 그룹 -->
  <fieldset>
    <legend>여정 선택</legend>

    <!-- radio: 단일 선택, name으로 그룹 형성 -->
    <input
      id="oneway"
      type="radio"
      name="itinerary"
      value="oneway"
      checked
    >
    <label for="oneway">편도(one way)</label>

    <input
      id="round"
      type="radio"
      name="itinerary"
      value="round"
    >
    <label for="round">왕복(round trip)</label>
  </fieldset>

  <fieldset>
    <legend>추가 옵션</legend>

    <!-- checkbox: 다중 선택 -->
    <input
      id="agree"
      type="checkbox"
      name="terms"
      value="agree"
      required
    >
    <label for="agree">약관에 동의합니다</label>

    <!-- file: 파일 업로드 -->
    <label for="profile">프로필 이미지</label>
    <input
      id="profile"
      type="file"
      name="profileImage"
      accept="image/*"
    >

    <!-- 날씨 선호 예시: UX 강화를 위해 color 사용 -->
    <label for="favcolor">선호 색상</label>
    <input
      id="favcolor"
      type="color"
      name="favoriteColor"
      value="#005CE6"
    >
  </fieldset>

  <fieldset disabled>
    <legend>비활성화 영역</legend>
    <!-- fieldset에 disabled → 내부 전체 비활성화 -->
    <label for="disabledInput">사용 불가 입력</label>
    <input
      id="disabledInput"
      type="text"
      value="disabled"
    >
  </fieldset>

  <!-- 버튼 영역 -->
  <button type="reset">초기화</button>
  <button type="submit">가입하기</button>
</form>

```

### 그 외 form 요소

일반 웹 페이지에서는 input/textarea/select는 form 안에 넣어야 합니다. 단, React 같은 SPA 코드에서는 form 없이도 API 호출로 처리 가능합니다.

**textarea**

여러 줄의 텍스트를 입력받을 때 사용하는 폼 요소입니다. 댓글, 설명, 메모 입력 등에 사용됩니다. CSS로 크기를 조절하는 경우 cols/rows는 무시되어도 상관 없습니다.

| Element | Attribute | Attribute value | Description |
| --- | --- | --- | --- |
| textarea | id | `{글자}` | 요소 식별자(ID). label과 연결하거나 JS/CSS에서 사용 |
|  | name | `{글자}`  | 서버로 보낼 데이터의 key (필수) |
|  | cols | `{숫자}` | 가로 글자 수 기준으로 보이는 너비 지정 |
|  | rows | `{숫자}` | 세로 줄 수 기준으로 보이는 높이 지정 |

```html
<form action="/submit" method="post">

  <!-- textarea -->
  <label for="comment">댓글</label>
  <textarea
    id="comment"
    name="comment"
    cols="40"
    rows="4"
  ></textarea>
  
</form>
```

**option**

드롭다운 목록이나 자동완성 리스트를 만들 때 사용하는 요소입니다.

| Element | Attribute | Attribute value | Description |
| --- | --- | --- | --- |
| select | id | `{글자}` | 드롭다운 전체 |
|  | name | `{글자}` |  |
| optgroup | label | `{글자}` | 옵션을 그룹으로 묶는 용도 |
| option | value | `{글자}` | 실제 선택 항목 |
| datalist | id | `{글자}` | `<datalist>` → `<input>`의 자동완성 후보 리스트 제공. `<input list="id">`와 연결하여 자동완성 제공 |

```html
<form action="/submit" method="post">
  
  <!-- select + optgroup + option -->
  <label for="country">국가 선택</label>
  <select id="country" name="country">
    <optgroup label="Asia">
      <option value="kr">South Korea</option>
      <option value="jp">Japan</option>
      <option value="cn">China</option>
    </optgroup>

    <optgroup label="Europe">
      <option value="fr">France</option>
      <option value="uk">United Kingdom</option>
    </optgroup>
  </select>

  <!-- input + datalist (자동완성) -->
  <label for="browser">브라우저 선택</label>
  <input id="browser" name="browser" list="browser-list" />

  <datalist id="browser-list">
    <option value="Chrome"></option>
    <option value="Safari"></option>
    <option value="Firefox"></option>
    <option value="Edge"></option>
  </datalist>
  
</form>
```

**progress & meter**

상태 표시 요소입니다.

| Element | Attribute | Attribute value | Description |
| --- | --- | --- | --- |
| progress | id | `{글자}` | 다운로드, 업로드, 처리 단계 등 정해진 목표를 향해 얼마나 진행됐는지 표시 |
|  | max | `{정수}` | 전체 목표 값 |
|  | value | `{글자}` | 현재 진행도 |
| meter |  | `{정수}` | “좋음/보통/나쁨” 같은 구간 기반의 상태를 표현할 때 사용 (예: 배터리 잔량, 설문점수, 리스크 레벨 등) |
|  | min · max | `{정수}` | 전체 범위 |
|  | optimum | `{정수}` | 가장 이상적인 구간 |
|  | value | `{정수}` | 현재 수치 |
|  | low · high | `{정수}` | 구간 기준 |

```html
<form action="/submit" method="post">
  
  <!-- progress (진행률 표시) -->
  <label for="download">다운로드 진행률</label>
  <progress id="download" value="40" max="100">
    40%
  </progress>

  <!-- meter (값의 수준 표시) -->
  <label for="battery">배터리 잔량</label>
  <meter
    id="battery"
    value="0.4"
    min="0"
    max="1"
    low="0.3"
    high="0.7"
    optimum="0.8"
  ></meter>

  <!-- 제출 버튼 -->
  <button type="submit">제출하기</button>

</form>
```

**👉 input 태그 id & name & value 비교**

id와 name은 목적이 다르므로 동일하게 사용하지 않습니다. 두 값을 분리해 작성하면 UI 로직과 서버 로직 간 의존성을 줄여 유지보수 시 오류를 방지할 수 있습니다.

- id
    - 브라우저가 요소를 식별하기 위한 값입니다.
    - `label`의 `for` 속성과 매칭하거나, CSS · JavaScript에서 요소를 선택할 때 사용합니다.
    - 문서 내에서 고유해야 하며, 화면(UI) 레벨에서의 식별자 역할을 합니다.
    - UI 구조(CSS/JS)에 의해 변경되기 어렵습니다.
- name
    - 폼 데이터를 서버로 전송할 때 사용되는 데이터 키입니다.
    - 서버가 요청 값을 읽을 때 기준이 되는 값으로, 동일한 name을 여러 input에서 공유할 수 있습니다(예: radio 그룹).
    - 서버 데이터 구조나 API 스펙 변경에 따라 수정될 수 있습니다.

| Attribute | For | Where | What | Example |
| --- | --- | --- | --- | --- |
| **id** | 브라우저 UI가 input을 식별하기 위한 값 | label → for, CSS & JS | 화면 구성 요소를 특정하는 고유 ID | `id="onewayOption"` |
| **name** | 서버가 데이터를 받을 때 key | form submit 시 서버 | 서버 데이터 구조/API 명세에 맞춘 필드 키 | `name="itinerary"` |
| **value** | 서버에 전달되는 실제 데이터 | form submit 시 서버 | input이 선택되거나 입력된 값 | `value="oneway"` |

### 빈 태그

| Element | Attribute | Attribute value | Description |
| --- | --- | --- | --- |
| div | class | `{정수}` | block 요소,  한 줄을 전체 차지하는 박스. 레이아웃(구조)를 잡는 용도로 사용 |
| span | class | `{정수}`  | inline 요소, 문장 안에서 특정 텍스트에 스타일을 주고 싶을 때 |

**div & span 비교**

| Element | Display | When | Width Height 적용 | line break |
| --- | --- | --- | --- | --- |
| div | block | 레이아웃 구조,  큰 박스 | 🟢 | 자동 줄바꿈 |
| span | inline | 텍스트 내부의 작고 세밀한 스타일링 | ❌ | 줄 안에서 계속 이어짐 |

```html
<!-- div -->
<div class="card">
  <div class="title">타이틀</div>
  <div class="content">내용</div>
</div>
```

```html
<!-- span -->
<!-- 문장 안에서 특정 텍스트에 스타일을 주고 싶을 때 -->
<p>
  이 문장 안에 <span class="highlight">중요한 부분</span>을 표시합니다.
</p>

<!-- 텍스트 안에서 버튼 처럼 보이게 -->
<span class="tag">New</span>
```

```css
.tag {
  display: inline-block;
  padding: 4px 8px;
  background: #005ce6;
  color: white;
  border-radius: 6px;
}
```
