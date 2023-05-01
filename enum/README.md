# Enum 활용
Enum에 대한 개념을 이해하고 활용한다.

### 열거체(enumeration type)

C언어와 C++에서는 열거체를 사용할 수 있지만, JDK 1.5 이전의 자바에서는 열거체를 사용할 수 없었습니다.   
하지만 JDK 1.5부터는 C언어의 열거체보다 더욱 향상된 성능의 열거체를 정의한 Enum 클래스를 사용할 수 있습니다.   
이와 같은 자바의 열거체는 다음과 같은 장점을 가집니다.

1. 열거체를 비교할 때 실제 값뿐만 아니라 타입까지도 체크합니다.

2. 열거체의 상숫값이 재정의되더라도 다시 컴파일할 필요가 없습니다.


### java.lang.Enum 클래스
Enum 클래스는 모든 자바 열거체의 공통된 조상 클래스입니다.   
Enum 클래스에는 열거체를 조작하기 위한 다양한 메소드가 포함되어 있습니다.


### Enum 예시
``` java
public enum Day {
    MON("Monday"),
    TUE("Tuesday"),
    WED("Wednesday"),
    THU("Thursday"),
    FRI("Friday"),
    SAT("Saturday"),
    SUN("Sunday");

    private final String label;

    Day(String label) {
        this.label = label;
    }

    public String getLabel() {
        return label;
    }
}
```

