# Serialization

## 직렬화(Serialization)란?
```
직렬화(直列化) 또는 시리얼라이제이션(serialization)은 컴퓨터 과학의 데이터 스토리지 문맥에서 데이터 구조나 오브젝트 상태를 동일하거나 다른 컴퓨터 환경에 저장(이를테면 파일이나 메모리 버퍼에서, 또는 네트워크 연결 링크 간 전송)하고 나중에 재구성할 수 있는 포맷으로 변환하는 과정이다.

오브젝트를 직렬화하는 과정은 오브젝트를 마샬링한다고도 한다. 반대로, 일련의 바이트로부터 데이터 구조를 추출하는 일은 역직렬화 또는 디시리얼라이제이션(deserialization)이라고 한다.
```

## 직렬화 조건
* 자바 기본(primitive) 타입과 java.io.Serializable 인터페이스를 상속받은 객체는 직렬화 할 수 있는 기본 조건을 가집니다.
``` java
    /**
    * 직렬 화할 회원 클래스
    */
    public class Member implements Serializable {
        private String name;
        private String email;
        private int age;

        public Member(String name, String email, int age) {
            this.name = name;
            this.email = email;
            this.age = age;
        }
    }
```
## 직렬화 방법
* 자바 직렬화는 방법은 java.io.ObjectOutputStream 객체를 이용합니다.

``` java
Member member = new Member("홍길동", "hong@email.com", 30);
    byte[] serializedMember;

    try (ByteArrayOutputStream baos = new ByteArrayOutputStream()) {
        try (ObjectOutputStream oos = new ObjectOutputStream(baos)) {
            oos.writeObject(member);
            // serializedMember -> 직렬화된 member 객체 
            serializedMember = baos.toByteArray();
        }
    }
    // 바이트 배열로 생성된 직렬화 데이터를 base64로 변환
    System.out.println(Base64.getEncoder().encodeToString(serializedMember));
```

## 역직렬화 조건
* 직렬화 대상이 된 객체의 클래스가 클래스 패스에 존재해야 하며 import 되어 있어야 합니다.
* 자바 직렬화 대상 객체는 동일한 serialVersionUID 를 가지고 있어야 합니다

``` java
private static final long serialVersionUID = 1L;
``` 

## 역직렬화 방법

``` java
// 직렬화 예제에서 생성된 base64 데이터 
    String base64Member = "...생략";
    byte[] serializedMember = Base64.getDecoder().decode(base64Member);
    try (ByteArrayInputStream bais = new ByteArrayInputStream(serializedMember)) {
        try (ObjectInputStream ois = new ObjectInputStream(bais)) {
            // 역직렬화된 Member 객체를 읽어온다.
            Object objectMember = ois.readObject();
            Member member = (Member) objectMember;
            System.out.println(member);
        }
    }
``` 

## 직렬화 장점
* 자바 직렬화는 자바 시스템에서 개발에 최적화되어 있습니다.
* 복잡한 데이터 구조의 클래스의 객체라도 직렬화 기본 조건만 지키면 직렬화를 가능합니다. 
* 역직렬화도 동일 합니다.
* 데이터 타입이 자동으로 맞춰집니다.
* 역직렬화가 되면 기존 객체처럼 바로 사용할 수 있게 됩니다.


***
## 참고
[우아한 기술블로그](https://techblog.woowahan.com/2550/)