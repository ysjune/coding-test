### 내 풀이

```java
import java.lang.reflect.Array;
import java.util.*;
import java.util.stream.Collectors;
import java.util.stream.Stream;

class Solution {
    public int solution(String[][] clothes) {

        Map<String, Integer> clothesMap = new HashMap();

        for (int i = 0; i <clothes.length ; i++) {
            clothesMap.put(clothes[i][1], clothesMap.getOrDefault(clothes[i][1], 0)+1);
        }

        int answer = 1;
        for (String key : clothesMap.keySet()) {
            answer *= clothesMap.get(key) + 1;
        }
        return answer-1;
    }
}
```

- 문제 자체를 수학적으로도 풀이 방법을 몰라서 이리저리 헤매다가 결국 구글링을 통해.. `입거나 말거나 와 마지막에는 모두 말거니 이니까 -1을 해줘야 한다` 라는 방법을 듣고 풀이



### 다른 풀이

```java
import java.util.*;
import static java.util.stream.Collectors.*;

class Solution {
    public int solution(String[][] clothes) {
        return Arrays.stream(clothes)
                .collect(groupingBy(p -> p[1], mapping(p -> p[0], counting())))
                .values()
                .stream()
                .collect(reducing(1L, (x, y) -> x * (y + 1))).intValue() - 1;
    }
}
```

- 다른 사람들 풀이 보는데 스트림을 통해 하나로 표현한 것에 감탄