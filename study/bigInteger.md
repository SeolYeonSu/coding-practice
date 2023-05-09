# BigInteger

### BigInteger
변수의 정수 표현 범위를 넘어서게 되면 0이나 의도하지 않은 값이 출력됩니다.BigInteger은 문자열 형태로 이루어져 있어 숫자의 범위가 무한하기에 어떠한 숫자이든지 담을 수 있습니다.

### BigInteger 선언
``` java
import java.math.BigInteger;

BigInteger bigNumber1 = new BigInteger("100000");
BigInteger bigNumber2 = new BigInteger("10000");
```

### BigInteger 사칙연산
``` java
System.out.println("덧셈(+) :" +bigNumber1.add(bigNumber2));
System.out.println("뺄셈(-) :" +bigNumber1.subtract(bigNumber2));
System.out.println("곱셈(*) :" +bigNumber1.multiply(bigNumber2));
System.out.println("나눗셈(/) :" +bigNumber1.divide(bigNumber2));
System.out.println("나머지(%) :" +bigNumber1.remainder(bigNumber2));
```

### BigInteger 형변환
``` java
BigInteger bigNumber = BigInteger.valueOf(100000); //int -> BigIntger

int int_bigNum = bigNumber.intValue(); //BigIntger -> int
long long_bigNum = bigNumber.longValue(); //BigIntger -> long
float float_bigNum = bigNumber.floatValue(); //BigIntger -> float
double double_bigNum = bigNumber.doubleValue(); //BigIntger -> double
String String_bigNum = bigNumber.toString(); //BigIntger -> String
```

### BigInteger 비교
``` java
BigInteger bigNumber1 = new BigInteger("50");
BigInteger bigNumber2 = new BigInteger("1000");
BigInteger bigNumber2_same = new BigInteger("1000");

int compare = bigNumber1.compareTo(bigNumber2);
System.out.println("작은 수를 큰 수랑 비교 할 때 : " + compare); // -1
int compare2 = bigNumber2.compareTo(bigNumber2_same);
System.out.println("2개의 수가 같을 때 : " + compare2); // 0
int compare3 = bigNumber2.compareTo(bigNumber1);
System.out.println("큰 수를 작은 수랑 비교할 때 : " + compare3); // 1 

/*
큰 수를 작은 수랑 비교 할 때 : -1
작은 수를 큰 수랑 비교할 때 : 1
2개의 수가 같을 때 : 0
*/
```