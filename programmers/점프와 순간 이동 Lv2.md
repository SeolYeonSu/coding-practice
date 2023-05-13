# 점프와 순간 이동 Lv2

### Summer/Winter Coding(~2018)
### 작성일 : 2023-05-13
***

![Alt text](image/%EC%A0%90%ED%94%84%EC%99%80%20%EC%88%9C%EA%B0%84%20%EC%9D%B4%EB%8F%991.jpg)
![Alt text](image/%EC%A0%90%ED%94%84%EC%99%80%20%EC%88%9C%EA%B0%84%20%EC%9D%B4%EB%8F%992.jpg)

## 해결 방안 추론      

앞으로 K칸을 점프하는 만큼 건전지를 사용하고 순간이동(현재까지 온 거리 x 2)은 건전지를 사용하지 않으므로 목표 거리까지 순간이동(N/2)를 반복하면서 N이 홀수 일 경우 점프(N-1)를 하면 된다.

## 소스 코드
``` java
import java.util.*;

public class Solution {
    public int solution(int n) {
        int ans = 0;
        
        while(n != 0) {
            if(n % 2 == 0) {
                n /= 2;
            } else {
                n -= 1;
                ans++;
            }
        }
    
        return ans;

    }
}
``` 
