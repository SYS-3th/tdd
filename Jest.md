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
진철하게도 Jest는 toBe() 대신에 toEqual() 함수를 사용하라고 가이드해주고 있다.  
실제로 테스트 코드를 작성할 때는 객체를 검증해야할 일이 많기 때문에 toEqual() 함수를 가장 많이 접할 수 있다.

- toBeTruthy(), toBeFalsy()  

toEqual() 함수 다음으로 많이 사용되는 Matcher 함수는 아마도 toBeTruthy() 와 toBeFalsy()일 것입니다. 많은 분들이 아시다시피 느슨한 타입 기반 언어인 자바스크립트는, 자바같은 강한 타입 기반 언어처럼 true와 false가 boolean 타입에 한정되지 않습니다. 따라서 숫자 1이 true로 간주되고, 숫자 0이 false로 간주되는 것과 같이 모든 타입의 값들을 true 아니면 false 간주하는 규칙이 있습니다. toBeTruthy()는 검증 대상이 이 규칙에 따라 true로 간주되면 테스트 통과이고, toBeFalsy()는 반대로 false로 간주되는 경우 테스트가 통과됩니다.
```
test("number 0 is falsy but string 0 is truthy", () => {
  expect(0).toBeFalsy();
  expect("0").toBeTruthy();
});
```

- toHaveLength(), toContain()
배열의 경우에는 배열이 길이를 체크하거나 특정 원소가 존재 여부를 테스트하는 경우가 많습니다. toHaveLength() 배열의 길이를 체크할 때 쓰이고, toContain() 특정 원소가 배열에 들어있는지를 테스트할 때 쓰입니다.
```
test("array", () => {
  const colors = ["Red", "Yellow", "Blue"];
  expect(colors).toHaveLength(3);
  expect(colors).toContain("Yellow");
  expect(colors).not.toContain("Green");
});
```
위 테스트 코드를 주의 깊게 보시면 마지막 줄에 not Matcher가 사용된 것을 알 수 있습니다. 이처럼 어떤 Matcher 함수가 불만족하는지를 테스트할 때는 앞에 not을 붙여주면 됩니다.  
  
- toMatch()

문자열의 경우에는 단순히 toBe()를 사용해서 문자열이 정확히 일치하는지를 체크하지만, 종종 정규식 기반의 테스트가 필요할 떄가 있는데 toMatch() 함수를 사용하면됩니다.
```
test("string", () => {
  expect(getUser(1).email).toBe("user1@test.com");
  expect(getUser(2).email).toMatch(/.*test.com$/);
});
```
- toThrow()

마지막으로 예외 발생 여부를 테스트해야할 때는 toThrow() 함수를 사용하면 됩니다. toThrow() 함수는 인자도 받는데 문자열을 넘기면 예외 메세지를 비교하고 정규식을 넘기면 정규식 체크를 해줍니다.

먼저, 위에서 작성한 getUser() 함수가 음수 아이디가 들어왔을 경우, 예외를 던지도록 수정하겠습니다.

```
function getUser(id) {
  if (id <= 0) throw new Error("Invalid ID");
  return {
    id,
    email: `user${id}@test.com`,
  };
}
```

```
function getUser(id) {
  if (id <= 0) throw new Error("Invalid ID");
  return {
    id,
    email: `user${id}@test.com`,
  };
}
```

```
test("throw when id is non negative", () => {
  expect(getUser(-1)).toThrow();
  expect(getUser(-1)).toThrow("Invalid ID");
});
```
```
$ npm test

> my-jest@1.0.0 test /my-jest
> jest

 FAIL  ./test.js
  ✕ throw when id is non negative (2ms)

  ● throw when id is non negative

    Invalid ID

      1 | function getUser(id) {
    > 2 |   if (id <= 0) throw Error('Invalid ID');
        |                      ^
      3 |   return {
      4 |     id,
      5 |     email: `user${id}@test.com`

      at Error (test.js:2:22)
      at Object.getUser (test.js:10:10)

Test Suites: 1 failed, 1 total
Tests:       1 failed, 1 total
Snapshots:   0 total
Time:        0.928s, estimated 1s
Ran all test suites.
npm ERR! Test failed.  See above for more details.
```
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
toThrow() 함수를 사용할 때 하기 쉬운 실수 인데요. 반드시 expect() 함수에 넘기는 검증 대상을 함수로 한 번 감싸줘야 합니다. 그렇지 않으면 예외 발생 여부를 체크하는 것이 아니라, 테스트 실행 도중 정말 그 예외가 발생하기 때문에 그 테스트는 항상 실패하게 됩니다.

아래와 같이, 예외가 발생할 함수 호출 부분을 함수로 감싸주면,

```
test("throw when id is non negative", () => {
  expect(() => getUser(-1)).toThrow();
  expect(() => getUser(-1)).toThrow("Invalid ID");
});
```
```
$ npm test

> my-jest@1.0.0 test /my-jest
> jest

 PASS  ./test.js
  ✓ throw when id is non negative (2ms)

Test Suites: 1 passed, 1 total
Tests:       1 passed, 1 total
Snapshots:   0 total
Time:        1.449s
Ran all test suites.
```
- beforeEach  
test()가 실행할 때마다 실행해주는 전처리기이다.

- afterEach
test()가 종료될 때마다 실행하는 후처리기이다.

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





