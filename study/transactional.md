# Transactional

## 트랜잭션(Transaction)이란?
모든 작업들이 성공적으로 완료되어야 작업한 결과를 적용하고, 작업 중 오류가 발생했을 때는 이전에 수행된 모든 작업들이 작업 전으로 완전히 되돌리는 것.   

가령 트랜잭션을 적용하면 DB에 데이터 추가, 갱신, 삭제 등으로 이루어진 작업을 처리하던 중 오류가 발생했을 때 모든 작업들은 이전상태로 돌아갑니다. 모든 작업들이 성공해야만 최종적으로 DB에 반영하도록 합니다.

## 트랜잭션의 목적

* 오류로부터 복구를 허용하고 데이터베이스를 일관성있게 유지하는 안정적인 작업 단위를 제공한다.
* 동시 접근하는 여러 프로그램 간 격리를 제공한다.


## ACID
``` 
이론적으로 데이터베이스 시스템은 각각의 트랜잭션에 대해 원자성(Atomicity), 일관성(Consistency), 독립성(Isolation), 영구성(Durability)을 보장한다. 이 성질을 첫글자를 따 ACID라 부른다.
```
* 원자성(Atomicity) :
트랜잭션이 완전히 성공하거나 완전히 실패하는 단일 단위로 처리되도록 보장하는 능력이다. 중간 단계까지 실행되고 실패하는 일이 없도록 하는 것이다.

* 일관성(Consistency): 각 데이터 트랜잭션이 데이터베이스를 일관성 있는 상태에서 일관성 있는 상태로 이동해야 함을 의미한다. 즉 트랜잭션이 성공적으로 완료하면 언제나 동일한 데이터베이스 상태로 유지하는 것을 의미한다.

* 독립성(Isolation): 트랜잭션을 수행 시 다른 트랜잭션의 연산 작업이 끼어들지 못하도록 보장하는 것을 의미한다. 이것은 트랜잭션 밖에 있는 어떤 연산도 중간 단계의 데이터를 볼 수 없음을 의미한다. 여러 트랜잭션이 동시에 발생하는 경우 최종 상태는 트랜잭션이 개별적으로 발생한 것과 같아야 한다. 즉, 데이터베이스는 스트레스 테스트를 통과해야 한다. 즉, 과부하로 인해 잘못된 데이터베이스 트랜잭션이 발생하지 않아야 한다.

* 지속성(Durability) : 성공적으로 수행된 트랜잭션은 영원히 반영(기록)되어야 함을 의미한다. 트랜잭션은 로그에 모든 것이 저장된 후에만 commit 상태로 간주될 수 있다. 데이터베이스 내의 데이터는 트랜잭션의 결과로만 변경되어야 하며 외부 영향에 의해 변경될 수 없어야 한다. 예를 들어 소프트웨어 업데이트로 인해 데이터가 실수로 변경되거나 삭제되지 않아야 한다.


## 선언적 트랜잭션 (@Transactional)
소스코드에 직접 트랜잭션 관련 로직을 넣어두지 않고 비지니스 로직에서 완전히 분리하는 방식입니다.

비즈니스 로직이 트랜잭션 처리를 필요로 할 때, 트랜잭션 처리 코드와 비즈니스 로직이 공존한다면 코드 중복이 발생합니다. 따라서 트랜잭션 처리와 비즈니스 로직을 분리할 수 있는 선언적
트랜잭션 방식을 자주 사용합니다. 트랜잭션이라는 횡단 관심사를 비지니스 로직에서 완전히 분리하기 때문에 많은 양의 트랜잭션 로직을 적용할 수 있습니다.