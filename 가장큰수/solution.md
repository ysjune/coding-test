### 내 풀이

```java
import java.util.*;

class Solution {
    public String solution(int[] numbers) {
        String answer = "";

        String[] arr = Arrays.stream(numbers).mapToObj(i -> String.valueOf(i)).toArray(String[]::new);

        Arrays.sort(arr, new Comparator<String>() {
            @Override
            public int compare(String s1, String s2) {

                String sb1 = makeStringBuilder(s1);
                String sb2 = makeStringBuilder(s2);

                return (sb2).compareTo(sb1);
            }
        });
        
        if(arr[0].equalsIgnoreCase("0")) {
            return "0";
        }
        
        for (int i = 0; i < arr.length; i++) {
            answer = answer.concat(arr[i]);
        }

        return answer;
    }

    private String makeStringBuilder(String s) {
        StringBuilder sb = new StringBuilder().append(s);
        int j = 0;
        while (true) {
            if(sb.length() == 4) {
                break;
            }
            sb.append(sb.charAt(j));
            j++;
        }
        return sb.toString();
    }
}
```

- 풀 수 있을 거 같은데.. 하면서 시간 엄청 끌다가 결국 못 풀어서 힌트보고 해결 (갈 길이 멀긴 하다.)
- 마지막 0,0,0 같은 케이스는 생각도 못했다..



### 다른 사람 풀이

```java
import java.util.ArrayList;
import java.util.Collections;
import java.util.List;

class Solution {
    public String solution(int[] numbers) {
        String answer = "";

        List<Integer> list = new ArrayList<>();
        for(int i = 0; i < numbers.length; i++) {
            list.add(numbers[i]);
        }
        Collections.sort(list, (a, b) -> {
            String as = String.valueOf(a), bs = String.valueOf(b);
            return -Integer.compare(Integer.parseInt(as + bs), Integer.parseInt(bs + as));
        });
        StringBuilder sb = new StringBuilder();
        for(Integer i : list) {
            sb.append(i);
        }
        answer = sb.toString();
        if(answer.charAt(0) == '0') {
            return "0";
        }else {
            return answer;
        }
    }
}
```

- 대부분 arrays.sort 를 써서 하는데, collection 이 인상깊었음. 나도 collections 에서 뭐가 있지 않을까 하고 찾다 형변환 때문에 포기했었는데.. 