### 내 풀이

 ```java
import java.util.*;

class Solution {
    public int[] solution(int[] array, int[][] commands) {
        List<Integer> list = new ArrayList();
        for (int i = 0; i < commands.length; i++) {
            int i1 = commands[i][0]-1;
            int i2 = commands[i][1];
            int i3 = commands[i][2]-1;

            int[] ints = Arrays.copyOfRange(array, i1, i2);
            Arrays.sort(ints);
            list.add(ints[i3]);
        }
        return list.stream().mapToInt(i->i).toArray();
    }
}
 ```

- answer = {} 이런식으로 나왔었는데, 평소에 콜렉션만 쓰니까 문제 다 풀어놓고 콜렉션을 배열로 바꾸는 방법을 몰라서 검색...
- 평소에 IDEA 에서 컨트롤 스페이스(자동완성) 해놓고 무슨 메소드 있나 보는 습관이 있는데, 이번엔 그게 도움이 되었다.



### 다른 풀이

```java
import java.util.Arrays;
class Solution {
    public int[] solution(int[] array, int[][] commands) {
        int[] answer = new int[commands.length];

        for(int i=0; i<commands.length; i++){
            int[] temp = Arrays.copyOfRange(array, commands[i][0]-1, commands[i][1]);
            Arrays.sort(temp);
            answer[i] = temp[commands[i][2]-1];
        }

        return answer;
    }
}
```

- 주요 로직은 비슷. 배열 초기화는 저렇게..