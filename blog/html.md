# HTML

### 인용문

| **태그** | 속성 | **설명** |
| --- | --- | --- |
| blockquote |  | 비교적 긴 인용문에 사용. cite 속성으로 출처 표시 |
| q |  | 비교적 짧은 인용문에 사용. cite 속성으로 출처 표시 |
|  | cite | 저작물의 출처 표기. 제목을 반드시 포함 |
| mark |  | 인용문 중 하이라이트 또는 사용자 행동과 연관된 곳 표시. CSS와 병행하여 사용 필요 |

```html
<blockquote cite="https://developer.mozilla.org/ko/docs/Web/HTML/Element/blockquote">
	 <p>
	   HTML &lt;blockquote&gt; 요소는 안쪽의 텍스트가 긴 <mark>인용문</mark>임을 나타냅니다.
	 </p>
</blockquote>
  
<p>
  q 태그에 대해 MDN 문서는
  <q cite="https://developer.mozilla.org/ko/docs/Web/HTML/Element/q">
	   HTML &lt;q&gt;요소는 둘러싼 텍스트가 짧은 인라인 <mark>인용문</mark> 이라는것을 나타냅니다.
  </q>
  라고 설명하고 있습니다.
</p>
```

### 목록

| **태그** | 속성 | **설명** |
| --- | --- | --- |
| ul |  | unordered list, 순서가 없는 목록 |
| ol |  | ordered list, 순서가 있는 목록 |
|  | type | 1, I, i, A, a 등 다양한 타입 선택 가능 |
|  | start | 1~ 시작 지점 선택 가능 |
| li |  | list item, 목록 아이템. `ul`, `ol` 태그의 1촌 자식으로 이 태그만 가능 |

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

### 이미지

| **태그** | 속성 | **설명** |
| --- | --- | --- |
| img | src | source, 원본파일 경로. 절대경로 또는 상대경로 |
|  | alt | alternative text, 대체 텍스트. 스크린 리더, 원본파일 무효시 |
|  | title | hover 시 표시. alt의 대체제나 반복이 되어서는 안됨 |
|  | width | 너비. 픽셀 단위의 정수로 표현 |
|  | height | 높이. 픽셀 단위의 정수 |

```html
<img 
	src="./coding.png" 
	alt="코딩중인 노트북" 
	title="프로그래밍"
	wight="600"
	height="400"
>
```

### 표

왼쪽에서 오른쪽으로 ➡️ 위에서 아래로 ⬇️ 표를 채워나간다. 

| 태그 | **속성** | 설명 |
| --- | --- | --- |
| table |  | 표 전체를 감싸는 태그 |
| caption |  | 표의 제목 또는 설명 (선택 사항) |
| thead |  | 헤더 부분으로 각 기둥 제목 |
| tbody |  | 실제 데이터 부분 |
| tfoot |  | 합계, 요약 같은 마지막 부분 |
| tr |  | table row, 가로 한 줄 |
| th | scope | table header, 헤더 셀로 제목 역할. `scope` 속성으로 `row`, `col` 중 선택  |
| td | scope | table data, 일반 데이터 셀 |
|  | colspan | column span, 열 (세로) 병합 |
|  | rowspan | row span, 행 (가로) 병합 |
| colgroup |  | 열 단위로 스타일을 주고 싶을 때 사용. `caption` 보다 뒤, 그 외 요소보다 앞에 와야 함 |
| col | span | column, 각 열 하나. `span` 속성으로 범위 지정 |
|  | class | `class` 속성을 통해 CSS에서 스타일 지정 |

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

### 페이지 이동

| 태그 | 속성 | 속성값 | 설명 |
| --- | --- | --- | --- |
| a | href | URL | anchor, **h**ypertext **ref**erence, 페이지 이동이 필요한 주소 및 `#{...}` |
|  | target | _self | 링크를 열 옵션 선택. 현재 창에서 페이지 이동 (기본) |
|  |  | _blank | 새 창 열림. 텍스트나 내부 이미지의 alt 등으로 명시 필요 |
|  |  | _parent | 바로 밖 부모 페이지에서 열기 (`iframe` 사용시) |
|  |  | _top | 최상위 페이지에서 열기 (`iframe` 사용시) |
| iframe | src | URL | 페이지 안에 다른 페이지 집어 넣기. 유튜브 영상 및 구글 지도 삽입 시 사용.  |
| address |  |  | 주소(`mailto:`) 및 연락처(`tel:`) 정보를 포함. a 태그와 함께 사용 가능 |

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
