# 짝지어 제거하기 Lv2

### 2017 팁스타운
### 작성일 : 2023-04-26
***

![Alt text](image/%EC%A7%9D%EC%A7%80%EC%96%B4%20%EC%A0%9C%EA%B1%B0%ED%95%98%EA%B8%B01.jpg)
![Alt text](image/%EC%A7%9D%EC%A7%80%EC%96%B4%20%EC%A0%9C%EA%B1%B0%ED%95%98%EA%B8%B02.jpg)

## 해결 방안 추론      

앞쪽에 같은 문자만 제거하는 방식으로 반복문으로 같은 문자를 찾고 *substring* 을 이용하여 다음 문자열을 만드는 방식을 구상하였다. 이 과정을 재귀함수를 통해 반복하는 것이다.

## 소스 코드
``` java
class Solution {
    int result = -1;
    
    public int solution(String s) {
        int answer = -1;

        removeMatching(s);
        answer = result;

        return answer;
    }
    
    public void removeMatching(String s) {
        boolean isRemove = false;
        
        if("".equals(s)) {
            result = 1;
        }else {
            result = 0;
            for(int i = 0; i < s.length()-1; i++) {
                if(s.charAt(i) == s.charAt(i+1)) {
                    s = s.substring(0, i) + s.substring(i+2, s.length());
                    isRemove = true;
                    break;
                }
            }
            
            if(isRemove) {
                removeMatching(s);
            }
        }
    }
}
``` 
해당 로직은 정답은 도출할 수 있지만 효율성 테스트에서 실패하였다. 재귀 함수 안에 반복문이 있다보니 속도가 느렸다. 문제 접근을 잘못된 방향으로 잡은 것이다. 


## 리마인드
해답을 찾지 못하고 다른 풀이들을 참고하였다. 이번 문제는 스택을 이용하는 문제였고 아래와 같이 소스를 수정하였다.
``` java
import java.util.Stack;

class Solution {
    public int solution(String s) {
        int answer = -1;

        Stack<Character> stack = new Stack<>();
		
		for (int i = 0; i < s.length(); i++) {
			char ch = s.charAt(i);
			
			if(!stack.isEmpty() && stack.peek() == ch) {
                stack.pop();
            }
			else {
                stack.push(ch);
            }
		}

		answer = stack.isEmpty() ? 1 : 0;
        
        return answer;
    }
    
   
}
```
주어준 문자열을 반복문을 통해 스택 최상단의 문자와 동일한 문자일 경우 *pop()* , 아닐경우 *push()* 해준다.