# Builder

### 빌더 패턴(Builder pattern)이란?
``` 
생성과 관련된 디자인 패턴으로, 동일한 프로세스를 거쳐 다양한 구성의 인스턴스를 만드는 방법
``` 

GoF 디자인 패턴 중 생성 패턴에 해당합니다.
빌더 패턴은 복잡한 객체를 생성하는 클래스와 표현하는 클래스를 분리하여, 동일한 절차에서도 서로 다른 표현을 생성하는 방법을 제공합니다.

### 빌더를 써야하는 이유
1. 유연성을 확보하고 가독성을 높일 수 있음
2. 어떤 값을 먼저 설정하던 상관 없으며 필요한 데이터만 설정할 수 있음
3. 불변성을 확보할 수 있음

### @Builder 사용 예시
``` java
@Builder
public class TestDTO {
    private final String name;
    private final int age;
    private final String phone;
    private final String email;
}
```

``` java
TestDTO test = TestDTO.builder()
			.name("홍길동")
			.age(45)
			.phone("010-1234-5678")
			.email("hong@email.com").build();
```

### @Builder javadoc
``` java
// Before:
   @Builder
   class Example<T> {
   	private T foo;
   	private final String bar;
   }
   
// After:
   class Example<T> {
   	private T foo;
   	private final String bar;
   	
   	private Example(T foo, String bar) {
   		this.foo = foo;
   		this.bar = bar;
   	}
   	
   	public static <T> ExampleBuilder<T> builder() {
   		return new ExampleBuilder<T>();
   	}
   	
   	public static class ExampleBuilder<T> {
   		private T foo;
   		private String bar;
   		
   		private ExampleBuilder() {}
   		
   		public ExampleBuilder foo(T foo) {
   			this.foo = foo;
   			return this;
   		}
   		
   		public ExampleBuilder bar(String bar) {
   			this.bar = bar;
   			return this;
   		}
   		
   		@java.lang.Override public String toString() {
   			return "ExampleBuilder(foo = " + foo + ", bar = " + bar + ")";
   		}
   		
   		public Example build() {
   			return new Example(foo, bar);
   		}
   	}
   }
```
