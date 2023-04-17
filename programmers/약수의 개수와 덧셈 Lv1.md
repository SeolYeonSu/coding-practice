# 약수의 개수와 덧셈 Lv1

###  월간 코드 챌린지 시즌2
### 작성일 : 2023-04-17
***

![Alt text](image/%EC%95%BD%EC%88%98%EC%9D%98%20%EA%B0%9C%EC%88%98%EC%99%80%20%EB%8D%A7%EC%85%881.jpg)
![Alt text](image/%EC%95%BD%EC%88%98%EC%9D%98%20%EA%B0%9C%EC%88%98%EC%99%80%20%EB%8D%A7%EC%85%882.jpg)

## 해결 방안 추론      

약수의 개수가 짝수인지 홀수 인지에 따라 덧셈, 뺄셈이 정해지므로 우선 약수의 개수를 구하는 방법을 생각하였다.   
하지만 수 하니씩 약수의 개수를 구하는것은 오래 걸릴 것으로 생각되어 다른 방법을 생각하였다.    
예시의 특징을 살펴보니 약수의 개수가 홀수이면 해당 수는 완전제곱수이다.   


>수학에서 정사각수(正四角數, 영어: square number) 또는 제곱수(-數) 또는 완전제곱수(完全-數, 영어: perfect square number)는 어떤 자연수의 제곱이 되는 수이다. - 출처 : wikipedia   

   
완전제곱수 여부를 판별하여 짝수, 홀수를 구분할 수 있으니 해당 조건문을 작성하였다.

## 소스 코드
``` java
class Solution {
    public int solution(int left, int right) {
        int answer = 0;
        double k = 0;
        
        for(int i = left; i <= right; i++) {
            k = Math.sqrt(i);
            if (Math.ceil(k) == Math.floor(k)) {
                answer -= i;
            }else {
                answer += i;
            }
        }
        return answer;
    }
}
```
우선 제곱근을 구한 후 올림, 내림한 값이 같으면 완전제곱수로 판단하였다.   

## 리마인드
올림, 내림 함수를 사용하는 조건문을 좀더 간결하게 수정하고 싶었다.   
제곱수로 나누어 떨어지면 약수이므로 아래와 같이 수정하였다.
``` java
class Solution {
    public int solution(int left, int right) {
        int answer = 0;
        
        for(int i = left; i <= right; i++) {
            if (i % Math.sqrt(i) == 0) {
                answer -= i;
            }else {
                answer += i;
            }
        }
        return answer;
    }
}
```
불필요한 변수 선언을 제거하고 조건문을 간결하게 수정하였다.