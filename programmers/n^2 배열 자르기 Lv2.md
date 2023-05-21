# n^2 배열 자르기 Lv2

### 월간 코드 챌린지 시즌3
### 작성일 : 2023-05-21
***

![Alt text](image/n%5E2%20%EB%B0%B0%EC%97%B4%20%EC%9E%90%EB%A5%B4%EA%B8%B0.jpg)

## 해결 방안 추론      
문제 설명대로 2차원 배열을 만드는 방식으로 배열을 만들고 주어진 범위로 잘라낼 경우 데이터가 커지면 오류가 발생한다.   
반대로 주어진 범위에서 배열을 만들어야 한다.    
n X n 배열일 때, ( i / n ) + 1 은 행의 값이 되고 ( i % n ) + 1 은 열의 값이다.   
left와 right사이의 값만 필요로 하므로 i 대신 i + left값을 이용하고 left가 long 타입이기 때문에 계산 결과를 int형으로 변환해준다.   
Max를 이용하여 행열 중 큰 값을 배열에 넣어준다.

## 소스 코드
``` java
import java.util.*;

class Solution {
    public int[] solution(int n, long left, long right) {
        int[] answer = new int[(int)(right - left) + 1];
        
        for(int i = 0; i < answer.length; i++){
            int row = (int)((i + left) / n) + 1;
            int col = (int)((i + left) % n) + 1;
            answer[i] = Math.max(row, col);
        }
        
        return answer;
    }
}
``` 