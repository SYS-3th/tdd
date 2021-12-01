# TDD
<div style="witdth=200px"><div>

![1_6nwBOHgl1CpsUPr4Ob7-gg](https://user-images.githubusercontent.com/88940298/144003150-91c92d8c-9d27-4dcd-807d-4e2e99bbe69a.png)

 ## TDD가 무엇 일까?
TDD란 Test Driven Development의 약자로 ‘테스트 주도 개발’이라고 한다.

테스트 주도 개발(TDD)은 설계 이후 코드 개발 및 테스트케이스를 작성하는 기존의 개발 프로세스[그림1]와 다르게 테스트케이스를 작성 한 후 실제 코드를 개발하여 리펙토링하는 절차(그림2)를 따른다. 이러한 이유로 TDD를 Test First Development라고도 한다.

 
 ![ka1-748x585](https://user-images.githubusercontent.com/88940298/144003602-9d7a635d-3ce7-453f-b83c-65dc9144057d.png)
TDD는 작가가 책을 쓰는 과정과 유사하다. 책을 쓸 때는 목차를 처음 구성한다. 이후 각 목차에 맞는 내용을 구상하여 초안을 작성하고 고쳐쓰기를 반복한다. 이 과정을 TDD에 비유하면 목차구성은 “테스트코드 작성”, 초안작성은 “코드개발”, 고쳐쓰기는 “코드수정”에 해당한다. 반복적인 검토와 고쳐쓰기를 통해서 좋은 글이 완성되는 것처럼 소프트웨어도 반복적인 테스트와 수정을 통해서 고품질의 소프트웨어를 만들 수 있다.

## TDD를 왜 해야할까
애자일에서 설명한 것과 같이 불확실성이 높을 때 “피드백”과 “협력”이 중요하기 때문에 피드백과 협력이 자주 이루어진다면 더 좋은 결과가 나올 수 있다.

## TDD는 어떤 상황에서 해야할까
만약 어떤 부분에 대한 코딩을 여러번 해봤고 결과가 어떻게 나올지 뻔하다면 TDD를 하지 않아도 된다. 또한 TDD를 했을 때 얻는 것이 적다면 TDD를 하지 않아도 된다. 그렇다면 TDD는 어떤 상황에서 해야할까?

1. 처음해보는 프로그램 주제
-나에 대한 불확실성이 높은 경우
2. 고객의 요구조건이 바뀔 수 있는 프로젝트
- 외부적인 불확실성이 높은 경우
3. 개발하는 중에 코드를 많이 바꿔야 된다고 생각하는 경우
4. 내가 개발하고 나서 이 코드를 누가 유지보수할지 모르는 경우
- 외부적인 불확실성이 즉, 불확실성이 높을 때 TDD를 하면 된다.
- TDD의 효과
모든 애자일의 실천법은 피드백과 협력을 동시에 증진시킨다.
 
 ![ka2](https://user-images.githubusercontent.com/88940298/144003807-d10dd8b6-cb62-492b-8298-b81fc15e98db.png)

 
 1. 피드백 – TDD를 하면 피드백이 증가한다. 테스트 코드를 통해서 Green인지 Red인지 자주 확인할 수 있다.
2. 협력(핵심)

## test의 명사화
test는 보통 동사이다.”테스트한다.”, “테스트해라.” 예를들어, 위의 생년월일 테스트 코드를 테스트 하라고 한다면 숫자를 여러개 찍어보는 작업을 할 것이다.
그러나 TDD를 하면 “test”는 명사가 된다. 동사는 그 순간에만 하는 것이고, 명사(대상,목적어)는 이후에도 소유할 수가 있다 그렇게 되면 남들에게 테스트 코드를 보여줄 수 있고, 남들은 그 코드를 직접 실행해볼 수 있다.

##  그렇다면 TDD는 왜 협력을 증진시킬까?
“test”가 명사가 된다면 공유가 쉬워진다. 다른 사람의 코드를 쉽게 접근가능하고, 이해가 빨라진다. 그렇게 되면 다른사람의 코드 의도를 확인할 수 있게 된다.

## TDD의 예제
중간고사 45, 기말고사 25, 과제 30 점수를 합하여 결과를 성적을 내는 예제이다. 성적은 점수의 총합이 90이상이면 A, 80이상 90미만이면 B, 70이상 80미만이면 C, 60이상 70미만이면 D, 60미만이면 F 이다. 사용자는 점수를 입력하고 점수계산을 하여 점수에 맞는 성적이 계산된다.
 
 
 
 
## TDD 개발 방식의 장점

보다 튼튼한 객체 지향적인 코드 생산
- TDD는 코드의 재사용 보장을 명시하므로 TDD를 통한 소프트웨어 개발 시 기능 별 철저한 모듈화가 이뤄진다. 이는 종속성과 의존성이 낮은 모듈로 조합된 소프트웨어 개발을 가능하게 하며 필요에 따라 모듈을 추가하거나 제거해도 소프트웨어 전체 구조에 영향을 미치지 않게 된다.

재설계 시간의 단축
- 테스트 코드를 먼저 작성하기 때문에 개발자가 지금 무엇을 해야하는지 분명히 정의하고 개발을 시작하게 된다. 또한 테스트 시나리오를 작성하면서 다양한 예외사항에 대해 생각해볼 수 있다. 이는 개발 진행 중 소프트웨어의 전반적인 설계가 변경되는 일을 방지할 수 있다.

디버깅 시간의 단축
- 이는 유닛 테스팅을 하는 이점이기도 하다. 예를 들면 사용자의 데이터가 잘못 나온다면 DB의 문제인지, 비즈니스 레이어의 문제인지 UI의 문제인지 실제 모든 레이러들을 전부 디버깅 해야하지만, TDD의 경우 자동화 된 유닛테스팅을 전재하므로 특정 버그를 손 쉽게 찾아낼 수 있다.

테스트 문서의 대체 가능
- 주로 SI 프로젝트 진행 과정에서 어떤 요소들이 테스트 되었는지 테스트 정의서를 만든다. 이것은 단순 통합 테스트 문서에 지나지 않는다. 하지만 TDD를 하게 될 경우 테스팅을 자동화 시킴과 동시에 보다 정확한 테스트 근거를 산출할 수 있다.

추가 구현의 용이함
- 개발이 완료된 소프트웨어에 어떤 기능을 추가할 때 가장 우려되는 점은 해당 기능이 기존 코드에 어떤 영향을 미칠지 알지 못한다는 것이다. 하지만 TDD의 경우 자동화된 유닛 테스팅을 전제하므로 테스트 기간을 획기적으로 단축시킬 수 있다.

## TDD 개발 방식의 단점
가장 큰 단점은 바로 생산성의 저하이다.

- 개발 속도가 느려진다고 생각하는 사람이 많기 때문에 TDD에 대해 반신반의 한다. 왜냐하면 처음부터 2개의 코드를 짜야하고, 중간중간 테스트를 하면서 고쳐나가야 하기 때문이다. TDD 방식의 개발 시간은 일반적인 개발 방식에 비해 대략 10~30% 정도로 늘어난다.
- SI 프로젝트에서는 소프트웨어의 품질보다 납기일 준수가 훨씬 중요하기 때문에 TDD 방식을 잘 사용하지 않는다.
 
 
 
 # [Jest.js](https://github.com/SYS-3th/tdd/blob/c064f289086c3742ab7ca49e777304239ba56950/Jest.md)
