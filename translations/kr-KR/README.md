# 일관성있는 CSS다운 CSS를 작성하기 위한 원칙

이하 문서는 CSS개발을 위한 합리적인 스타일가이드의 중요한 내용입니다.
규범이 될만한 것이라 하긴 좀 그렇고 스스로 스타일 작업시 즐겨쓰는 방식을 다른분들께 꼭 이렇게 해야 한다고 말하려는 의도는 전혀 없습니다. 단, 이런 가이드라인은 현존하는 일반적이며 분별력있는 페턴을 이용하는 것을 추천합니다. 

이 문서는 계속 변경해 나갈 예정이므로 새로운 아이디어를 계속해서 추가해 나갈 생각입니다. 많은 아이디어들을 주시면 고맙겠습니다.

[일관성있는 CSS다운 CSS를 작성하기 위한 원칙](https://github.com/necolas/idiomatic-css/)

## 목차

1. [일반원칙](#general-principles)
2. [화이트스페이스(여백)](#whitespace)
3. [커맨트(주석)](#comments)
4. [포멧](#format)
5. [명명규칙](#naming)
6. [실례](#example)
7. [편성](#organization)
8. [빌드와 디플로이](#build-and-deployment)

[감사의 말](#acknowledgements)


<a name="general-principles"></a>
## 1. 일반규칙

> "성공을 거둔 프로젝트를 잘 관리하는 한 방법은 스스로 코드를 작성하여 실행해 보는것이다.
>  라고 말하는건 아니다. 혹시 많은 사람들이 당신의 코드를 이용하고 있다면, 사양은
> 당신의 취향이 아닌, 최대한 명확한 코드를 사용해야 한다." - Idan Gazit

* 아무리 많은 사람들이 참여했다고 하더라도, 코드는 한사람이 작성한 것처럼 보여야 한다.
* 동의하에 스타일을 엄격하게 지킨다.
* 혹시 고민하게 될 경우에는 현존하는 공통의 페턴을 이용한다.


<a name="whitespace"></a>
## 2. 화이트스페이스(여백)

프로젝트의 모든 소스코드에 한개의 스타일만을 사용할것. 화이트스페이스(여백)은 늘 일관성을 갖어야 한다. 그리고 화이트스페이스(여백)을 가독성을 향상시키기 위해서 이용해야 한다.

* 들여쓰기는 텝, 스페이스를 **절대로** 섞어서 사용해서는 안된다.
* 들여쓰기는 스페이스로 할지 아니면 텝으로 할지를 결정하고, 도중에 변경해서는 안된다.(스페이스 선호)
* 만약 스페이스를 이용하는 경우에 들여쓰기에 이용하는 문자수를 결정할 것.(4 스페이스 선호)

힌트: 이용하고 있는 에디터에 숨김문자표시기능을 활성화 해두자. 이걸로 행의 마지막에 스페이스를 삭제한다던가 불필요한 공백을 삭제하여 불필요한 커밋을 피할 수 있다.


<a name="comments"></a>
## 3. 커맨트(주석)

소스코드에 상세한 주석은 비상시에 중요하다. 컴포넌트가 어떤식으로 동작하는 건지, 어떤 제약이 있는지, 어떤 구성을 갖고 있는지를 설명할 수 있기 때문이다. 팀 내에서 다른 맴버가 일반적이지 않고 명확하지도 않은 코드를 추측하게끔 하는 일은 만들어서는 안된다.

주석의 스타일은 간단하고 소스코드안에서 일관성을 갖고 있을 필요가 있다.

* 주석은 대상이 되는 컴포넌트의 상단에 배치한다.
* 주석은 선언문의 뒤에 추가하지 않도록 한다.
* 행을 구분하는 줄에는 최대문수를 넘지 않도록 한다. 예: 80자
* 주석을 사용해서 CSS 코드를 따로따로 구분하기.
* 주석의 맨 앞자는 대문자로 하고 텍스트의 들여넣기는 일관성을 갖도록 한다.

힌트: 에디터의 설정에 스닙펫기능을 활용해서 정해진 주석페턴을 등록해놓고 사용하도록 한자.

#### CSS의 예:

```css
/* ==========================================================================
   섹션 블럭
   ========================================================================== */

/* 서브 섹션 블럭
   ========================================================================== */

/*
 * 그룹 블럭
 * 여러행을 포함하고 있는 문서나 설명을 적을때 사용한다.
 */

/* 기본 주석 */
```

#### SCSS의 예:

```scss
// ==========================================================================
// 색션 블럭
// ==========================================================================

// 서브 섹션 블럭
// ==========================================================================

//
// 그룹 블럭
// 여러행을 포함하고 있는 문서나 설명을 적을때 사용한다.
//

// 기본 주석
```


<a name="format"></a>
## 4. 포멧

선택한 코드 포멧은 코드가 해독이 쉬운지, 주석이 명확한지, 예상치 못한 에러를 최대한 방지하고 있는지, 그리고 diff,blame과 같은 커멘드의 이점을 잘 활용하는 형태여야 한다. 

1. 복수셀렉터를 갖고있는 룰셋의 경우, 셀러터를 한줄씩 기술할것.
2. 룰셋에서 맨 처음 괄호의 앞에 스페이스 한개를 둘것.
3. 선언 블럭 안에서는 선언을 한줄씩 기술할것.
4. 각 선언에 1레벨의 들여쓰기를 할것.
5. 선언문의 콜론뒤에 스페이스 한개를 둘것.
6. 선언 블럭안의 맨 마지막의 선언문에는 늘 세미콜론을 추가할 것.
7. 룰셋의 닫기괄호는 룰셋안의 첫번째 문자의 위치와 맞춘다.
8. 룰셋은 빈줄로 구분을 짓는다.

```css
.selector-1,
.selector-2,
.selector-3 {
    -webkit-box-sizing: border-box;
    -moz-box-sizing: border-box;
    box-sizing: border-box;
    display: block;
    color: #333;
    background: #fff;
}
```

#### 선언

선언 순서는 단 하나의 원칙에 따라서만 작성할 것. 저와 같은 경우엔 관련하는 프로퍼티끼리 그룹화하였고, 구조적으로 중요한 프로퍼티(예:포지션이나 박스모델)는 타이포그래피, 백그라운드, 컬러의 프로퍼티보다 먼저 선언하도록 하고 있습니다.


```css
.selector {
    position: relative;
    display: block;
    width: 50%;
    height: 100px;
    padding: 10px;
    border: 0;
    margin: 10px;
    color: #fff
    background: #000;
}
```

알파벳순도 자주 사용되고 있지만 결점은 관련하는 프로퍼티끼리 떨어져있다는 점입니다. 예를 들어서 포지션의 옵셋을 그룹화할수가 없고, 박스모델의 프로퍼티는 선언블럭안에서 서로서로 떨어져서 선언 됩니다.

#### 예외와 작은 편차

한줄 선언의 수가 많아지게 되는 경우, 지금까지와는 다른 한줄포멧을 사용할 수 있습니다. 이 경우에는 중괄호 안쪽의 양쪽 끝에 스페이스를 한자 넣는 것입니다.

```css
.selector-1 { width: 10%; }
.selector-2 { width: 20%; }
.selector-3 { width: 30%; }
```

그라데이션이나 쉐도우같이 길고, 컴마로 구분하여 사용하는 프로퍼티값을 갖고있는 경우에는 diff를 좀 더 유용하게 활용하기 위해 여러줄을 사용해도 괜찮습니다. 여러가지의 포맷이 있을 것으로 생각되지만 밑에 적은것과 비슷한 형태일 것입니다.

```css
.selector {
    box-shadow:
        1px 1px 1px #000,
        2px 2px 1px 1px #ccc inset;
    background-image:
        linear-gradient(#fff, #ccc),
        linear-gradient(#f3c, #4ec);
}
```

#### 그 외...

* hex값은 소문자를 이용할 것. 예: `#aaa`
* 싱글따옴표, 더블따옴표에는 일관성을 둘 것. 추천하는 것은 더블따옴표입니다. 예: `content: ""`
* 셀렉터안의 속성치는 늘 따옴표로 감쌀 것. 예: `input[type="checkout"]`
* **가능한 경우**에는 0이 되는 값에는 단위지정을 하지 않는다. 예: `margin: 0`

### 프리프로세서:추가 포멧

CSS프리프로세서의 특성, 기능, 신텍스는 툴에 의해서 전혀 틀립니다. 규칙은 이용하고 있는 프리프로세서의 특성에 맞춰서 확장하세요.
이후의 가이드라인은 SASS를 대상으로 하고 있습니다.

* 코드블럭(nesting)은 한단계만 들여쓰도록 한다. 2단계이상 들어간 중첩요소들이 있는 구조라면 다시한번 코드를 고쳐야 한다. 이렇게 함으로써 CSS셀렉터가 필요이상 상세해 지는걸 막을 수 있다.
* 코드블럭 작성룰은 여러가지를 사용하지 않도록 한다. 읽기 어려워 질것 같다면 나눠서 작성한다. 코드블럭에는 20개 이상의 룰셋을 두지 않도록 한는걸 추천한다.
* `@extend`문은 선언 블럭의 최상단에 기술한다.
* 가능한한 `@include`는 선언블럭안의 `@extend`의 밑에 그룹화 한다.
* 네이티브 CSS함수와 커스텀화한 함수의 차이를 알기 쉽게 하고, 라이브러리에서 함수의 충돌을 피하기 위해 커스텀화한 함수의 접두어로 'x-'를 사용한다던가 아니면 다른 네임스페이스를 지정하여 사용하도록 한다.

```scss
.selector-1 {
    @extend .other-rule;
    @include clearfix();
    @include box-sizing(border-box);
    width: x-grid-unit(1);
    // other declarations
}
```


<a name="naming"></a>
## 5. 명명규칙

우리 인간은 코드컴파일러, 콤프레셔가 아니기 때문에 그렇게 행동할 필요는 없다.

HTML 클래스는 명확하고 심사숙고하여 만든 이름을 사용하여야 한다. HTML화일, CSS화일 안에서 서로가 알기 쉽도록, 일관성있는 명명 페턴을 선택해야 한다.

```css
/* 안좋은 명명규칙의 예 */

.s-scr {
    overflow: auto;
}

.cb {
    background: #000;
}

/* 좀 더 낳은 명명규칙의 예 */

.is-scrollable {
    overflow: auto;
}

.column-body {
    background: #000;
}
```


<a name="example"></a>
## 6. 실례

여러가지 규칙의 예

```css
/* ==========================================================================
   그리드 레이아웃
   ========================================================================== */

/*
 * HTML예:
 *
 * <div class="grid">
 *     <div class="cell cell-5"></div>
 *     <div class="cell cell-5"></div>
 * </div>
 */

.grid {
    overflow: visible;
    height: 100%;
    /* Prevent inline-block cells wrapping */
    white-space: nowrap;
    /* Remove inter-cell whitespace */
    font-size: 0;
}

.cell {
    box-sizing: border-box;
    position: relative;
    overflow: hidden;
    width: 20%;
    height: 100%;
    /* Set the inter-cell spacing */
    padding: 0 10px;
    border: 2px solid #333;
    vertical-align: top;
    /* Reset white-space */
    white-space: normal;
    /* Reset font-size */
    font-size: 16px;
}

/* Cell 상태 */

.cell.is-animating {
    background-color: #fffdec;
}

/* Cell 사이즈
   ========================================================================== */

.cell-1 { width: 10%; }
.cell-2 { width: 20%; }
.cell-3 { width: 30%; }
.cell-4 { width: 40%; }
.cell-5 { width: 50%; }

/* Cell 수식 인자
   ========================================================================== */

.cell--detail,
.cell--important {
    border-width: 4px;
}
```


<a name="organization"></a>
## 7. 편성

소스코드의 편성은 어떤 CSS코드안에서도 중요한 부분이며 또한 거대한 코드베이스의 경우에는 더더욱 중요해진다.

* 소스코드는 논리적으로 확실하게 틀린부분을 이해할 수 있도록 잘 나눠놔야 한다.
* 컴포넌트의 명백함을 강화시키기 위해서 별도의 화일로 만든다.(빌드스텝에서 연결한다.)
* 프리프로세서를 이용하는 경우에는 공통의 코드, 타이포그래피, 색등을 변수로 정의 해둔다.


<a name="build-and-deployment"></a>
## 8. 빌드와 디플로이

프로젝트는 늘 소스코드의 문법체크, 테스트, 압축과 실제 사용에 앞서 버젼관리의 수단들을 갖추어야 합니다.
이런 테스크들은 Ben Alman씨에 의해서 만들어진 [grunt](https://github.com/cowboy/grunt)가 괜찮은 툴입니다.


<a name="acknowledgements"></a>
## 감사의 말

[idiomatic.js](https://github.com/rwldrn/idiomatic.js)에 참여해주신 여러분들께 감사드립니다. idiomatic.js는 기발한 생각이며、인용과 가이드라인의 원본입니다.
