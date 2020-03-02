### 내 풀이

```java
import java.util.*;

class Solution {
    public int[] solution(int[] answers) {

        List<Integer> supo1 = Arrays.asList(1, 2, 3, 4, 5);
        List<Integer> supo2 = Arrays.asList(2, 1, 2, 3, 2, 4, 2, 5);
        List<Integer> supo3 = Arrays.asList(3, 3, 1, 1, 2, 2, 4, 4, 5, 5);
        int count1 = 0;
        int count2 = 0;
        int count3 = 0;
        int supo1Size = supo1.size();
        int supo2Size = supo2.size();
        int supo3Size = supo3.size();

        for (int i = 0; i < answers.length; i++) {
            if(answers[i] == supo1.get(i%supo1Size)) {
                count1++;
            }
            if(answers[i] == supo2.get(i%supo2Size)) {
                count2++;
            }
            if(answers[i] == supo3.get(i%supo3Size)) {
                count3++;
            }
        }

        int[] temp = {count1, count2, count3};
        int max = Arrays.stream(temp).max().getAsInt();
        List<Integer> list = new ArrayList();
        for (int i = 0; i < temp.length; i++) {
            if(max == temp[i]) { 
                list.add(i+1);
            }
        }
        Collections.sort(list);
        
        return list.stream().mapToInt(i -> i).toArray();
    }
}
```

- For 문까지는 금방 구해놓고, 많이 푼 맞춘 애를 어떻게 골라내지.... 하면서 시간을 많이 까먹었다.
- Arrays 의 메소드와 Stream 을 손에 익히려고 일부러 쓴다. (알고리즘도 중요하지만, 실무에서는 배열보단 람다를 더 많이 쓰는 느낌이라, 익숙해지고자)



### 다른 풀이

```java
import java.util.ArrayList;
class Solution {
    public int[] solution(int[] answer) {
        int[] a = {1, 2, 3, 4, 5};
        int[] b = {2, 1, 2, 3, 2, 4, 2, 5};
        int[] c = {3, 3, 1, 1, 2, 2, 4, 4, 5, 5};
        int[] score = new int[3];
        for(int i=0; i<answer.length; i++) {
            if(answer[i] == a[i%a.length]) {score[0]++;}
            if(answer[i] == b[i%b.length]) {score[1]++;}
            if(answer[i] == c[i%c.length]) {score[2]++;}
        }
        int maxScore = Math.max(score[0], Math.max(score[1], score[2]));
        ArrayList<Integer> list = new ArrayList<>();
        if(maxScore == score[0]) {list.add(1);}
        if(maxScore == score[1]) {list.add(2);}
        if(maxScore == score[2]) {list.add(3);}
        return list.stream().mapToInt(i->i.intValue()).toArray();
    }
}
```

- 풀이 상위에 있는 코드로 얼핏보면 되게 짧지만, 논란 또한 많아보인다.
- score 를 배열로 사용하기에 배열을 찾고 수정해야 하니까 시간이 오래 걸린다는 얘기도 있고(이건 무슨 얘긴지 잘 모르겠다. 배열로 찾으나... 리스트로 찾으나... 내가 모르는 다른 게 있나..?
- 또 다른 의견은 맨 아래 return 부분에서 시간이 많이 걸린다는 얘기가 있다. 음.. 내 풀이랑 같아서 뭐라 말은 못하겠으나.. 나온 의견으로는 저렇게 하는 것보단 for 문을 돌리는 게 더 빠르다고 한다. 
- ~~돌려봤는데, 내 풀이가 더 오래 걸린다..~~