### ch7 타입 별칭

#### type alias와 인터페이스의 차이

- 인터페이스는 객체 타입 정의, type alias는 일반 타입 이름이나 유니언타입, 인터섹션 타입에 사용
- 인터페이스는 타입 확정시 상속 extends 키워드 사용, 타입 별칭은 인터섹션 타입(A & B)으로 객체 타입을 여러개 합쳐서 사용
- 인터페이스의 경우 여러번 선언했을 때 해당 인터페이스의 타입내용을 합치는 선언 병합(declaration merging)이 이루어짐

### ch9 클래스

#### 클래스 접근 제어자

- private 실행 결과까지 클래스 접근 제어자와 일치시키고 싶다면 '#'을 사용

```
class WaterPurifier {
    #waterAmount:number;

    constructor(amount: number) {
        this.#waterAmount = amount;
    }

    public wash() {
        if (this.#waterAmount > 0)
            console.log('정수기 동작 성공')
    }
}

var purifier = new WaterPurifier(500);
purifier.wash()
purifier.#waterAmount = 0;
purifier.wash()
```

### ch13 타입 단언

- as 키워드와 null 아님 보장 연산자(!)를 사용해서 타입 단언 가능
- 타입 단언(type assertion)은 타입 에러는 해결할 수 있지만 실제 실행 시점의 에러는 해결하지 못함.

### ch14 타입 가드
특정 위치에서 타입 여러개 중 하나로 걸러내는 역할을 함.

- typeof, instanceof, in 연산자(객체) 등을 사용해서 타입 구분
- 타입 가드 함수는 타입 가드 역할을 하는 함수로 주로 객체 유니언 타입 중 하나를 구분하는 데 사용됨

### ch15 타입 호환
- 구조적 타이핑(structural typing): 타입 구조로 호환여부를 판별함
- enum 타입의 호환:같은 속성과 값을 가졌어도 타입 간 서로 호환되지 x
- 제네릭 타입의 호환: 제네릭으로 받은 타입이 해당 타입 구조에서 사용되지 않는다면 타입 호환에 영향 x
  ex1) 타입 사용 x
  ```
  interface Empty<T> {
  }
  let Empty1:Empty<string>;
  let Empty2:Empty<number>;
  Empty2 = Empty1;
  Empty1 = Empty2;
  ```
  ex2) 타입 사용
  ```
  interface NotEmpty<T> {
    data: T;
  }
  let notEmpty1:notEmpty1<string>;
  let notEmpty2:notEmpty1<number>;
  notEmpty2 = notEmpty1; // 에러발생
  notEmpty1 = notEmpty2; // 에러발생
  ```

### ch17 유틸리티 타입
