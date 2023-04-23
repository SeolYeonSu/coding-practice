# 이진 변환 반복하기 Lv2

### 월간 코드 챌린지 시즌1
### 작성일 : 2023-04-23
***

![Alt text](image/%EC%9D%B4%EC%A7%84%20%EB%B3%80%ED%99%98%20%EB%B0%98%EB%B3%B5%ED%95%98%EA%B8%B01.jpg)
![Alt text](image/%EC%9D%B4%EC%A7%84%20%EB%B3%80%ED%99%98%20%EB%B0%98%EB%B3%B5%ED%95%98%EA%B8%B02.jpg)

## 해결 방안 추론      

문제 요구사항은 아래와 같이 정리할 수 있다.
1. 주어진 문자열 x에서 0을 제거해야한다. 이때 제거한 0의 개수를 저장한다.
2. 0을 제거한 문자열 x의 길이 c를 2진법으로 변환한다.
3. 2번에 도출된 문자열이 1이 나올 때 까지 반복한다.   

위와같은 과정을 반복하므로 재귀함수를 구현하는것으로 생각하였다.

## 소스 코드
``` java
class Solution {
    private int convCnt = 0;
    private int zeroCnt = 0;
    
    public int[] solution(String s) {
        removeZero(s);
        int[] answer = {convCnt, zeroCnt};
        return answer;
    }
    
    public void removeZero(String s) {
        if(!"1".equals(s)) {
            convCnt++;
            zeroCnt += s.length() - s.replace("0", "").length();
            removeZero(Integer.toString(s.replace("0", "").length(), 2));
        }
    }
}
``` 
변환 횟수와 0의 개수를 반환해주기 위해 멤버 변수를 선언하였다. 재귀 함수를 호출하여 변환 횟수와 0의 개수를 갱신한다.   
0의 개수는 기존 문자열의 길이에서 0을 제거한 문자열의 길이를 빼면 쉽게 구할 수 있다. 이후 문자열에 "1"만 남을 때 까지 반복 호출한다.