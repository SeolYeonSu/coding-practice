# 소수 만들기 Lv1

### Summer/Winter Coding(~2018)
### 작성일 : 2023-04-28
***

![Alt text](image/%EC%86%8C%EC%88%98%20%EB%A7%8C%EB%93%A4%EA%B8%B01.jpg)
![Alt text](image/%EC%86%8C%EC%88%98%20%EB%A7%8C%EB%93%A4%EA%B8%B02.jpg)

## 해결 방안 추론      

반복문을 이용해 세 수를 뽑아 소수 여부를 확인하였다.

## 소스 코드
``` java
class Solution {
    public int solution(int[] nums) {
        int answer = 0;
        int sum =0;

        for(int i = 0; i < nums.length; i++) {
            for(int j = i + 1; j < nums.length; j++) {
                for(int k = j+1; k < nums.length; k++) {
                    sum = nums[i] + nums[j] + nums[k];

                    if(isPrime(sum)) {
                        answer++;
                    }
                }
            }
        }
        return answer;
    }
        
    public boolean isPrime(int num){
        for(int i = 2; i < num; i++){
            if(num % i == 0) {
                return false;
            }
        }
        return true;
    }  
}
``` 
