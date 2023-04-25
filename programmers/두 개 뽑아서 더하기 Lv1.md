# 두 개 뽑아서 더하기 Lv1

### 월간 코드 챌린지 시즌1
### 작성일 : 2023-04-25
***

![Alt text](image/%EB%91%90%20%EA%B0%9C%20%EB%BD%91%EC%95%84%EC%84%9C%20%EB%8D%94%ED%95%98%EA%B8%B01.jpg)
![Alt text](image/%EB%91%90%20%EA%B0%9C%20%EB%BD%91%EC%95%84%EC%84%9C%20%EB%8D%94%ED%95%98%EA%B8%B02.jpg)

## 해결 방안 추론      

우선 두 수의 합을 배열에 저장하기 위해 배열의 크기를 지정해야 했다. **N * (N-1) / 2** 식을 이용하였다. 배열에 두 수의 합을 저장 한 후 중복 제거와 정렬을 한 뒤 결과를 반환하였다. 

## 소스 코드
``` java
import java.util.Arrays;

class Solution {
    public int[] solution(int[] numbers) {
        int len = (numbers.length - 1) * numbers.length / 2;
        int index = 0;
        int[] answer = new int[len];
        
        for(int i = 0; i < numbers.length-1; i++) {
            for(int j = i+1; j < numbers.length; j++) {
                answer[index] = numbers[i] + numbers[j];
                index++;
            }
        }
        
        answer = Arrays.stream(answer).distinct().toArray();
        Arrays.sort(answer);
        
        return answer;
    }
}
``` 
