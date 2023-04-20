# 예산 Lv1

###  Summer/Winter Coding(~2018)
### 작성일 : 2023-04-20
***

![Alt text](image/%EC%98%88%EC%82%B01.jpg)
![Alt text](image/%EC%98%88%EC%82%B02.jpg)

## 해결 방안 추론      

문제에서 요구하는 것은 한정된 예산으로 지원 가능한 부서의 최대 수를 구하는 것이다. 따라서 가장 작은 수(금액)를 순차적으로 합하여 예산을 넘지 않는 부서 수를 구하면 된다.


## 소스 코드
``` java
import java.util.Arrays;

class Solution {
    public int solution(int[] d, int budget) {
        int answer = 0;
        int sum = 0;
        
        Arrays.sort(d);
        
        for(int i = 0; i < d.length; i++) {
            sum += d[i];
            if(sum <= budget) {
                answer = i+1;
            }else {
                break;
            }
        }
        
        return answer;
    }
}
```
sort를 이용하여 오름차순 정렬 후 반복문을 이용하여 부서의 개수를 구하였다.
