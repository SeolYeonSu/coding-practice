# 숫자 문자열과 영단어 Lv1

### 2021 카카오 채용연계형 인턴십
### 작성일 : 2023-04-24
***

![Alt text](image/%EC%88%AB%EC%9E%90%20%EB%AC%B8%EC%9E%90%EC%97%B4%EA%B3%BC%20%EC%98%81%EB%8B%A8%EC%96%B41.jpg)
![Alt text](image/%EC%88%AB%EC%9E%90%20%EB%AC%B8%EC%9E%90%EC%97%B4%EA%B3%BC%20%EC%98%81%EB%8B%A8%EC%96%B42.jpg)

## 해결 방안 추론      

영단어를 숫자로 변환 해주는 단순 문제이다.
영단어를 배열에 담고 반복문으로 *replace* 를 하면된다.

## 소스 코드
``` java
class Solution {
    public int solution(String s) {
        int answer = 0;
        String[] number = {"zero", "one", "two", "three", "four", "five", "six", "seven", "eight", "nine"};
        
        for(int i = 0; i < 10; i++) {
            s = s.replace(number[i], Integer.toString(i));
        }
        answer = Integer.parseInt(s);
            
        return answer;
    }
}
``` 