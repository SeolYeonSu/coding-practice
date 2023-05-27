# 캐시 Lv2

### 2018 KAKAO BLIND RECRUITMENT
### 작성일 : 2023-05-27
***

![Alt text](image/%EC%BA%90%EC%8B%9C.jpg)

## 해결 방안 추론      
캐시 교체 알고리즘은 LRU 방식을 사용하므로 별도로 공부하였다.   
[LRU 알고리즘](../study/lru.md)

## 소스 코드
``` java
import java.util.ArrayList;

class Solution {
    public static int solution(int cacheSize, String[] cities) {
        int answer = 0;
        ArrayList<String> list = new ArrayList<String>();

        if (cacheSize == 0)
            return cities.length * 5;

        for (int i = 0; i < cities.length; i++) {
            cities[i] = cities[i].toUpperCase();

            if (list.contains(cities[i])) {
                answer++;
                list.remove(cities[i]);
                list.add(cities[i]);
            } else {
                answer += 5;
                if (list.size() == cacheSize) {
                    list.remove(0);
                    list.add(cities[i]);
                }
                else 
                    list.add(cities[i]);
            }
        }
        return answer;
    }
}
``` 
입출력 예제에 캐시 사이즈 0이 포함되어 있다. 사이즈 0을 처리하는 예외 처리를 추가하였다.