# 없는 숫자 더하기 Lv1

###  월간 코드 챌린지 시즌3
### 작성일 : 2023-04-21
***

![Alt text](image/%EC%97%86%EB%8A%94%20%EC%88%AB%EC%9E%90%20%EB%8D%94%ED%95%98%EA%B8%B01.jpg)
![Alt text](image/%EC%97%86%EB%8A%94%20%EC%88%AB%EC%9E%90%20%EB%8D%94%ED%95%98%EA%B8%B02.jpg)

## 해결 방안 추론      

numbers의 모든 원소는 서로 다르므로 0~9까지 수를 가지고 있는 배열을 선언하였다. 주어진 매개변수에 존재하는 숫자를 0으로 변경한 후 남은 숫자를 모두 합하였다.

## 소스 코드
``` java
import java.util.Arrays;

class Solution {
    public int solution(int[] numbers) {
        int answer = -1;
        int[] answers = {0, 1, 2, 3, 4, 5, 6, 7, 8, 9};
        
        for(int i = 0; i < numbers.length; i++) {
            answers[numbers[i]] = 0;
        }
        
        answer = Arrays.stream(answers).sum();
        return answer;
    }
}
``` 

## 리마인드
없는 숫자를 더하는것은 있는 숫자를 뺀다는 것과 같은 의미이다.   
0~9까지 합은 45이고, 매개변수에 있는 숫자를 빼면 원하는 답을 도출할 수 있다.
``` java
class Solution {
    public int solution(int[] numbers) {
        int answer = 45;
        
        for(int i = 0; i < numbers.length; i++) {
            answer -= numbers[i];
        }

        return answer;
    }
}
```
0~9까지의 값을 담은 배열 선언과 stream으로 합계를 구하는 과정을 생략할 수 있게 되었다.