# 영어 끝말잇기 Lv2

### Summer/Winter Coding(~2018)
### 작성일 : 2023-05-05
***

![Alt text](image/%EC%98%81%EC%96%B4%20%EB%81%9D%EB%A7%90%EC%9E%87%EA%B8%B01.jpg)
![Alt text](image/%EC%98%81%EC%96%B4%20%EB%81%9D%EB%A7%90%EC%9E%87%EA%B8%B02.jpg)

## 해결 방안 추론      

문제 요구사항대로 중복되는 단어가 나오거나 마지막 단어의 끝 글자와 현재 단어의 첫 글자가 일치하지 않을 경우 탈락하게된다.
이전 단어들을 기록하고 중복 여부를 확인 하기 위해 *HashMap* 을 사용하였다. 또한 번호와 차례는 **사람 수(N)** 을 이용하여 구한다.

## 소스 코드
``` java
import java.util.*;

class Solution {
    public int[] solution(int n, String[] words) {
        int[] answer = {0, 0};

		Map<String, Integer> history = new HashMap<>();
		
		for(int i = 0; i < words.length; i++) {
			if(i != 0) {
				if(history.containsKey(words[i]) || words[i-1].charAt(words[i-1].length() - 1) != words[i].charAt(0)) {
					answer[0] = (i % n) + 1;
					answer[1] = (i / n) + 1;
					
					return answer;
				}
			}
			
			history.put(words[i], 1);
		}

        return answer;
    }
}
``` 
맨 처음 단어는 이전 단어 기록이 존재하지 않기 때문에 조건문을 추가하여 확인 과정을 거치지 않는다.

