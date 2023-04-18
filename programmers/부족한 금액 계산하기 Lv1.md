# 부족한 금액 계산하기 Lv1

###  위클리 챌린지
### 작성일 : 2023-04-18
***

![Alt text](image/%EB%B6%80%EC%A1%B1%ED%95%9C%20%EA%B8%88%EC%95%A1%20%EA%B3%84%EC%82%B0%ED%95%98%EA%B8%B01.jpg)
![Alt text](image/%EB%B6%80%EC%A1%B1%ED%95%9C%20%EA%B8%88%EC%95%A1%20%EA%B3%84%EC%82%B0%ED%95%98%EA%B8%B02.jpg)
## 해결 방안 추론      

입출력 예의 설명에 나온 **30 (= 3+6+9+12)** 부분에서 힌트를 얻었다. 
>3+6+9+12 = 3*(1+2+3+4)  

위와 같은 식으로 변경하면 1부터 count까지의 합을 구하고 price를 곱하면 이용 금액을 구할 수 있다. 

## 소스 코드
``` java
class Solution {
    public long solution(int price, int money, int count) {
        long answer = -1; 
        answer = (long)(count * (count+1) / 2) * price - money;
        if(answer < 0) answer = 0;
        return answer;
    }
}
```
1부터 count까지의 숫자들의 합은 *N(N+1)/2* 의 식을 이용하였다.   
금액이 부족하지 않으면 0을 return하기 위해 조건문을 추가하였다. 

## 리마인드
다른 사람 풀이 중 Math.max를 활용한 풀이가 있어 참고용으로 기록한다.
``` java
class Solution {
    public long solution(long price, long money, long count) {
        return Math.max(price * (count * (count + 1) / 2) - money, 0);
    }
}
```
Math.max 는 가장 큰 수를 반환 해주는 함수로 0을 리턴해주기 위해 활용하였다.