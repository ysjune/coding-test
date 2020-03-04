### 내 풀이

```java
class Solution {
    public int[] solution(int[] heights) {
        int[] answer = new int[heights.length];
        answer[0] = 0;
        for(int i = 1; i < heights.length; i++) {
            for(int j = i; j >= 0;j--) {
                if(heights[i] < heights[j]) {
                    answer[i] = j+1;
                    break;
                }
            }
        }
        return answer;
    }
}
```

- stack/queue 카테고리지만, 굳이 안써도 풀리기에 그냥 이대로 풀이



### 다른 풀이

```java
import java.util.*;

class Solution {
    class Tower {
        int idx;
        int height;

        public Tower(int idx, int height) {
            this.idx = idx;
            this.height = height;
        }

        @Override
        public String toString() {
            return "idx : " + idx + " height : " + height;
        }
    }

    public int[] solution(int[] heights) {
        Stack<Tower> st = new Stack<>();
        int[] answer = new int[heights.length];

        for (int i = 0; i < heights.length; i++) {
            Tower tower = new Tower(i + 1, heights[i]);
            int receiveIdx = 0;

            while (!st.isEmpty()) {
                Tower top = st.peek();

                if (top.height > tower.height) {
                    receiveIdx = top.idx;
                    break;
                }

                st.pop();
            }

            st.push(tower);
            answer[i] = receiveIdx;
        }

        return answer;
    }
}
```

- stack 을 이용한 풀이 (문제 출제의도에는 이게 더 가깝..)
- Index 와 height 를 가지고 있는 inner class 를 만들어주고, 그걸 스택을 통해 풀이