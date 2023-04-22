# 비밀지도 Lv1

###  2018 KAKAO BLIND RECRUITMENT
### 작성일 : 2023-04-22
***

![Alt text](image/%EB%B9%84%EB%B0%80%EC%A7%80%EB%8F%841.jpg)
![Alt text](image/%EB%B9%84%EB%B0%80%EC%A7%80%EB%8F%842.jpg)
![Alt text](image/%EB%B9%84%EB%B0%80%EC%A7%80%EB%8F%843.jpg)
![Alt text](image/%EB%B9%84%EB%B0%80%EC%A7%80%EB%8F%844.jpg)
![Alt text](image/%EB%B9%84%EB%B0%80%EC%A7%80%EB%8F%845.jpg)

## 해결 방안 추론      

주어진 정수를 2진법으로 변환하고 공백과 벽인 부분을 알아내야한다. 이후 두개의 지도를 비교하여 벽이 하나라도 있으면 전체 지도에서 벽이고, 모두 공백인 부분은 전체 지도에서 공백이다.   
먼저 주어진 정수를 **2진법으로 변환**해야한다. 이후 벽이 **하나라도 있다면** 전체 지도에서 벽이라는 조건에 만족하는 **OR 비트연산**을 이용하여 전체 지도를 만들어야한다. 마지막으로 **벽(1)은 #로 공백(0)은 " "으로 치환**하여 반환해야한다.

## 소스 코드
``` java
class Solution {
    public String[] solution(int n, int[] arr1, int[] arr2) {
        String[] answer = new String[n];
        
        for(int i = 0; i < n; i++) {
            answer[i] = String.format("%"+n+"s", Integer.toBinaryString(arr1[i] | arr2[i]).replace("1", "#").replace("0", " "));
        }
        return answer;
    }
}
``` 
*(arr1[i] | arr2[i])* 비트 연산 후 *Integer.toBinaryString()* 를 이용하여 2진법으로 변환하였다. 그 다음 *String.format()* 을 사용하여 앞자리가 0으로 인해 생략된 부분을 자리수에 맞춰 채워주었다. 이후 *replace()* 로 요구사항에 맞게 문자 치환 후 반환하였다.