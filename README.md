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