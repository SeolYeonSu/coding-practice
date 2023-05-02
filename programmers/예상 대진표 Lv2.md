# 예상 대진표 Lv2

### 2017 팁스타운
### 작성일 : 2023-05-02
***

![Alt text](image/%EC%98%88%EC%83%81%20%EB%8C%80%EC%A7%84%ED%91%9C1.jpg)
![Alt text](image/%EC%98%88%EC%83%81%20%EB%8C%80%EC%A7%84%ED%91%9C2.jpg)

## 해결 방안 추론      

라운드 진행 후 다음 라운드 수는 절반으로 줄어든다. 그리고 번호는 줄어든 라운드에 맞게 다시 1번부터 시작한다.   
1번부터 N번까지 +1을 하고 나누기 2를 시도하면 같은 그룹으로 묶이면서 나눠지게 되는데 이는 다음 라운드를 나타낸다. 위 과정을 반복하여 A B 가 같은 값이 나오는 횟수를 구한다.

## 소스 코드
``` java
class Solution {
    public int solution(int n, int a, int b) {
        int answer = 0;
        
        while(a != b) {
            a = (a + 1) / 2;
            b = (b + 1) / 2;
            answer++;
        }

        return answer;
    }
}
``` 



## 리마인드
XOR 연산을 이용한 풀이가 있어 참고용으로 기록한다.
``` java
class Solution {
    public int solution(int n, int a, int b) {
        return Integer.toBinaryString((a-1)^(b-1)).length();
    }
}
```
문자열 길이를 이용하여 라운수 횟수를 도출하였다.