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

describe = 테스팅을 그룹화해서 내부에 세부적인 테스트코드들이있고
describe 그룹끼리 또 테스팅을 연결해서 리액트 컴포넌트 연결하듯이 테스팅가능  

--   

it('테스팅이름', () => {}) = 테스팅 소분화

--   


afterAll(fn, timeout)
afterEach(fn, timeout)
beforeAll(fn, timeout)
beforeEach(fn, timeout)
테스팅 실행을 처음,마지막,전부 등등 실행후 실행전 뭘할건지

--  
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

   it("sets", () => {
      cal.set(9);
      cal.clear();
      expect(cal.value).toBe(0);
   });

   it("add", () => {
      cal.set(1);
      cal.add(2);
      expect(cal.value).toBe(3);
   });

   it("substracts", () => {
      cal.set(3);
      cal.subtract(1);
      expect(cal.value).toBe(2);
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





