# 괄호 회전하기 Lv2

### 월간 코드 챌린지 시즌2
### 작성일 : 2023-05-14
***

![Alt text](image/%EA%B4%84%ED%98%B8%20%ED%9A%8C%EC%A0%84%ED%95%98%EA%B8%B01.jpg)
![Alt text](image/%EA%B4%84%ED%98%B8%20%ED%9A%8C%EC%A0%84%ED%95%98%EA%B8%B02.jpg)

## 해결 방안 추론      

우선 문자열을 왼쪽으로 회전하는 방법을 먼저 구상하였다. *substring* 을 이용하여 앞 부분을 추출하고 뒤에 붙이는 식으로 구현하였다.   
그 다음 올바른 괄호 인지 확인하기 위해 스택을 이용하였다. 닫기 형식 일 때 마지막에 담긴 괄호가 같은 괄호의 열기면 스택에서 빼내고, 아니라면 스택에 넣는다.    
 위 과정을 반복 후 스택에 괄호가 남아 있는지 확인하여 올바른 괄호 여부를 확인한다.

## 소스 코드
``` java
import java.util.Stack;

class Solution {
    public int solution(String s) {
        int answer = 0;
        
        for(int i = 0; i < s.length(); i++){
            StringBuilder sb = new StringBuilder(s);
            String subString = sb.substring(0, i);
            sb.delete(0,i);
            sb.append(subString);
            if(check(sb)) answer++;
        }
        return answer;
    }
    
    private boolean check(StringBuilder s) {
        Stack<Character> stack = new Stack<Character>();
        
        for(int i = 0; i < s.length(); i++) {
            if(stack.empty()) {
                stack.push(s.charAt(i));
            } else {
                switch(s.charAt(i)) {
                    case ')':
                        if(stack.peek() == '(') stack.pop();
                        break;
                    case '}':
                        if(stack.peek() == '{') stack.pop();
                        break;
                    case ']':
                        if(stack.peek() == '[') stack.pop();
                        break;
                    default :
                        stack.push(s.charAt(i));
                        break;
                }
            }         
        }
        
        return stack.empty();
    }
}
``` 
맨 처음에는 스택이 비어있는 상태이므로 첫 문자는 무조건 스택에 담아야한다.
