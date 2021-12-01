# Jest
![다운로드](https://user-images.githubusercontent.com/88940298/144252665-be14d4f5-597c-43b3-84ef-ed5b3df59f1c.png)



환경설정 및 설치
```
npm I jest —global
```
```
jest -init
```
<img width="500" alt="KakaoTalk_Photo_2021-12-01-22-21-45" src="https://user-images.githubusercontent.com/88940298/144251520-a41e8de3-b0ab-4925-9be4-de06cfbc7f63.png">


```
npm i -—save-dev jest
```
```
npm install @types/jest
```
```
npm run test
```
```
jest —coverage 
```
test폴더 생성 후
파일명.test.js생성
--- 

- describe
describe: 테스트 단위를 묶는 가장 큰 단위이다. 테스트 시 describe에 설명된 내용으로 테스트 단위를 크게 분류 해준다.

-  test, it
test(), it()을 통해 기본 테스트를 한다.

test와 it의 기능적 차이는 없지만 it의 경우 다른 테스트 프레임워크에서 많이 사용하기 때문에 넣었다고 한다.

-  expect
expect()안에 테스트할 변수나 값을 넣는다. 이후 toBe나 toEqual을 이용해 예측 값과 비교한다.

-  toBe, toEqual
결과 예측으로 가장 많이 쓰는 문법은 toBe와 toEqual이다.

toBe는 단순 비교, toEqual은 배열이나 객체 내부까지 깊은 비교를 해준다.

-  beforeEach, afterEach
```
let temp;
describe("simple test", () => {
  beforeEach(() => {
    temp = 1;
  });
  
  afterEach(() => {
    temp = 0;
  });
  
  test('tmep is 1', () => {
    expect(temp).toBe(1); // true
  });
  
  test('temp is 1', () => {
    expect(temp).toBe(1); // true
  });
});
```
beforeEach는 test()가 실행할 때마다 실행해주는 전처리기이다.

afterEach의 경우 test()가 종료될 때마다 실행하는 후처리기이다.

따라서 위 예시에서 몇번의 테스트를 하더라도 temp는 1이 된다.

---   


afterAll(fn, timeout)
afterEach(fn, timeout)
beforeAll(fn, timeout)
beforeEach(fn, timeout)
테스팅 실행을 처음,마지막,전부 등등 실행후 실행전 뭘할건지

---  
### 사용예시

```
const Calculator = require("../calculator.js");

describe("Calculator", () => {
   /*
  const cal = new Calculator();
  이렇게 공통 값을 만들면 독립적으로 동작이 안되기 때문에
  공통적으로 하는 것은 beforeEach 사용
  */
   let cal;
   beforeEach(() => {
      cal = new Calculator();
   });
   it("init with 0", () => {
      expect(cal.value).toBe(0);
   });
   it("multiply", () => {
      cal.set(3);
      cal.multiply(2);
      expect(cal.value).toBe(6);
   });

   describe("divides", () => {
      it("0/0 === NaN", () => {
         cal.divide(0);
         expect(cal.value).toBe(NaN);
      });
      it("1/0 === Infinity", () => {
         cal.set(1);
         cal.divide(0);
         expect(cal.value).toBe(Infinity);
      });
      it("4/2 === 2", () => {
         cal.set(4);
         cal.divide(2);
         expect(cal.value).toBe(2);
      });
   });
});
```





